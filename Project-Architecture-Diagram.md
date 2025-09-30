# 🎨 Guest List Project - Colorful Architecture Diagrams

This comprehensive visual guide shows the complete DevSecOps architecture with rich colors and detailed styling.

## 🌈 Complete System Architecture

```mermaid
graph TB
    %% Developer Input
    DEVELOPERS["👨‍💻 Development Team<br/>Gili, Sivan, Sahar, Dvir"]
    
    %% Code Repositories
    subgraph REPOS ["📚 GitHub Repositories"]
        API_REPO["📱 Guest-List-API<br/>Flask Application Code<br/>Docker & CI/CD"]
        DEPLOY_REPO["🏗️ Guest-List-Deploy<br/>Terraform Infrastructure<br/>Kubernetes Configs"]
    end
    
    %% CI/CD Process
    subgraph PIPELINE ["🔄 CI/CD Pipeline"]
        BUILD["🔨 Build & Test<br/>Docker Images<br/>API Testing"]
        TRIGGER["🔔 Cross-Repo Trigger<br/>Repository Dispatch<br/>Environment Selection"]
        DEPLOY["🚀 Infrastructure Deploy<br/>Terraform Apply<br/>Kubernetes Update"]
    end
    
    %% Container Registry
    REGISTRY["🐳 Docker Hub<br/>sivanmonshi/guestlistapi<br/>Image Tags by Environment"]
    
    %% AWS Cloud
    subgraph AWS ["☁️ AWS Cloud Infrastructure"]
        subgraph EKS_CLUSTER ["☸️ EKS Kubernetes Cluster"]
            PODS["🏃 API Pods<br/>Flask Application<br/>Auto-scaling"]
            LB_SVC["⚖️ Load Balancer<br/>External Access<br/>Health Checks"]
        end
        
        subgraph DATABASES ["📊 DynamoDB Tables"]
            STUDENT_DBS["👤 Student Environments<br/>GuestList-gili<br/>GuestList-sivan<br/>GuestList-sahar<br/>GuestList-dvir"]
            SHARED_DBS["🤝 Shared Environments<br/>GuestList-dev<br/>GuestList-staging<br/>GuestList-main"]
        end
    end
    
    %% Users
    USERS["👥 End Users<br/>Web Interface<br/>API Clients"]
    
    %% Flow connections
    DEVELOPERS ==> API_REPO
    DEVELOPERS ==> DEPLOY_REPO
    
    API_REPO ==> BUILD
    BUILD ==> REGISTRY
    BUILD ==> TRIGGER
    
    TRIGGER ==> DEPLOY
    DEPLOY_REPO ==> DEPLOY
    
    REGISTRY ==> PODS
    DEPLOY ==> EKS_CLUSTER
    DEPLOY ==> DATABASES
    
    LB_SVC ==> USERS
    PODS <==> STUDENT_DBS
    PODS <==> SHARED_DBS
    
    %% Styling
    classDef repoColor fill:#2D3748,stroke:#4A5568,stroke-width:3px,color:#FFFFFF,font-weight:bold
    classDef pipelineColor fill:#6B46C1,stroke:#553C9A,stroke-width:3px,color:#FFFFFF,font-weight:bold
    classDef awsColor fill:#FF9900,stroke:#E68900,stroke-width:3px,color:#FFFFFF,font-weight:bold
    classDef k8sColor fill:#326CE5,stroke:#2557CC,stroke-width:3px,color:#FFFFFF,font-weight:bold
    classDef dataColor fill:#DC2626,stroke:#B91C1C,stroke-width:3px,color:#FFFFFF,font-weight:bold
    classDef userColor fill:#059669,stroke:#047857,stroke-width:3px,color:#FFFFFF,font-weight:bold
    
    class API_REPO,DEPLOY_REPO,REGISTRY repoColor
    class BUILD,TRIGGER,DEPLOY pipelineColor
    class AWS awsColor
    class EKS_CLUSTER,PODS,LB_SVC k8sColor
    class DATABASES,STUDENT_DBS,SHARED_DBS dataColor
    class DEVELOPERS,USERS userColor
```

## 🔄 Environment Workflow Process

