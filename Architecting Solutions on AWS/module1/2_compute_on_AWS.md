# Compute on AWS — Architecture Decision Notes

---

## Choosing a Compute Service (EXAM CRITICAL)
When selecting a compute service, consider:
- Workload characteristics
- Operational overhead
- Scalability requirements
- Performance efficiency
- Cost optimization
- Level of infrastructure control needed

Always evaluate:
- New AWS service releases
- Managed vs self-managed tradeoffs

---

# AWS Lambda (Chosen for This Architecture)

## Why Lambda Was Selected
For the Orders Service use case:
- Serverless compute
- Supports web backends
- Handles spiky workloads
- Minimizes operational overhead

---

## What Is AWS Lambda?
- Serverless compute service
- Runs code in response to:
  - Events
  - Triggers
- Each invocation runs in:
  - An isolated execution environment
- Maximum runtime:
  - 15 minutes

---

## Key Characteristics

### Serverless
- No servers to provision
- No OS management
- No patching required

### Automatic Scaling
- Scales automatically with demand
- No idle resource costs

### Cost Model
- Pay only for:
  - Execution time
  - Memory allocated
- No cost when idle

---

## Limitations
- Cannot customize OS
- Cannot log into instances
- Maximum runtime of 15 minutes

---

## Ideal Lambda Use Cases
- Web backends
- Mobile backends
- IoT backends
- Stream processing
- File processing
- Event-driven workloads

---

# Amazon API Gateway (Frontend for Lambda)

## Why API Gateway?
- Exposes Lambda securely
- Acts as the API entry point
- Avoids exposing backend directly

---

## What API Gateway Provides
- Traffic management
- Throttling
- Authentication
- Authorization
- Monitoring
- Versioning
- CORS handling

---

## Cost Model
- Pay per API call
- Pay for data transferred out
- No minimum cost

---

# Amazon EC2 (Why It Was Not Chosen)

## What EC2 Offers
- Full control over:
  - OS
  - Networking
  - Security
  - Software stack
- Multiple instance types and pricing models

---

## Why EC2 Was Not Ideal
- Higher operational overhead
- Requires capacity planning
- Less efficient for spiky demand
- Customer wants reduced management effort

---

# AWS Container Services (Not Chosen Here)

## Categories of Container Management
1. Registry
2. Orchestration
3. Compute

---

# Amazon ECS
- Managed container orchestration
- Serverless option with AWS Fargate
- Secure and integrated with AWS

---

# Amazon EKS
- Managed Kubernetes
- Runs Kubernetes control plane
- Integrates with IAM, VPC, ECR, ELB

---

# AWS Fargate
- Serverless compute for containers
- No EC2 cluster management
- Each task isolated
- Supports Fargate Spot for cost savings

---

## Why Containers Were Not Chosen
- Customer preference
- Simpler serverless Lambda solution met requirements
- Avoid introducing unnecessary complexity

---

# Architecture Decision Summary (EXAM TAKEAWAY)

| Requirement | Chosen Service |
|-------------|----------------|
| Spiky demand | AWS Lambda |
| Low operational overhead | AWS Lambda |
| API exposure | API Gateway |
| Decoupled backend | Event-driven + serverless |
| Managed scaling | Lambda |
| Cost efficiency | Pay-per-use serverless |

---

## Final Key Insight
For this use case:
- **Serverless > EC2**
- Lambda minimizes idle costs
- API Gateway securely exposes backend
- Containers were unnecessary complexity

➡️ Match compute service to workload characteristics.
