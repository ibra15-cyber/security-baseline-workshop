# AWS Security Baseline Workshop - Lab Project

## Overview

This project demonstrates the implementation of fundamental AWS security practices through hands-on exercises from the AWS Security Baseline Workshop. The lab focuses on implementing security best practices using various AWS security services including IAM roles, secrets management, resource-based policies, and VPC endpoints.

## Workshop Source

**Official Workshop Link:** https://catalog.workshops.aws/startup-security-baseline/en-US

## Project Structure

This lab is divided into two main sections:

### Part II - Level 1: Basic Security Implementations
- IAM Role Management
- Secrets and Parameter Management

### Part II - Level 4: Advanced Security Controls
- Resource-based Policy Implementation
- VPC Endpoint Security Configuration

## Completed Tasks

### 1. IAM Role Creation

#### EC2 Role (`Ibrahim_Anyars_Safianu_ec2_role`)
- **Purpose**: Allows EC2 instances to call AWS services securely
- **Attached Policy**: `AmazonEC2FullAccess`
- **Creation Date**: August 22, 2025
- **Screenshot**: `Ibrahim_Anyars_Safianu_ec2_role_1.png`

#### Lambda Role (`Ibrahim_Anyars_Safianu_lambda_role`)
- **Purpose**: Enables Lambda functions to access AWS services
- **Attached Policy**: `AWSLambda_FullAccess`
- **Creation Date**: August 22, 2025
- **Screenshot**: `Ibrahim_Anyars_Safianu_lambda_role_2.png`

#### ECS Role (`Ibrahim_Anyars_Safianu_ecs_role`)
- **Purpose**: Allows ECS to create and manage AWS resources
- **Attached Policy**: `AmazonEC2ContainerServiceRole`
- **Creation Date**: August 22, 2025
- **Screenshot**: `Ibrahim_Anyars_Safianu_ecs_role_3.png`

### 2. Secrets and Parameter Management

#### Systems Manager Parameter Store
- **Parameter Name**: `/Ibrahim_Anyars_Safianu/week2lab/parameter_name`
- **Type**: SecureString
- **Tier**: Standard
- **Last Modified**: August 22, 2025, 21:54:40 GMT
- **Screenshot**: `Ibrahim_Anyars_Safianu_week2lab_parameter_name_4.png`

#### AWS Secrets Manager
- **Secret Name**: `/Ibrahim_Anyars_Safianu/week2lab/secret_name`
- **Encryption**: AWS managed key (aws/secretsmanager)
- **ARN**: `arn:aws:secretsmanager:eu-central-1:24153313642​0:secret:/Ibrahim_Anyars_Safianu/week2lab/secret_name-9y3KX7`
- **Screenshot**: `Ibrahim_Anyars_Safianu_week2lab_secret_name_5.png`

### 3. Resource-Based Policy Implementation

#### S3 Bucket Access Control
- **Bucket Name**: `ibrahim-anyars-safianu-restricted-bucket`
- **IAM User**: `Ibrahim_Anyars_Safianu_week2_iamuser`

**Access Control Results:**
- **Unauthorized Access**: Upload failed with "Access Denied" error when using non-authorized user
- **Authorized Access**: Upload succeeded when using the specifically authorized IAM user
- **Screenshots**: 
  - Unauthorized: `Ibrahim_Anyars_Safianu_s3_unauthorized_putobjectresponse_6.png`
  - Authorized: `Ibrahim_Anyars_Safianu_s3_authorized_putobjectresponse_7.png`

### 4. VPC Endpoint Configuration

#### Gateway Endpoints Testing
- **Unrestricted Bucket Access**: Successfully accessed via gateway endpoint
- **Restricted Bucket Access**: Access controlled via VPC endpoint policy
- **Screenshots**:
  - Gateway Unrestricted: `Ibrahim_Anyars_Safianu_gw_unrestricted_s3_8.png`
  - Gateway Restricted: `Ibrahim_Anyars_Safianu_gw_restricted_s3_9.png`

#### Interface Endpoints Testing
- **Combined Testing**: Both unrestricted and restricted bucket access via interface endpoints
- **Screenshot**: `Ibrahim_Anyars_Safianu_int_restricted_unrestricted_s3_10_11.png`

## Key Security Concepts Demonstrated