```mermaid
graph LR
    subgraph INDIVIDUAL ["👤 Individual Development"]
        GILI["🟢 gili-feature-*<br/>Personal Dev & Testing"]
        SIVAN["🔵 sivan-feature-*<br/>Personal Dev & Testing"]
        SAHAR["🟡 sahar-feature-*<br/>Personal Dev & Testing"]
        DVIR["🟣 dvir-feature-*<br/>Personal Dev & Testing"]
    end
    
    subgraph SHARED ["🤝 Shared Environments"]
        DEV["🔧 dev Environment<br/>🔄 Auto-deploy on push<br/>🧪 Integration Testing"]
        STAGING["🎭 staging Environment<br/>✋ Manual deployment<br/>📋 Pre-production Validation<br/>✅ Quality Assurance"]
        MAIN["🏭 main Environment<br/>🔄 Auto-deploy on PR merge<br/>🚀 Production Ready"]
    end
    
    %% Individual to Dev
    GILI ==>|"Merge PR"| DEV
    SIVAN ==>|"Merge PR"| DEV
    SAHAR ==>|"Merge PR"| DEV
    DVIR ==>|"Merge PR"| DEV
    
    %% Dev to Staging (Manual)
    DEV ==>|"Manual Deploy<br/>When ready for validation"| STAGING
    
    %% Staging to Main
    STAGING ==>|"PR Review & Merge<br/>After staging validation"| MAIN
    
    %% Styling
    classDef individualColor fill:#6366F1,stroke:#4F46E5,stroke-width:3px,color:#FFFFFF,font-weight:bold
    classDef devColor fill:#059669,stroke:#047857,stroke-width:3px,color:#FFFFFF,font-weight:bold
    classDef stagingColor fill:#D97706,stroke:#B45309,stroke-width:3px,color:#FFFFFF,font-weight:bold
    classDef prodColor fill:#DC2626,stroke:#B91C1C,stroke-width:3px,color:#FFFFFF,font-weight:bold
    
    class GILI,SIVAN,SAHAR,DVIR individualColor
    class DEV devColor
    class STAGING stagingColor
    class MAIN prodColor
```

## 🌈 Complete System Architecture

```mermaid
sequenceDiagram
    participant 🧑‍💻 as Developer Team
    participant 📱 as API Repository
    participant 🐳 as Docker Hub
    participant 🎯 as Deploy Repository
    participant ☁️ as AWS Cloud
    participant 👥 as End Users

    rect rgb(240, 248, 255)
        Note over 🧑‍💻,📱: Development Phase
        🧑‍💻->>📱: 🌟 Push feature branch
        Note right of 📱: gili-feature-auth ✨<br/>sivan-feature-ui 🎨<br/>sahar-feature-api 🔧<br/>dvir-feature-deploy 🚀
        
        📱->>📱: 🔨 Run CI Pipeline
        Note right of 📱: Build 🏗️<br/>Test 🧪<br/>Quality Gates ✅
        
        📱->>🐳: 📦 Push Tagged Image
        Note right of 🐳: student-feature-abc123 🏷️<br/>Multi-arch support 🌍
    end

    rect rgb(240, 255, 240)
        Note over 🧑‍💻,🎯: Integration Phase
        🧑‍💻->>📱: 🔀 Merge to dev branch
        📱->>📱: 🧪 Integration Testing
        Note right of 📱: DynamoDB Local 🗄️<br/>Full API Tests ✅<br/>Coverage Reports 📊
        
        📱->>🐳: 📤 Push dev image
        Note right of 🐳: sivanmonshi/guestlistapi:dev 🔖
        
        📱->>🎯: 🔔 Repository Dispatch
        Note right of 🎯: Event: deploy_plan 📋<br/>Payload: environment=dev 🎯
        
        🎯->>🎯: 📋 Terraform Plan
        Note right of 🎯: Infrastructure Preview 👀<br/>Cost Estimation 💰<br/>Security Validation 🔒
    end

    rect rgb(255, 240, 240)
        Note over 🧑‍💻,☁️: Production Phase
        🧑‍💻->>📱: 📋 Create PR to main
        📱->>🎯: 🚀 Repository Dispatch
        Note right of 🎯: Event: deploy_apply ⚡<br/>Payload: environment=main 🏭
        
        🎯->>☁️: 🏗️ Terraform Apply
        Note right of ☁️: Provision EKS 🎯<br/>Create DynamoDB 📊<br/>Setup Networking 🌐
        
        ☁️->>🐳: 📥 Pull latest image
        Note right of 🐳: sivanmonshi/guestlistapi:latest 🔖
        
        ☁️->>☁️: ☸️ Deploy to EKS
        Note right of ☁️: Rolling Update 🔄<br/>Health Checks ❤️<br/>Auto Scaling 📈
    end

    rect rgb(255, 255, 240)
        Note over 🎯,👥: Validation Phase
        🎯->>☁️: ❤️ Health Validation
        Note right of ☁️: Load Balancer Ready ⚖️<br/>DNS Resolution 🌐<br/>API Endpoints Active 🔗
        
        ☁️-->>🎯: ✅ Service Healthy
        🎯-->>📱: 📝 Deployment Complete
        
        ☁️->>👥: 🌐 Service Available
        Note right of 👥: Guest List API Ready! 🎉<br/>Multi-environment Access 🌍
    end
```

