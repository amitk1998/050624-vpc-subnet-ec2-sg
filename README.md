AWSTemplateFormatVersion: '2010-09-09'
Description: Template to create an EC2 instances

Parameters:
  InstanceType:
    Type: String
    Description: Type of EC2 instance
    Default: t2.micro
    AllowedValues:
      - t2.micro
      - t2.small
      - t2.medium
  KeyName:
    Type: AWS::EC2::KeyPair::KeyName
    Description: Name of an existing EC2 KeyPair to enable SSH access to the instance
    Default: Gravitee # Replace with your actual key pair name
  VpcId:
    Type: AWS::EC2::VPC::Id
    Description: VPC ID where the instance will be launched
    Default: vpc-02448f48814658f8b # Replace with your actual VPC ID
  SubnetId:
    Type: AWS::EC2::Subnet::Id
    Description: Subnet ID within the selected VPC
    Default: subnet-0b57dc05d3b2a0f85 # Replace with your actual Subnet ID
  InstanceSecurityGroup:
    Type: String
    Description: Security Group for the instance
    Default: sg-080309821f1012699 # Replace with your actual Security Group ID

Resources:
  MyEC2Instance:
    Type: AWS::EC2::Instance
    Properties:
      InstanceType: !Ref InstanceType
      KeyName: !Ref KeyName
      SubnetId: !Ref SubnetId
      ImageId: ami-0912f71e06545ad88 # Specify the AMI ID for the region
      SecurityGroupIds:
        - !Ref InstanceSecurityGroup
      BlockDeviceMappings:
        - DeviceName: /dev/xvda
          Ebs:
            VolumeSize: 20 # Size of the EBS volume in GB
            VolumeType: gp2 # General Purpose SSD
            DeleteOnTermination: true # Deletes the volume when instance is terminated
      Tags:
        - Key: Name
          Value: MyEC2Instance
        - Key: Environment
          Value: Production # Environment tag

Outputs:
  InstanceId:
    Description: The Instance ID
    Value: !Ref MyEC2Instance
  PublicIP:
    Description: Public IP address of the EC2 instance
    Value: !GetAtt MyEC2Instance.PublicIp