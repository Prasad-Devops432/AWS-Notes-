AWSTemplateFormatVersion: 2010-09-09
Description: EC2 Instance Creation Template with Security Group and S3 Bucket

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
      KeyName: !Ref KeyName
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

  MyS3Bucket:
    Type: AWS::S3::Bucket
    Properties:
      BucketName: labbucket2023
      AccessControl: PublicRead
      Tags:
        - Key: Project
          Value: LabBucket

Outputs:
  InstanceId:
    Description: The Instance ID
    Value: !Ref MyEC2Instance

  PublicIP:
    Description: Public IP address of the EC2 instance
    Value: !GetAtt MyEC2Instance.PublicIp