## 🌈 Multi-Environment Deployment View

```mermaid
graph LR
    subgraph FEATURE_ENVS ["🌟 Student Feature Environments"]
        subgraph GILI_ENV ["🟢 Gili's Innovation Lab"]
            G_CODE["🔧 Feature Code<br/>🧪 Experimentation<br/>🔬 Testing Ground"]
            G_IMAGE["🖼️ gili-feature-abc123<br/>🔄 Auto-tagged<br/>📦 Ready to deploy"]
            G_INFRA["🏗️ Personal Infrastructure<br/>☸️ Individual EKS<br/>📊 GuestList-gili"]
            G_CODE ==> G_IMAGE ==> G_INFRA
        end
        
        subgraph SIVAN_ENV ["🔵 Sivan's Development Space"]
            S_CODE["🔧 Feature Code<br/>🧪 Experimentation<br/>🔬 Testing Ground"]
            S_IMAGE["🖼️ sivan-feature-xyz789<br/>🔄 Auto-tagged<br/>📦 Ready to deploy"]
            S_INFRA["🏗️ Personal Infrastructure<br/>☸️ Individual EKS<br/>📊 GuestList-sivan"]
            S_CODE ==> S_IMAGE ==> S_INFRA
        end
        
        subgraph SAHAR_ENV ["🟡 Sahar's Build Lab"]
            H_CODE["🔧 Feature Code<br/>🧪 Experimentation<br/>🔬 Testing Ground"]
            H_IMAGE["🖼️ sahar-feature-def456<br/>🔄 Auto-tagged<br/>📦 Ready to deploy"]
            H_INFRA["🏗️ Personal Infrastructure<br/>☸️ Individual EKS<br/>📊 GuestList-sahar"]
            H_CODE ==> H_IMAGE ==> H_INFRA
        end
        
        subgraph DVIR_ENV ["🟣 Dvir's Deploy Studio"]
            D_CODE["🔧 Feature Code<br/>🧪 Experimentation<br/>🔬 Testing Ground"]
            D_IMAGE["🖼️ dvir-feature-ghi123<br/>🔄 Auto-tagged<br/>📦 Ready to deploy"]
            D_INFRA["🏗️ Personal Infrastructure<br/>☸️ Individual EKS<br/>📊 GuestList-dvir"]
            D_CODE ==> D_IMAGE ==> D_INFRA
        end
    end
    
    subgraph SHARED_ENVS ["🤝 Shared Team Environments"]
        subgraph DEV_ENV ["🔧 Development Integration Hub"]
            DEV_CODE["🔀 Merged Features<br/>🧪 Integration Testing<br/>🤝 Team Collaboration"]
            DEV_IMAGE["🖼️ sivanmonshi/guestlistapi:dev<br/>🔄 Auto-deployment<br/>📈 Continuous Integration"]
            DEV_INFRA["🏗️ Shared Infrastructure<br/>☸️ Team EKS Cluster<br/>📊 GuestList-dev<br/>⚖️ Load Balancing<br/>📈 Auto Scaling"]
            DEV_CODE ==> DEV_IMAGE ==> DEV_INFRA
        end
        
        subgraph PROD_ENV ["🏭 Production Environment"]
            PROD_CODE["✅ Stable Release<br/>🚀 Production Ready<br/>🏆 Quality Assured"]
            PROD_IMAGE["🖼️ sivanmonshi/guestlistapi:latest<br/>🔒 Security Scanned<br/>⚡ Performance Optimized"]
            PROD_INFRA["🏗️ Production Infrastructure<br/>☸️ HA EKS Cluster<br/>📊 GuestList-main<br/>🌍 Multi-AZ Deployment<br/>📊 Advanced Monitoring<br/>🔒 Enhanced Security"]
            PROD_CODE ==> PROD_IMAGE ==> PROD_INFRA
        end
    end

    %% Flow between environments
    G_CODE -.->|"🔀 Feature PR"| DEV_CODE
    S_CODE -.->|"🔀 Feature PR"| DEV_CODE
    H_CODE -.->|"🔀 Feature PR"| DEV_CODE
    D_CODE -.->|"🔀 Feature PR"| DEV_CODE
    
    DEV_CODE ==>|"📋 PR Review<br/>✅ Quality Gates"| PROD_CODE

    %% Styling with vibrant colors
    classDef studentGreen fill:#4CAF50,stroke:#2E7D32,stroke-width:4px,color:#FFFFFF,font-weight:bold
    classDef studentBlue fill:#2196F3,stroke:#1565C0,stroke-width:4px,color:#FFFFFF,font-weight:bold
    classDef studentYellow fill:#FF9800,stroke:#E65100,stroke-width:4px,color:#FFFFFF,font-weight:bold
    classDef studentPurple fill:#9C27B0,stroke:#6A1B9A,stroke-width:4px,color:#FFFFFF,font-weight:bold
    classDef devOrange fill:#FF5722,stroke:#D84315,stroke-width:4px,color:#FFFFFF,font-weight:bold
    classDef prodRed fill:#F44336,stroke:#C62828,stroke-width:4px,color:#FFFFFF,font-weight:bold
    
    class G_CODE,G_IMAGE,G_INFRA studentGreen
    class S_CODE,S_IMAGE,S_INFRA studentBlue
    class H_CODE,H_IMAGE,H_INFRA studentYellow
    class D_CODE,D_IMAGE,D_INFRA studentPurple
    class DEV_CODE,DEV_IMAGE,DEV_INFRA devOrange
    class PROD_CODE,PROD_IMAGE,PROD_INFRA prodRed
```