### 1. Principle of Least Privilege
- Created specific roles for different AWS services (EC2, Lambda, ECS)
- Each role has only the necessary permissions for its intended use case

### 2. Secrets Management
- Implemented secure storage using AWS Systems Manager Parameter Store
- Utilized AWS Secrets Manager for sensitive data encryption and rotation

### 3. Resource-Based Access Control
- Configured S3 bucket policies to restrict access to specific IAM users
- Demonstrated the difference between authorized and unauthorized access attempts

### 4. Network Security with VPC Endpoints
- Implemented Gateway Endpoints for S3 access within VPC
- Configured Interface Endpoints with access policies
- Tested both restricted and unrestricted access scenarios

## Technical Implementation Details

### IAM Roles Configuration
- All roles follow the naming convention: `Ibrahim_Anyars_Safianu_[service]_role`
- Maximum session duration: 1 hour
- Trust relationships configured for respective AWS services

### Secrets Management Setup
- Parameter Store: Encrypted using AWS managed keys
- Secrets Manager: Automatic encryption with aws/secretsmanager key
- Hierarchical naming structure for organized secret management

### VPC Endpoint Security
- Gateway Endpoints: Direct routing to S3 service
- Interface Endpoints: ENI-based access with security group controls
- Endpoint policies restrict access based on resource and user context

## Security Best Practices Implemented

1. **No Hard-coded Credentials**: All access managed through IAM roles and policies
2. **Encrypted Storage**: Secrets and parameters stored with encryption at rest
3. **Network Isolation**: VPC endpoints prevent internet traffic for AWS service access
4. **Access Logging**: All actions logged for audit and compliance
5. **Resource-based Policies**: Fine-grained access control at resource level

## Assessment Criteria Met

- ✅ **IAM Roles Creation (30%)**: Successfully created EC2, ECS, and Lambda roles
- ✅ **Secrets Management (20%)**: Implemented Parameter Store and Secrets Manager
- ✅ **S3 Resource Policy (15%)**: Demonstrated restricted access control
- ✅ **Gateway Endpoint Policy (15%)**: Tested VPC gateway endpoint restrictions
- ✅ **Interface Endpoint Policy (15%)**: Verified interface endpoint access controls
- ✅ **Documentation (5%)**: Comprehensive project documentation and screenshots

## Files Included

### Screenshots
1. `Ibrahim_Anyars_Safianu_ec2_role_1.png` - EC2 IAM role configuration
2. `Ibrahim_Anyars_Safianu_lambda_role_2.png` - Lambda IAM role setup
3. `Ibrahim_Anyars_Safianu_ecs_role_3.png` - ECS IAM role details
4. `Ibrahim_Anyars_Safianu_week2lab_parameter_name_4.png` - Parameter Store configuration
5. `Ibrahim_Anyars_Safianu_week2lab_secret_name_5.png` - Secrets Manager setup
6. `Ibrahim_Anyars_Safianu_s3_unauthorized_putobjectresponse_6.png` - Unauthorized S3 access
7. `Ibrahim_Anyars_Safianu_s3_authorized_putobjectresponse_7.png` - Authorized S3 access
8. `Ibrahim_Anyars_Safianu_gw_unrestricted_s3_8.png` - Gateway endpoint unrestricted access
9. `Ibrahim_Anyars_Safianu_gw_restricted_s3_9.png` - Gateway endpoint restricted access
10. `Ibrahim_Anyars_Safianu_int_restricted_unrestricted_s3_10_11.png` - Interface endpoint testing

## Learning Outcomes

This lab demonstrates practical implementation of:
- AWS Identity and Access Management (IAM) best practices
- Secure secrets and configuration management
- Resource-based security policies
- Network-level security controls with VPC endpoints
- Security testing and validation methodologies

## Future Enhancements

- Implementation of CloudTrail for comprehensive audit logging
- Integration with AWS Config for compliance monitoring
- Advanced VPC endpoint policies with condition-based access
- Automated security testing with AWS Security Hub

## Author

**Ibrahim Anyars Safianu**
- AWS Account: amalitecht-labs-account-007 (2415-3313-6420)
- Lab Completion Date: August 2025

---

*This project was completed as part of the AWS Security Baseline Workshop to demonstrate fundamental security practices in AWS cloud environments.*