# AWS Secure VPC Architecture & Network Security Lab

## Project Overview

Designed, deployed, and validated a segmented AWS network environment
to demonstrate foundational cloud security and network engineering
principles.

The environment uses an Amazon VPC with separate public and private
subnets, independent route tables, custom network ACLs, and an
Amazon Linux EC2 web server.

AWS CloudWatch and CloudTrail provide infrastructure monitoring and
management-event auditing.

## Project Objectives

- Implement network segmentation using Amazon VPC.
- Separate public-facing workloads from private network resources.
- Apply network access controls using security groups and NACLs.
- Restrict administrative SSH access to an authorized source IP.
- Configure IAM authentication with multi-factor authentication.
- Monitor EC2 CPU utilization using CloudWatch.
- Record AWS management activity using CloudTrail.
- Validate the architecture through connectivity and configuration tests.

## Architecture

**AWS Region:** US East (Ohio) — `us-east-2`

| Component | Configuration |
|---|---|
| VPC | `10.0.0.0/16` |
| Public Subnet | `10.0.1.0/24` |
| Private Subnet | `10.0.2.0/24` |
| Availability Zone | `us-east-2a` |
| Internet Connectivity | Internet Gateway and public route table |
| Private Routing | Local VPC route only |
| Compute | Amazon EC2 |
| Operating System | Amazon Linux 2023 |
| Web Server | Apache HTTP Server |
| Network Controls | Security Groups and Network ACLs |
| Monitoring | Amazon CloudWatch |
| Audit Logging | AWS CloudTrail |

![AWS Secure VPC Architecture](AWS%20secure%20architecture%20project%20diagram.png)

## Security Controls

### Network Segmentation

Created separate public and private subnets with independent
route tables to control network connectivity.

### Security Groups

Configured instance-level access controls to permit public HTTP
traffic while restricting SSH access to an authorized source IP.

### Network ACLs

Implemented custom subnet-level network ACLs to provide an
additional layer of traffic filtering.

### Identity and Access Management

Enabled MFA for the AWS root identity and administrative IAM user.
No IAM access keys were created for the administrative user.

### Monitoring

Configured a CloudWatch CPU utilization alarm for the EC2 web server.

### Audit Logging

Configured a multi-region CloudTrail trail to record management
events and deliver logs to Amazon S3. Log-file validation was enabled.

## Testing and Validation

| Test | Result |
|---|---|
| EC2 instance health checks | PASS |
| Public HTTP connectivity | PASS |
| Authorized SSH connectivity | PASS |
| CloudWatch CPU monitoring | VERIFIED |
| CloudTrail management-event logging | PASS |
| Public/private routing configuration | VERIFIED |

The private subnet's isolation was evaluated through route table
and network ACL configuration review. A separate live connectivity
test from a private-subnet workload was not performed.

The CloudWatch CPU alarm configuration was reviewed, but an actual high-CPU alarm trigger was not tested.

## Key Learning Outcomes

- Designed a segmented AWS network architecture.
- Configured public and private routing.
- Applied stateful and stateless network security controls.
- Troubleshot SSH connectivity and ephemeral-port requirements.
- Implemented cloud monitoring and audit logging.
- Validated infrastructure using AWS console evidence and connectivity tests.
- Applied cost-conscious resource management practices.

## Future Improvements

- Replace broad administrative permissions with a more restricted IAM policy.
- Test SSH access from an unauthorized source.
- Validate CloudWatch alarm behavior under high CPU utilization.
- Perform live private-subnet isolation testing.
- Implement Infrastructure as Code using Terraform.
- Explore AWS Systems Manager for administrative access.

## Project Status

**Infrastructure:** Implemented  
**Testing:** Initial validation completed  
**Documentation:** In progress  
**Portfolio Evidence:** Being organized