## 🏗️ AWS Infrastructure Color-Coded View

```mermaid
graph TB
    subgraph REGION ["🌍 AWS us-east-1 Region"]
        subgraph NETWORKING ["🌐 Virtual Private Cloud"]
            VPC_MAIN["🏠 VPC 10.0.0.0/16<br/>🔗 DNS Resolution<br/>🌐 Internet Gateway Ready<br/>📊 Flow Logs Enabled"]
            
            subgraph PUBLIC_ZONE ["📡 Public Network Zone"]
                PUB_SUB_1["📡 Public Subnet 1<br/>🌐 10.0.1.0/24<br/>📍 Availability Zone A<br/>🌍 Internet Accessible<br/>⚖️ Load Balancer Ready"]
                PUB_SUB_2["📡 Public Subnet 2<br/>🌐 10.0.2.0/24<br/>📍 Availability Zone B<br/>🌍 Internet Accessible<br/>⚖️ Load Balancer Ready"]
                
                IGW_MAIN["🌍 Internet Gateway<br/>⚡ High Bandwidth<br/>🔒 Security Group Controlled<br/>🌐 Bidirectional Traffic"]
                
                NAT_GW["🔄 NAT Gateway<br/>💰 Cost Optimized (Single)<br/>🔒 Outbound Only<br/>📊 CloudWatch Monitoring<br/>⚡ Enhanced Bandwidth"]
            end
            
            subgraph PRIVATE_ZONE ["🔒 Private Network Zone"]
                PRIV_SUB_1["🔒 Private Subnet 1<br/>🌐 10.0.10.0/24<br/>📍 Availability Zone A<br/>☸️ Kubernetes Workers<br/>🛡️ No Direct Internet"]
                PRIV_SUB_2["🔒 Private Subnet 2<br/>🌐 10.0.11.0/24<br/>📍 Availability Zone B<br/>☸️ Kubernetes Workers<br/>🛡️ No Direct Internet"]
            end
        end
        
        subgraph COMPUTE_LAYER ["💻 Container Orchestration"]
            EKS_CLUSTER["☸️ EKS Control Plane<br/>🎯 Kubernetes 1.28<br/>🏗️ Managed Service<br/>📊 Logging: API + Audit<br/>🔒 Private + Public Endpoints<br/>🌍 Multi-AZ High Availability"]
            
            subgraph WORKER_NODES ["🖥️ Worker Node Pool"]
                WORKER_1["💻 t3.small Worker 1<br/>🔒 Private Subnet A<br/>📈 Auto Scaling Group<br/>🐳 Container Runtime<br/>📊 CloudWatch Agent<br/>🔧 Managed Node Group"]
                WORKER_2["💻 t3.small Worker 2<br/>🔒 Private Subnet B<br/>📈 Auto Scaling Group<br/>🐳 Container Runtime<br/>📊 CloudWatch Agent<br/>🔧 Managed Node Group"]
            end
            
            subgraph APP_WORKLOADS ["🏃 Application Workloads"]
                POD_REPLICAS["🏃 API Pod Replicas<br/>🐍 Flask Application<br/>❤️ Health Probes<br/>📊 Resource Limits<br/>🔒 Security Context<br/>📈 Horizontal Scaling"]
            end
        end
        
        subgraph DATA_LAYER ["📊 Database Services"]
            subgraph DYNAMODB_CLUSTER ["🗄️ DynamoDB NoSQL Cluster"]
                STUDENT_TABLES["📊 Student Tables<br/>🟢 GuestList-gili<br/>🔵 GuestList-sivan<br/>🟡 GuestList-sahar<br/>🟣 GuestList-dvir"]
                SHARED_TABLES["📊 Shared Tables<br/>🔧 GuestList-dev<br/>🏭 GuestList-main"]
            end
            
            TABLE_CONFIG["⚙️ Table Configuration<br/>⚡ Pay-per-Request Billing<br/>🔐 Encryption at Rest<br/>🔄 Point-in-Time Recovery<br/>📈 Auto Scaling Ready"]
        end
        
        subgraph LOAD_BALANCING ["⚖️ Load Balancing & Traffic"]
            ALB_MAIN["⚖️ Application Load Balancer<br/>🌍 Internet-facing<br/>❤️ Health Check Integration<br/>🔐 SSL/TLS Termination<br/>📊 Access Logging<br/>🛡️ WAF Ready<br/>🌐 Multi-AZ Distribution"]
            
            TARGET_GROUPS["🎯 Target Groups<br/>☸️ Kubernetes Service Integration<br/>❤️ Health Check Endpoints<br/>⚖️ Load Distribution Algorithm<br/>📊 Connection Draining"]
        end
        
        subgraph STATE_MANAGEMENT ["🗄️ Infrastructure State"]
            S3_BUCKET["🗄️ S3 State Bucket<br/>🔄 Versioning Enabled<br/>🔐 Server-side Encryption<br/>🚫 Public Access Blocked<br/>📋 Lifecycle Policies<br/>🏷️ Per-environment Keys"]
            
            LOCK_TABLE["🔐 DynamoDB Lock Table<br/>🏷️ terraform-locks<br/>🛡️ Concurrent Execution Protection<br/>⚡ On-demand Billing<br/>🔄 Automatic Cleanup"]
        end
        
        subgraph MONITORING ["📊 Observability & Monitoring"]
            CLOUDWATCH["📊 CloudWatch<br/>📈 Metrics Collection<br/>📋 Log Aggregation<br/>🚨 Alarm Management<br/>📊 Dashboard Creation"]
            
            HEALTH_CHECKS["❤️ Health Monitoring<br/>☸️ Kubernetes Probes<br/>⚖️ Load Balancer Checks<br/>🔗 API Endpoint Validation<br/>📊 Performance Metrics"]
        end
    end

    %% Enhanced connection flows
    IGW_MAIN ==>|"🌐 Internet Traffic"| ALB_MAIN
    ALB_MAIN ==>|"⚖️ Distribute Load"| TARGET_GROUPS
    TARGET_GROUPS ==>|"🎯 Route Traffic"| POD_REPLICAS
    
    VPC_MAIN -.->|"🌐 Contains"| PUB_SUB_1
    VPC_MAIN -.->|"🌐 Contains"| PUB_SUB_2
    VPC_MAIN -.->|"🔒 Contains"| PRIV_SUB_1
    VPC_MAIN -.->|"🔒 Contains"| PRIV_SUB_2
    
    PUB_SUB_1 -.->|"💰 Cost Share"| NAT_GW
    NAT_GW ==>|"🔄 Outbound NAT"| PRIV_SUB_1
    NAT_GW ==>|"🔄 Outbound NAT"| PRIV_SUB_2
    
    EKS_CLUSTER ==>|"☸️ Orchestrates"| WORKER_1
    EKS_CLUSTER ==>|"☸️ Orchestrates"| WORKER_2
    WORKER_1 ==>|"🏃 Hosts"| POD_REPLICAS
    WORKER_2 ==>|"🏃 Hosts"| POD_REPLICAS
    
    POD_REPLICAS ==>|"📊 Data Access"| STUDENT_TABLES
    POD_REPLICAS ==>|"📊 Data Access"| SHARED_TABLES
    
    TABLE_CONFIG -.->|"⚙️ Configures"| STUDENT_TABLES
    TABLE_CONFIG -.->|"⚙️ Configures"| SHARED_TABLES
    
    S3_BUCKET -.->|"🗄️ Terraform State"| LOCK_TABLE
    CLOUDWATCH ==>|"📊 Monitors"| POD_REPLICAS
    HEALTH_CHECKS ==>|"❤️ Validates"| ALB_MAIN

    %% Rich color scheme for AWS services
    classDef vpcBlue fill:#232F3E,stroke:#FF9900,stroke-width:4px,color:#FFFFFF,font-weight:bold
    classDef publicGreen fill:#7AA116,stroke:#4B7C0C,stroke-width:4px,color:#FFFFFF,font-weight:bold
    classDef privateRed fill:#D13212,stroke:#8B1E0A,stroke-width:4px,color:#FFFFFF,font-weight:bold
    classDef computeOrange fill:#FF9900,stroke:#CC7A00,stroke-width:4px,color:#FFFFFF,font-weight:bold
    classDef k8sBlue fill:#326CE5,stroke:#1E4A9C,stroke-width:4px,color:#FFFFFF,font-weight:bold
    classDef databasePurple fill:#9D5AAE,stroke:#6B3A75,stroke-width:4px,color:#FFFFFF,font-weight:bold
    classDef loadBalancerYellow fill:#F58536,stroke:#C26A29,stroke-width:4px,color:#FFFFFF,font-weight:bold
    classDef storageGray fill:#7D8998,stroke:#5A6270,stroke-width:4px,color:#FFFFFF,font-weight:bold
    classDef monitoringTeal fill:#1BA6A0,stroke:#137772,stroke-width:4px,color:#FFFFFF,font-weight:bold
    
    class VPC_MAIN vpcBlue
    class PUB_SUB_1,PUB_SUB_2,IGW_MAIN,NAT_GW publicGreen
    class PRIV_SUB_1,PRIV_SUB_2 privateRed
    class EKS_CLUSTER,WORKER_1,WORKER_2 computeOrange
    class POD_REPLICAS k8sBlue
    class STUDENT_TABLES,SHARED_TABLES,TABLE_CONFIG databasePurple
    class ALB_MAIN,TARGET_GROUPS loadBalancerYellow
    class S3_BUCKET,LOCK_TABLE storageGray
    class CLOUDWATCH,HEALTH_CHECKS monitoringTeal
```

