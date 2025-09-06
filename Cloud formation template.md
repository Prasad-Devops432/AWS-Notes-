# Code for ASW-CFT 
# Code for ASW-CFT for The EC2 instance Creation Template
# This code creates an EC2 instance, a security group for SSH access, and an S3 bucket with public read access.
# Ensure to update the AMI ID and security group ID with valid values for your AWS region
AWSTemplateFormatVersion: 2010-09-09
Description: EC2 Instance Creation Template

Parameters:
  KeyName:
    Description: Name of an existing EC2 KeyPair to enable SSH access
    Type: AWS::EC2::KeyPair::KeyName

Resources:
  MyEC2Instance:
    Type: AWS::EC2::Instance
    Properties:
      InstanceType: t2.micro
      ImageId: ami-096fd57f2d61eec65 # Update with a valid AMI ID for your region
      KeyName: labkey
      SecurityGroupIds:
        - sg-06df394c86f8f97d0 # Update with a valid security group ID

  InstanceSecurityGroup:
    Type: AWS::EC2::SecurityGroup
    Properties:
      GroupDescription: Enable SSH access via port 22
      SecurityGroupIngress:
        - IpProtocol: tcp
          FromPort: 22
          ToPort: 22
          CidrIp: 0.0.0.0/0
  S3 Bucket:
    Type: AWS::S3::Bucket
    Properties:
      BucketName: labbucket2023
      AccessControl: PublicRead
      Tags:
        - Key: labkey
          Value: My S3 Bucket

Outputs:
  InstanceId:
    Description: The Instance ID
    Value: 
      Ref: MyEC2Instance
  PublicIP:
    Description: Public IP address of the EC2 instance
    Value: 
      Fn::GetAtt: 
        - MyEC2Instance
        - PublicIp

