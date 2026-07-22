# System Architecture

## Architecture Overview

StockFlow is a multi-tenant order and inventory management platform designed for restaurant and retail merchants. It supports four primary order workflows: `Point of Sale (POS)`, `Online Ordering`, `Self Checkout`, and `Manual`.

StockFlow adopts a modular monolith architecture, where the backend is organised into clearly defined business modules. This architecture reduces development, testing, and deployment complexity during the initial implementation while maintaining clear module boundaries. Each module owns its business responsibilities and communicates with other modules through well-defined application interfaces rather than accessing another module's data directly.

The core business modules are:

- Merchant Management
- Authentication and Access Control
- Product Management
- Inventory Management
- Order Management

All client applications access the platform through dedicated gateways:

- `POS Gateway` - Handles requests from POS devices used by operational staff.
- `Customer Gateway` - Handles customer requests from `Online Ordering` and `Self Checkout`.
- `Admin Gateway` - Handles requests from back-office and merchant staff for administrative and manual operations that are not performed through the POS or customer-facing workflows.

StockFlow uses a shared PostgreSQL database for data storage. Merchant-owned records are associated with a `merchant_id` to ensure that users can only access data belonging to their own merchant organisation. PostgreSQL schemas are used to separate business modules, providing logical boundaries between modules while maintaining a single shared database.

The modular monolith architecture is designed to evolve as the platform grows. Individual modules can be extracted into independent services when scaling, deployment, or operational requirements justify separate ownership, allowing the system to evolve towards a microservices architecture without significant redesign.


## Architecture Diagram

This section provides an overview of the StockFlow system from different architectural perspectives. Each diagram focuses on a specific aspect of the platform, including the overall system structure, the logical organisation of the backend components, and the deployment infrastructure.

- High-Level System Diagram - Illustrates the major components of the platform and how client applications communicate with the backend.
- Logical Architecture - Describes the internal organisation of the StockFlow backend and the relationships between core modules.
- Infrastructure Architecture - Shows how the platform is deployed and the supporting infrastructure used to run the application.

### High-Level System Diagram

The StockFlow platform uses a containerised architecture for its initial deployment. Client applications communicate with the backend through the internet. The `Nginx` acts as the reverse proxy and entry point to the system.

The `StockFlow backend` and `PostgreSQL` database run as Docker containers in the same Docker environment using `docker-compose`. The backend processes business requests and stores application data in `PostgreSQL`.

```mermaid
flowchart TD
    subgraph Clients["Client Applications"]
        Customer["Customer Application"]
        POS["POS Application"]
        Admin["Administration Web Portal"]
    end

    Internet["Internet"]
    Nginx["Nginx"]

    subgraph DockerHost["Docker Environment"]
        StockFlow["StockFlow Backend Container"]
        Database[("PostgreSQL Container")]
    end

    Customer --> Internet
    POS --> Internet
    Admin --> Internet

    Internet --> Nginx
    Nginx --> StockFlow
    StockFlow --> Database
```

### Logical Architecture

The StockFlow backend uses a modular monolith architecture, organising the application into independent modules with clear responsibilities. Client requests are routed through dedicated gateway layers based on the order channel before being processed by the appropriate backend modules.

Each module manages its own business logic and stores its data within a dedicated PostgreSQL schema. This provides clear data isolation, improves maintainability, and supports future scalability.

```mermaid
flowchart TD
    subgraph OrderChannels["Order Channels"]
        OnlineOrder["Online Ordering"]
        
        subgraph InStoreOrdering["In-Store Ordering"]
            SelfCheckout["Customer Self-Checkout"]
            POS["POS Order"]
            MerchantStaff["Merchant Staff Manual Order"]
        end
       
        BackOfficeStaff["Back-Office Staff Manual Order"]
    end

    subgraph Gateway["Gateway Layer"]
        CustomerGateway["Customer Gateway"]
        POSGateway["POS Gateway"]
        AdminGateway["Admin Gateway"]
    end

    subgraph StockFlowBackend["StockFlow Backend (Modular Monolith)"]
        AuthenticationModule["Authentication and Access Control Module"]
        MerchantModule["Merchant Module"]
        ProductModule["Product Module"]
        InventoryModule["Inventory Module"]
        OrderModule["Order Module"]
    end

    subgraph Database["PostgreSQL Database"]
        AuthenticationSchema[("Authentication Schema")]
        MerchantSchema[("Merchant Schema")]
        ProductSchema[("Product Schema")]
        InventorySchema[("Inventory Schema")]
        OrderSchema[("Order Schema")]
    end

    OnlineOrder --> CustomerGateway
    SelfCheckout --> POSGateway
    POS --> POSGateway
    MerchantStaff --> POSGateway
    BackOfficeStaff --> AdminGateway

    CustomerGateway --> StockFlowBackend
    POSGateway --> StockFlowBackend
    AdminGateway --> StockFlowBackend

    ProductModule --> ProductSchema
    InventoryModule --> InventorySchema
    OrderModule --> OrderSchema
    AuthenticationModule --> AuthenticationSchema
    MerchantModule --> MerchantSchema
```