```mermaid
sequenceDiagram
    participant Dev as 👨‍💻 Developer
    participant API as 📱 API Repo
    participant Hub as 🐳 Docker Hub
    participant Deploy as 🏗️ Deploy Repo
    participant AWS as ☁️ AWS Cloud
    participant Users as 👥 End Users

    %% Development Phase
    Dev->>API: 1. Push feature branch
    Note over API: gili-feature-*, sivan-feature-*, etc.
    
    API->>API: 2. Run CI/CD Pipeline
    Note over API: Build, Test, Integration
    
    API->>Hub: 3. Push tagged image
    Note over Hub: student-feature-sha7
    
    %% Integration Phase
    Dev->>API: 4. Merge to dev branch
    API->>API: 5. Build & test dev image
    API->>Hub: 6. Push dev image
    API->>Deploy: 7. Repository dispatch (deploy_plan)
    
    Deploy->>Deploy: 8. Terraform plan
    Note over Deploy: Infrastructure preview
    
    %% Production Phase
    Dev->>API: 9. Create PR to main
    API->>Deploy: 10. Repository dispatch (deploy_apply)
    
    Deploy->>AWS: 11. Terraform apply
    Note over AWS: Provision infrastructure
    
    AWS->>Hub: 12. Pull latest image
    AWS->>AWS: 13. Deploy to EKS
    Note over AWS: Rolling update
    
    AWS->>Users: 14. Service available
    Note over Users: Load balancer endpoint
    
    %% Health Check Phase
    Deploy->>AWS: 15. Health validation
    AWS-->>Deploy: 16. Service healthy
    Deploy-->>API: 17. Deployment complete
```

