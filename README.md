# VPC Peering Demo - Using CloudFormation Template

## Description
This project demonstrates VPC Peering using a CloudFormation template. It provisions two VPCs (VPCA and VPCB) along with necessary subnets, security groups, and EC2 instances within those VPCs.

## Provisioning Infrastructure
To provision the infrastructure, follow the steps below:

1. **Template:** Use the provided CloudFormation template to provision the infrastructure.

    ```yaml
    Description: VPC Peering Demo
    Parameters:
      LatestAmiId:
        Description: AMI for Bastion Host (default is latest AmaLinux2)
        Type: 'AWS::SSM::Parameter::Value<AWS::EC2::Image::Id>'
        Default: '/aws/service/ami-amazon-linux-latest/amzn2-ami-hvm-x86_64-gp2'
    Resources:
      VPCA:
        Type: AWS::EC2::VPC
        Properties:
          CidrBlock: 10.16.0.0/16
          EnableDnsSupport: true
          EnableDnsHostnames: true
          Tags:
            - Key: Name
              Value: vpc-a
      VPCB:
        Type: AWS::EC2::VPC
        Properties:
          CidrBlock: 10.17.0.0/16
          EnableDnsSupport: true
          EnableDnsHostnames: true
          Tags:
            - Key: Name
              Value: vpc-b
      ...
    ```

2. **Creation Steps:**
   - Go to AWS CloudFormation in your AWS account.
   - Create a stack and follow the steps provided by AWS.
   - Specify stack details and configure stack options.
   - Proceed to provision the infrastructure.

## VPC Peering
Once the infrastructure is provisioned, follow the steps below to establish VPC peering:

1. **Create Peering Connections:**
   - Go to the VPC dashboard.
   - Create peering connections.
   - Add details of both VPCs.

2. **Configure Security Groups:**
   - Change the security group for VPCB to allow All ICMP - IPv4 from VPCA security group.

3. **SSH and Ping:**
   - SSH into an EC2 instance in VPCA.
   - Ping an EC2 instance in VPCB using its private IP address.

## Systematic Steps:
To ensure a systematic process, follow these steps:
1. Provision infrastructure using CloudFormation.
2. Create peering connections between VPCs.
3. Configure security groups accordingly.
4. Test connectivity between instances using SSH and Ping.

