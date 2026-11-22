
# 8. AWS Application Deployment

## 8.1 Introduction

Amazon Web Services (AWS) provides the cloud environment used to host and run the application.

The project uses Amazon Elastic Container Registry (ECR) to store Docker images and Amazon Elastic Container Service (ECS) to manage application containers.

## 8.2 AWS Services

### Amazon ECR

Amazon Elastic Container Registry provides secure storage for Docker container images.

### Amazon ECS

Amazon Elastic Container Service manages container deployment and application availability.

### AWS Fargate

AWS Fargate provides serverless compute capacity for running ECS containers without managing EC2 instances.

### Application Load Balancer

The Application Load Balancer distributes incoming application requests across healthy application tasks.

### IAM

IAM manages access permissions for Jenkins and AWS services.

### CloudWatch

CloudWatch collects application logs, infrastructure metrics, and operational information.

## 8.3 Application Deployment Workflow

1. Jenkins builds the application.
2. Docker creates the container image.
3. Jenkins authenticates with Amazon ECR.
4. The image is tagged with a version.
5. The image is pushed to ECR.
6. The ECS task definition is updated with the new image.
7. The ECS service deploys the updated task.
8. Application health checks verify deployment success.

## 8.4 Authenticate Docker with Amazon ECR

Example:

```bash
aws ecr get-login-password --region AWS_REGION \
| docker login \
  --username AWS \
  --password-stdin AWS_ACCOUNT_ID.dkr.ecr.AWS_REGION.amazonaws.com
```

Replace the placeholders with your actual AWS account ID and region.

## 8.5 Tag Docker Image

```bash
docker tag end-to-end-devops-platform:1.0 \
AWS_ACCOUNT_ID.dkr.ecr.AWS_REGION.amazonaws.com/end-to-end-devops-platform:1.0
```

## 8.6 Push Image to ECR

```bash
docker push AWS_ACCOUNT_ID.dkr.ecr.AWS_REGION.amazonaws.com/end-to-end-devops-platform:1.0
```

## 8.7 ECS Deployment

The new container image is deployed by updating the ECS task definition and triggering an ECS service deployment.

The deployment process can be automated through Jenkins or AWS CDK.

## 8.8 Deployment Verification

Verify ECS service status:

```bash
aws ecs describe-services \
  --cluster CLUSTER_NAME \
  --services SERVICE_NAME \
  --region AWS_REGION
```

Verify running tasks:

```bash
aws ecs list-tasks \
  --cluster CLUSTER_NAME \
  --region AWS_REGION
```

Check application availability through its configured endpoint.

## 8.9 Security Considerations

- Use IAM roles with least-privilege permissions.
- Keep application tasks in private subnets where appropriate.
- Use HTTPS for external application traffic.
- Restrict security group access.
- Store secrets securely.
- Enable CloudWatch logging.

## 8.10 Conclusion

Amazon ECR and ECS provide container image management and application deployment capabilities, enabling an automated and scalable cloud application delivery process.