## 🌍 Multi-Environment Architecture

```mermaid
graph LR
    subgraph "Student Development"
        subgraph "Gili Environment"
            G_API[API Pod] --> G_DB[GuestList-gili]
            G_LB[Load Balancer] --> G_API
        end
        
        subgraph "Sivan Environment"
            S_API[API Pod] --> S_DB[GuestList-sivan]
            S_LB[Load Balancer] --> S_API
        end
        
        subgraph "Sahar Environment"
            H_API[API Pod] --> H_DB[GuestList-sahar]
            H_LB[Load Balancer] --> H_API
        end
        
        subgraph "Dvir Environment"
            D_API[API Pod] --> D_DB[GuestList-dvir]
            D_LB[Load Balancer] --> D_API
        end
    end
    
    subgraph "Shared Environments"
        subgraph "Development Environment"
            DEV_API[API Pods × 2] --> DEV_DB[GuestList-dev]
            DEV_LB[Load Balancer] --> DEV_API
        end
        
        subgraph "Production Environment"
            PROD_API[API Pods × 3] --> PROD_DB[GuestList-main]
            PROD_LB[Load Balancer] --> PROD_API
            PROD_HPA[Auto Scaler] --> PROD_API
        end
    end
    
    %% Image Sources
    GILI_IMG[gili-feature-*] --> G_API
    SIVAN_IMG[sivan-feature-*] --> S_API
    SAHAR_IMG[sahar-feature-*] --> H_API
    DVIR_IMG[dvir-feature-*] --> D_API
    DEV_IMG[dev] --> DEV_API
    LATEST_IMG[latest] --> PROD_API
```

