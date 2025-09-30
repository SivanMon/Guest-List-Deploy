# 🎨 Guest List Project - Colorful Architecture Diagrams

This comprehensive visual guide shows the complete DevSecOps architecture with rich colors and detailed styling.

## 🌈 Complete System Architecture

```mermaid
graph TB
    %% Developer Workflow
    subgraph DEV_FLOW ["👥 Development Workflow"]
        DEV_TEAM["🧑‍💻 Team Members<br/>🎯 Gili, Sivan, Sahar, Dvir<br/>💡 Collaborative Development"]
        
        subgraph FEATURES ["🌟 Feature Development"]
            GILI_BRANCH["🟢 gili-feature-*<br/>🔧 Personal development<br/>🧪 Individual testing"]
            SIVAN_BRANCH["🔵 sivan-feature-*<br/>🔧 Personal development<br/>🧪 Individual testing"]
            SAHAR_BRANCH["🟡 sahar-feature-*<br/>🔧 Personal development<br/>🧪 Individual testing"]
            DVIR_BRANCH["🟣 dvir-feature-*<br/>🔧 Personal development<br/>🧪 Individual testing"]
        end
        
        DEV_BRANCH["🔀 dev Branch<br/>🤝 Integration & Testing<br/>📊 Team Collaboration"]
        MAIN_BRANCH["🚀 main Branch<br/>🏭 Production Release<br/>✅ Stable Deployment"]
        
        DEV_TEAM -.-> GILI_BRANCH
        DEV_TEAM -.-> SIVAN_BRANCH  
        DEV_TEAM -.-> SAHAR_BRANCH
        DEV_TEAM -.-> DVIR_BRANCH
        
        GILI_BRANCH ==> DEV_BRANCH
        SIVAN_BRANCH ==> DEV_BRANCH
        SAHAR_BRANCH ==> DEV_BRANCH
        DVIR_BRANCH ==> DEV_BRANCH
        
        DEV_BRANCH ===> MAIN_BRANCH
    end

    %% Repository Structure
    subgraph REPOS ["📚 GitHub Repositories"]
        subgraph API_REPO ["🔥 Guest-List-API Repository"]
            API_CODE["📱 Flask REST API<br/>🐍 Python 3.11<br/>🗄️ DynamoDB Integration<br/>🌐 Web Interface<br/>🔒 Input Validation"]
            API_DOCKER["🐳 Dockerfile<br/>🏗️ Multi-stage build<br/>❤️ Health checks<br/>⚡ Performance optimization<br/>🔐 Security hardening"]
            API_CI["⚙️ GitHub Actions<br/>🚀 api-workflow.yml<br/>🧪 Automated testing<br/>📦 Image publishing"]
        end
        
        subgraph DEPLOY_REPO ["🎯 Guest-List-Deploy Repository"]
            TERRAFORM["🏗️ Terraform IaC<br/>☁️ AWS Provider<br/>☸️ EKS Cluster<br/>📊 DynamoDB Tables<br/>🌐 Network Infrastructure"]
            K8S_MANIFESTS["☸️ Kubernetes<br/>🚀 Deployments<br/>⚖️ Services<br/>📋 ConfigMaps<br/>🔑 Secrets"]
            DEPLOY_CI["⚙️ GitHub Actions<br/>🎬 clean-terraform.yml<br/>🔄 Cross-repo triggers<br/>📊 Health validation"]
        end
    end

    %% CI/CD Pipeline
    subgraph PIPELINE ["🔄 CI/CD Pipeline"]
        subgraph API_STAGES ["🔥 API Pipeline Stages"]
            BUILD["🔨 Build & Test<br/>🐳 Docker build<br/>🗄️ DynamoDB Local<br/>🧪 Integration tests<br/>✅ Quality gates"]
            TEST["🧪 API Testing<br/>❤️ Health checks<br/>🔧 CRUD operations<br/>🚨 Error handling<br/>📊 Coverage reports"]
            PUBLISH["📦 Image Publishing<br/>🐳 Docker Hub<br/>🏷️ Tag strategy<br/>🌍 Multi-environment<br/>🔐 Registry security"]
        end
        
        subgraph DEPLOY_STAGES ["🎯 Deploy Pipeline Stages"]
            PLAN["📋 Terraform Plan<br/>👀 Infrastructure preview<br/>✅ Resource validation<br/>💰 Cost estimation<br/>🔒 Security checks"]
            APPLY["🚀 Terraform Apply<br/>🏗️ Resource provisioning<br/>☸️ Kubernetes deployment<br/>❤️ Health validation<br/>📊 Monitoring setup"]
        end
        
        REPO_DISPATCH["🔔 Repository Dispatch<br/>🌉 Cross-repo communication<br/>⚡ Real-time triggers<br/>📡 Event propagation"]
    end

    %% Container Registry
    DOCKER_HUB["🐳 Docker Hub Registry<br/>📦 sivanmonshi/guestlistapi<br/>🏷️ latest (main)<br/>🏷️ dev (dev branch)<br/>🏷️ student-feature-* (features)<br/>🔐 Access control<br/>📊 Image scanning"]

    %% AWS Cloud Infrastructure
    subgraph AWS_CLOUD ["☁️ AWS Cloud Infrastructure"]
        subgraph NETWORK ["🌐 Networking Layer"]
            VPC["🏠 VPC 10.0.0.0/16<br/>🌐 DNS hostnames<br/>🔍 DNS support<br/>🔒 Network isolation<br/>📊 Flow logs"]
            
            subgraph PUBLIC_NETS ["📡 Public Subnets"]
                PUB_1["📡 Public Subnet 1<br/>🌐 10.0.1.0/24<br/>📍 us-east-1a<br/>🌍 Internet access<br/>⚖️ Load balancer ready"]
                PUB_2["📡 Public Subnet 2<br/>🌐 10.0.2.0/24<br/>📍 us-east-1b<br/>🌍 Internet access<br/>⚖️ Load balancer ready"]
            end
            
            subgraph PRIVATE_NETS ["🔒 Private Subnets"]
                PRIV_1["🔒 Private Subnet 1<br/>🌐 10.0.10.0/24<br/>📍 us-east-1a<br/>🛡️ Secure workloads<br/>☸️ Kubernetes nodes"]
                PRIV_2["🔒 Private Subnet 2<br/>🌐 10.0.11.0/24<br/>📍 us-east-1b<br/>🛡️ Secure workloads<br/>☸️ Kubernetes nodes"]
            end
            
            IGW["🌍 Internet Gateway<br/>🚪 Public internet access<br/>⚡ High bandwidth<br/>🔒 Security groups"]
            NAT["🔄 NAT Gateway<br/>🌍 Outbound internet<br/>🔒 Private subnet access<br/>💰 Cost optimized<br/>🏠 Single AZ placement"]
        end
        
        subgraph COMPUTE ["💻 Compute Layer"]
            EKS["☸️ EKS Cluster<br/>🎯 Kubernetes 1.28<br/>🏗️ Managed control plane<br/>🌍 Multi-AZ deployment<br/>📊 Logging enabled<br/>🔒 IAM integration"]
            
            subgraph NODES ["🖥️ Worker Nodes"]
                NODE_1["💻 t3.small Node 1<br/>📈 Auto Scaling Group<br/>🔒 Private subnet<br/>🐳 Container runtime<br/>📊 CloudWatch agent"]
                NODE_2["💻 t3.small Node 2<br/>📈 Auto Scaling Group<br/>🔒 Private subnet<br/>🐳 Container runtime<br/>📊 CloudWatch agent"]
            end
        end
        
        subgraph DATABASE ["📊 Database Layer"]
            subgraph DDB_TABLES ["🗄️ DynamoDB Tables"]
                DDB_GILI["📊 GuestList-gili<br/>🟢 Personal development<br/>⚡ Pay-per-request<br/>🔐 Encryption at rest"]
                DDB_SIVAN["📊 GuestList-sivan<br/>🔵 Personal development<br/>⚡ Pay-per-request<br/>🔐 Encryption at rest"]
                DDB_SAHAR["📊 GuestList-sahar<br/>🟡 Personal development<br/>⚡ Pay-per-request<br/>🔐 Encryption at rest"]
                DDB_DVIR["📊 GuestList-dvir<br/>🟣 Personal development<br/>⚡ Pay-per-request<br/>🔐 Encryption at rest"]
                DDB_DEV["📊 GuestList-dev<br/>🔧 Integration testing<br/>⚡ Pay-per-request<br/>🔐 Encryption at rest"]
                DDB_MAIN["📊 GuestList-main<br/>🏭 Production data<br/>⚡ Pay-per-request<br/>🔐 Encryption at rest"]
            end
        end
        
        subgraph LOAD_BAL ["⚖️ Load Balancing"]
            ALB["⚖️ Application Load Balancer<br/>❤️ Health checks<br/>🔐 SSL termination<br/>🌍 Multi-AZ distribution<br/>📊 Access logging<br/>🛡️ WAF integration"]
        end
        
        subgraph STATE_MGMT ["🗄️ State Management"]
            S3_STATE["🗄️ S3 State Bucket<br/>🔄 Versioning enabled<br/>🔐 Encryption at rest<br/>🔑 Per-environment keys<br/>🚫 Public access blocked"]
            DDB_LOCKS["🔐 DynamoDB Locks<br/>🏷️ terraform-locks table<br/>🛡️ Concurrent protection<br/>⚡ On-demand billing"]
        end
    end

    %% Application Layer
    subgraph APP_RUNTIME ["🚀 Application Runtime"]
        subgraph K8S_WORKLOADS ["☸️ Kubernetes Workloads"]
            NAMESPACE["📁 guestlist namespace<br/>🏷️ Resource isolation<br/>🔒 Security boundaries<br/>📊 Resource quotas"]
            
            subgraph API_DEPLOYMENT ["🏃 API Deployment"]
                POD_1["🏃 API Pod 1<br/>🐍 Flask application<br/>❤️ Health probes<br/>📊 Resource limits<br/>🔒 Security context"]
                POD_2["🏃 API Pod 2<br/>🐍 Flask application<br/>❤️ Health probes<br/>📊 Resource limits<br/>🔒 Security context"]
                POD_3["🏃 API Pod 3<br/>🐍 Flask application<br/>❤️ Health probes<br/>📊 Resource limits<br/>🔒 Security context"]
            end
            
            K8S_SVC["⚙️ Kubernetes Service<br/>⚖️ LoadBalancer type<br/>🔌 Port 9999 → 1111<br/>🎯 Pod selection<br/>📊 Session affinity"]
            K8S_HPA["📈 Horizontal Pod Autoscaler<br/>📊 CPU-based scaling<br/>📉 Min: 1, Max: 5<br/>🎯 Target: 70% CPU<br/>⚡ Rapid response"]
            K8S_SECRET["🔑 Secrets<br/>🔐 AWS credentials<br/>🗄️ DynamoDB config<br/>🌍 Environment vars<br/>🔒 Base64 encoded"]
        end
    end

    %% Environment Strategy
    subgraph ENV_MGMT ["🌍 Environment Management"]
        subgraph INDIVIDUAL ["👤 Individual Environments"]
            ENV_GILI["👤 gili Environment<br/>🟢 Personal development<br/>🖼️ gili-feature images<br/>🧪 Isolated testing<br/>💡 Innovation space"]
            ENV_SIVAN["👤 sivan Environment<br/>🔵 Personal development<br/>🖼️ sivan-feature images<br/>🧪 Isolated testing<br/>💡 Innovation space"]
            ENV_SAHAR["👤 sahar Environment<br/>🟡 Personal development<br/>🖼️ sahar-feature images<br/>🧪 Isolated testing<br/>💡 Innovation space"]
            ENV_DVIR["👤 dvir Environment<br/>🟣 Personal development<br/>🖼️ dvir-feature images<br/>🧪 Isolated testing<br/>💡 Innovation space"]
        end
        
        ENV_DEV["🔧 dev Environment<br/>🤝 Integration testing<br/>👥 Team collaboration<br/>🏷️ dev image tag<br/>🔄 Continuous integration"]
        ENV_MAIN["🏭 main Environment<br/>✅ Production stable<br/>🏷️ latest image tag<br/>🚀 High availability<br/>📊 Performance monitoring"]
    end

    %% External Access
    USERS["👥 End Users<br/>🌐 Web browsers<br/>📱 API clients<br/>🔒 Authenticated access<br/>⚡ Fast response times"]
    DEVS["👨‍💻 Developers<br/>☸️ kubectl access<br/>☁️ AWS CLI tools<br/>📚 GitHub integration<br/>🔧 Development tools"]

    %% Enhanced Flow Connections with colors
    %% Development Flow
    API_CODE -.->|"🔄 Code changes"| API_CI
    API_CI ==>|"🔨 Build trigger"| BUILD
    BUILD ==>|"✅ Build success"| TEST
    TEST ==>|"🧪 Tests pass"| PUBLISH
    PUBLISH ==>|"📦 Image ready"| DOCKER_HUB
    PUBLISH ==>|"🔔 Trigger event"| REPO_DISPATCH
    
    REPO_DISPATCH ==>|"📡 Cross-repo"| DEPLOY_CI
    DEPLOY_CI ==>|"📋 Plan phase"| PLAN
    PLAN ==>|"🚀 Deploy phase"| APPLY
    
    %% Infrastructure Flow  
    TERRAFORM -.->|"🏗️ Infrastructure"| APPLY
    K8S_MANIFESTS -.->|"☸️ Workloads"| APPLY
    APPLY ==>|"🎯 Provision EKS"| EKS
    APPLY ==>|"🗄️ Create tables"| DDB_GILI
    APPLY ==>|"🗄️ Create tables"| DDB_SIVAN
    APPLY ==>|"🗄️ Create tables"| DDB_SAHAR
    APPLY ==>|"🗄️ Create tables"| DDB_DVIR
    APPLY ==>|"🗄️ Create tables"| DDB_DEV
    APPLY ==>|"🗄️ Create tables"| DDB_MAIN
    
    %% Networking Flow
    VPC -.->|"🌐 Contains"| PUB_1
    VPC -.->|"🌐 Contains"| PUB_2
    VPC -.->|"🔒 Contains"| PRIV_1
    VPC -.->|"🔒 Contains"| PRIV_2
    IGW ==>|"🌍 Internet"| PUB_1
    IGW ==>|"🌍 Internet"| PUB_2
    NAT ==>|"🔄 Outbound"| PRIV_1
    NAT ==>|"🔄 Outbound"| PRIV_2
    PUB_1 -.->|"💰 Cost optimized"| NAT
    
    %% Kubernetes Flow
    EKS ==>|"☸️ Manages"| NODE_1
    EKS ==>|"☸️ Manages"| NODE_2
    NODE_1 ==>|"🏃 Runs"| POD_1
    NODE_1 ==>|"🏃 Runs"| POD_2
    NODE_2 ==>|"🏃 Runs"| POD_3
    K8S_SVC ==>|"⚖️ Routes to"| POD_1
    K8S_SVC ==>|"⚖️ Routes to"| POD_2
    K8S_SVC ==>|"⚖️ Routes to"| POD_3
    K8S_HPA -.->|"📈 Scales"| POD_1
    K8S_HPA -.->|"📈 Scales"| POD_2
    K8S_HPA -.->|"📈 Scales"| POD_3
    
    %% External Access Flow
    USERS ==>|"🌐 HTTP/HTTPS"| ALB
    ALB ==>|"⚖️ Load balance"| K8S_SVC
    DEVS ==>|"🔧 Management"| EKS
    
    %% State Management Flow
    APPLY ==>|"🗄️ State storage"| S3_STATE
    APPLY ==>|"🔐 Lock management"| DDB_LOCKS
    
    %% Environment Flow
    ENV_GILI ==>|"🔗 Uses"| DDB_GILI
    ENV_SIVAN ==>|"🔗 Uses"| DDB_SIVAN
    ENV_SAHAR ==>|"🔗 Uses"| DDB_SAHAR
    ENV_DVIR ==>|"🔗 Uses"| DDB_DVIR
    ENV_DEV ==>|"🔗 Uses"| DDB_DEV
    ENV_MAIN ==>|"🔗 Uses"| DDB_MAIN

    %% Docker Registry Flow
    DOCKER_HUB ==>|"📥 Pull image"| POD_1
    DOCKER_HUB ==>|"📥 Pull image"| POD_2
    DOCKER_HUB ==>|"📥 Pull image"| POD_3

    %% Rich Color Styling
    classDef awsOrange fill:#FF9900,stroke:#FF6600,stroke-width:3px,color:#FFFFFF,font-weight:bold
    classDef k8sBlue fill:#326CE5,stroke:#1E4A9C,stroke-width:3px,color:#FFFFFF,font-weight:bold
    classDef gitDark fill:#24292E,stroke:#000000,stroke-width:3px,color:#FFFFFF,font-weight:bold
    classDef envGreen fill:#28A745,stroke:#1E7E34,stroke-width:3px,color:#FFFFFF,font-weight:bold
    classDef pipelinePurple fill:#6F42C1,stroke:#563D7C,stroke-width:3px,color:#FFFFFF,font-weight:bold
    classDef networkCyan fill:#17A2B8,stroke:#138496,stroke-width:3px,color:#FFFFFF,font-weight:bold
    classDef computeLime fill:#20C997,stroke:#17A085,stroke-width:3px,color:#FFFFFF,font-weight:bold
    classDef databaseRed fill:#DC3545,stroke:#C82333,stroke-width:3px,color:#FFFFFF,font-weight:bold
    classDef loadBalancerYellow fill:#FFC107,stroke:#E0A800,stroke-width:3px,color:#212529,font-weight:bold
    classDef userPink fill:#E83E8C,stroke:#D91A72,stroke-width:3px,color:#FFFFFF,font-weight:bold
    classDef featureColors fill:#6610F2,stroke:#520DC2,stroke-width:3px,color:#FFFFFF,font-weight:bold
    
    %% Apply color classes
    class VPC,IGW,NAT,S3_STATE,DDB_LOCKS awsOrange
    class EKS,NAMESPACE,POD_1,POD_2,POD_3,K8S_SVC,K8S_HPA,K8S_SECRET k8sBlue
    class API_CODE,API_DOCKER,API_CI,TERRAFORM,K8S_MANIFESTS,DEPLOY_CI,DOCKER_HUB gitDark
    class ENV_GILI,ENV_SIVAN,ENV_SAHAR,ENV_DVIR,ENV_DEV,ENV_MAIN envGreen
    class BUILD,TEST,PUBLISH,PLAN,APPLY,REPO_DISPATCH pipelinePurple
    class PUB_1,PUB_2,PRIV_1,PRIV_2 networkCyan
    class NODE_1,NODE_2 computeLime
    class DDB_GILI,DDB_SIVAN,DDB_SAHAR,DDB_DVIR,DDB_DEV,DDB_MAIN databaseRed
    class ALB loadBalancerYellow
    class USERS,DEVS,DEV_TEAM userPink
    class GILI_BRANCH,SIVAN_BRANCH,SAHAR_BRANCH,DVIR_BRANCH featureColors
```

## 🎨 Colorful CI/CD Workflow Process

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