### Infrastructure Architecture

The StockFlow infrastructure is designed to run on either a local mini PC or an AWS EC2 instance using the same containerised deployment model.

Incoming requests pass through the host firewall or security rules, which allow HTTP and HTTPS traffic on ports 80 and 443. Nginx acts as the reverse proxy and forwards requests to the API Gateway, which then routes them to the StockFlow backend. The backend processes the business logic and communicates with the PostgreSQL database through a private Docker network.

Persistent data is stored outside the containers on the host storage, using a local SSD for the mini PC deployment or an EBS volume for AWS. This includes PostgreSQL data, database backups, application files, and logs. A scheduled backup job creates SQL dumps of the database and stores them in the backup directory.

Amazon S3 is optional external storage for database backups, application files, and archived logs. This provides additional durability while keeping the core infrastructure portable between local and AWS environments.

```mermaid
flowchart TD
    Users["Users"]
    Internet["Internet / Local Network"]

    subgraph HostEnv["Deployment Host\n(Mini PC or AWS EC2 Instance)"]

        Firewall["Firewall / Security Rules\n(Allow ports 80 & 443)"]

        subgraph DockerEnv["Docker Environment"]
            subgraph DockerNetwork["Private Docker Network"]
                Nginx["Nginx (Container)"]
                APIGateway["API Gateway (Container)"]
                StockFlowBackend["StockFlow Backend (Container)"]
                Database[("PostgreSQL (Container)")]
                DatabaseBackupJob["Database Backup Cron Job"]
            end
        end

        subgraph PersistentStorage["Persistent Storage (Local SSD / AWS EBS & RDS)"]
            PostgreSQLData["PostgreSQL Data"]
            DatabaseBackup["Database Backups\n(SQL dump files)"]
            AppData["Application Data\n(Image, csv, etc)"]
            AppLog["Application Logs"]
        end
        
    end

    subgraph ExternalStorage["Optional External Storage"]
        S3[("AWS S3")]
    end

    Users --> Internet
    Internet --> Firewall
    Firewall --> Nginx
    Nginx --> APIGateway
    APIGateway --> StockFlowBackend
    StockFlowBackend --> Database

    Database -. mount .-> PostgreSQLData
    DatabaseBackupJob -->|run dump| Database
    DatabaseBackupJob -. write backup .-> DatabaseBackup
    
    StockFlowBackend -. mount .-> AppData
    StockFlowBackend -. write logs .-> AppLog
    Nginx -. write access and error logs .-> AppLog

    DatabaseBackupJob -. upload backup .-> S3
    StockFlowBackend -. upload application files .-> S3
    AppLog -. archive logs .-> S3
```

## Architectural Layers

The StockFlow platform is organised into three primary architectural layers: the `Gateway Layer`, `Backend Modules`, and `Data Layer`. Each layer has a distinct responsibility, promoting clear separation of concerns, maintainability, and future scalability.

### Gateway Layer

The Gateway Layer serves as the entry point for all client requests. It receives requests from different order channels, performs request validation and authentication, and routes requests to the appropriate backend modules based on the client type and business operation.

### Backend Modules

The Backend Modules implement the core business capabilities of the StockFlow platform. Each module is responsible for a specific business domain, encapsulating its own business logic while collaborating with other modules through well-defined interfaces.

### Data Layer

The Data Layer is responsible for persisting application data in PostgreSQL. Each backend module owns its corresponding database schema, providing clear data ownership and isolation while supporting maintainability and future evolution of the system.