## 🛠️ Technology Stack Rainbow

```mermaid
graph TD
    subgraph FRONTEND_LAYER ["🌈 Frontend & User Interface"]
        WEB_UI["🌐 Web Interface<br/>🎨 HTML5 + CSS3<br/>⚡ JavaScript ES6+<br/>📱 Responsive Design<br/>🎭 Interactive Dashboard"]
        API_ENDPOINTS["🔗 REST API Endpoints<br/>📡 HTTP/HTTPS<br/>📊 JSON Responses<br/>🔒 Input Validation<br/>❤️ Health Checks"]
    end
    
    subgraph APPLICATION_LAYER ["🚀 Application Runtime"]
        FLASK_APP["🌶️ Flask Framework<br/>🐍 Python 3.11<br/>⚡ Lightweight & Fast<br/>🔌 Extensible Architecture<br/>🧪 Built-in Testing"]
        BUSINESS_LOGIC["🧠 Business Logic<br/>👥 Guest Management<br/>✅ Data Validation<br/>🔄 CRUD Operations<br/>📊 Event Processing"]
    end
    
    subgraph DATA_LAYER ["📊 Data & Storage"]
        DYNAMODB["📊 DynamoDB NoSQL<br/>⚡ Serverless Database<br/>🔄 Auto Scaling<br/>💰 Pay-per-Request<br/>🔐 Encryption at Rest<br/>🌍 Multi-Region Ready"]
        DATA_MODELS["🗄️ Data Models<br/>👤 Guest Entity<br/>🔑 Primary Keys<br/>📋 Attributes Schema<br/>🔍 Query Patterns"]
    end
    
    subgraph CONTAINER_LAYER ["🐳 Containerization"]
        DOCKER_BASE["🐳 Docker Container<br/>🐧 Python 3.11-slim<br/>⚡ Multi-stage Build<br/>🔒 Security Hardened<br/>📦 Minimal Footprint"]
        IMAGE_REGISTRY["🏪 Docker Hub Registry<br/>🏷️ Tag Management<br/>🔐 Access Control<br/>📊 Image Scanning<br/>🌍 Global Distribution"]
    end
    
    subgraph ORCHESTRATION_LAYER ["☸️ Container Orchestration"]
        KUBERNETES["☸️ Kubernetes<br/>🎯 Pod Management<br/>⚖️ Load Balancing<br/>📈 Auto Scaling<br/>❤️ Health Monitoring<br/>🔄 Rolling Updates"]
        EKS_SERVICE["🎯 AWS EKS<br/>🏗️ Managed Control Plane<br/>🔒 IAM Integration<br/>📊 CloudWatch Logging<br/>🌍 Multi-AZ Deployment"]
    end
    
    subgraph INFRASTRUCTURE_LAYER ["🏗️ Infrastructure as Code"]
        TERRAFORM["🏗️ Terraform<br/>📜 Declarative Config<br/>🔄 State Management<br/>📊 Plan & Apply<br/>🌍 Multi-Cloud Support"]
        AWS_PROVIDER["☁️ AWS Provider<br/>🔧 Resource Management<br/>🔒 IAM Roles<br/>🌐 VPC Networking<br/>📊 Service Integration"]
    end
    
    subgraph CICD_LAYER ["🔄 CI/CD Automation"]
        GITHUB_ACTIONS["⚙️ GitHub Actions<br/>🚀 Workflow Automation<br/>🧪 Automated Testing<br/>📦 Build & Deploy<br/>🔔 Cross-repo Events"]
        PIPELINE_STAGES["🎬 Pipeline Stages<br/>🔨 Build & Test<br/>📊 Quality Gates<br/>🐳 Image Publishing<br/>🚀 Deployment"]
    end
    
    subgraph NETWORKING_LAYER ["🌐 Network Infrastructure"]
        AWS_VPC["🏠 AWS VPC<br/>🌐 Virtual Network<br/>🔒 Security Groups<br/>📡 Subnets & Routes<br/>🌍 Internet Gateway"]
        LOAD_BALANCER["⚖️ Application Load Balancer<br/>🌍 Internet-facing<br/>❤️ Health Checks<br/>🔐 SSL Termination<br/>📊 Access Logging"]
    end
    
    subgraph MONITORING_LAYER ["📊 Observability"]
        HEALTH_MONITORING["❤️ Health Monitoring<br/>☸️ Kubernetes Probes<br/>📊 Metrics Collection<br/>🚨 Alert Management<br/>📋 Log Aggregation"]
        PERFORMANCE_METRICS["📈 Performance Metrics<br/>⚡ Response Times<br/>🔄 Request Rates<br/>💾 Resource Usage<br/>📊 Business KPIs"]
    end
    
    %% Flow connections with colorful arrows
    WEB_UI ==>|"🌐 HTTP Requests"| API_ENDPOINTS
    API_ENDPOINTS ==>|"🔄 Route Handling"| FLASK_APP
    FLASK_APP ==>|"🧠 Process Logic"| BUSINESS_LOGIC
    BUSINESS_LOGIC ==>|"📊 Data Operations"| DATA_MODELS
    DATA_MODELS ==>|"🗄️ Store & Retrieve"| DYNAMODB
    
    FLASK_APP -.->|"📦 Containerize"| DOCKER_BASE
    DOCKER_BASE ==>|"🚀 Publish"| IMAGE_REGISTRY
    IMAGE_REGISTRY ==>|"📥 Pull Images"| KUBERNETES
    KUBERNETES -.->|"🎯 Managed Service"| EKS_SERVICE
    
    TERRAFORM ==>|"🏗️ Provision"| AWS_PROVIDER
    AWS_PROVIDER ==>|"☁️ Create Resources"| EKS_SERVICE
    AWS_PROVIDER ==>|"🌐 Setup Network"| AWS_VPC
    AWS_PROVIDER ==>|"📊 Create Database"| DYNAMODB
    AWS_PROVIDER ==>|"⚖️ Deploy LB"| LOAD_BALANCER
    
    GITHUB_ACTIONS ==>|"🎬 Execute"| PIPELINE_STAGES
    PIPELINE_STAGES ==>|"🐳 Build Images"| DOCKER_BASE
    PIPELINE_STAGES ==>|"🚀 Deploy Infrastructure"| TERRAFORM
    
    KUBERNETES ==>|"📊 Export Metrics"| HEALTH_MONITORING
    LOAD_BALANCER ==>|"📈 Performance Data"| PERFORMANCE_METRICS
    
    AWS_VPC ==>|"🌐 Network Traffic"| LOAD_BALANCER
    LOAD_BALANCER ==>|"⚖️ Route Traffic"| KUBERNETES

    %% Vibrant color scheme for each technology layer
    classDef frontendPink fill:#E91E63,stroke:#AD1457,stroke-width:4px,color:#FFFFFF,font-weight:bold
    classDef applicationGreen fill:#4CAF50,stroke:#2E7D32,stroke-width:4px,color:#FFFFFF,font-weight:bold
    classDef dataBlue fill:#2196F3,stroke:#1565C0,stroke-width:4px,color:#FFFFFF,font-weight:bold
    classDef containerCyan fill:#00BCD4,stroke:#00838F,stroke-width:4px,color:#FFFFFF,font-weight:bold
    classDef orchestrationPurple fill:#9C27B0,stroke:#6A1B9A,stroke-width:4px,color:#FFFFFF,font-weight:bold
    classDef infrastructureOrange fill:#FF9800,stroke:#E65100,stroke-width:4px,color:#FFFFFF,font-weight:bold
    classDef cicdIndigo fill:#3F51B5,stroke:#283593,stroke-width:4px,color:#FFFFFF,font-weight:bold
    classDef networkTeal fill:#009688,stroke:#00695C,stroke-width:4px,color:#FFFFFF,font-weight:bold
    classDef monitoringRed fill:#F44336,stroke:#C62828,stroke-width:4px,color:#FFFFFF,font-weight:bold
    
    class WEB_UI,API_ENDPOINTS frontendPink
    class FLASK_APP,BUSINESS_LOGIC applicationGreen
    class DYNAMODB,DATA_MODELS dataBlue
    class DOCKER_BASE,IMAGE_REGISTRY containerCyan
    class KUBERNETES,EKS_SERVICE orchestrationPurple
    class TERRAFORM,AWS_PROVIDER infrastructureOrange
    class GITHUB_ACTIONS,PIPELINE_STAGES cicdIndigo
    class AWS_VPC,LOAD_BALANCER networkTeal
    class HEALTH_MONITORING,PERFORMANCE_METRICS monitoringRed
```

## 🔄 Workflow Process Flow

1. **Complete DevSecOps Pipeline**: From development to production
2. **Multi-Environment Support**: Individual and shared environments
3. **Infrastructure as Code**: Terraform-managed AWS resources
4. **Container Orchestration**: Kubernetes on EKS
5. **Automated CI/CD**: Cross-repository integration
6. **Security Best Practices**: IAM roles, network isolation, encryption
7. **Scalability**: Auto-scaling and load balancing
8. **Cost Optimization**: Resource-efficient configurations

The project showcases modern cloud-native development practices with comprehensive automation and professional-grade infrastructure management.
