# Guest List API - DevSecOps Project

Simple infrastructure deployment for Guest List API using Terraform and EKS.

## Quick Start

### 1. Add AWS Credentials to GitHub Secrets

Go to your repo → Settings → Secrets → Actions and add:

**For Sivan:**
- `AWS_ACCESS_KEY_ID_SIVAN` 
- `AWS_SECRET_ACCESS_KEY_SIVAN`

**For Dvir:**
- `AWS_ACCESS_KEY_ID_DVIR`
- `AWS_SECRET_ACCESS_KEY_DVIR`

### 2. Deploy by Pushing to Branches

```bash
# Plan for Sivan
git checkout sivan-feature
git push origin sivan-feature

# Plan for Dvir  
git checkout dvir-feature
git push origin dvir-feature

# Auto-deploy to Dev
git checkout dev
git push origin dev
```

### 3. Manual Deploy

1. Go to **Actions** tab
2. Click **Deploy Infrastructure**
3. Click **Run workflow**
4. Choose environment and action

## What Gets Created

- EKS cluster (1.28)
- VPC with public/private subnets
- NAT gateways
- S3 bucket for terraform state
- DynamoDB for state locking

## Environments

| Branch | Environment | Action |
|--------|-------------|---------|
| `sivan-feature` | sivan | plan only |
| `dvir-feature` | dvir | plan only |
| `dev` | dev | auto apply |
| `stage` | stage | plan only |
| `prod` | prod | plan only |

## Files

```
├── .github/workflows/terraform-deploy.yml  # Pipeline
├── bootstrap/main.tf                       # S3/DynamoDB setup  
├── terraform/main.tf                       # EKS infrastructure
├── environments/                           # Environment configs
│   ├── sivan.tfvars
│   ├── dvir.tfvars  
│   ├── dev.tfvars
│   ├── stage.tfvars
│   └── prod.tfvars
└── k8s/deployment.yaml                     # App deployment
```

## Deploy the App

After EKS is ready:

```bash
# Get kubeconfig
aws eks update-kubeconfig --name sivan-guest-list-cluster --region us-west-2

# Deploy app
kubectl apply -f k8s/deployment.yaml

# Get service URL
kubectl get services
```

## Destroy Everything

1. Actions → Deploy Infrastructure → Run workflow
2. Select environment → destroy

This will remove both the EKS infrastructure AND the S3/DynamoDB state resources.

## Troubleshooting

- Check Actions tab for errors
- Verify AWS credentials in Secrets
- Make sure regions match (us-west-2)

---
Made for DevSecOps students 👨‍💻👩‍💻

