AWSTemplateFormatVersion: '2010-09-09'
Description: >
    CloudFormation template to launch a Python web application on an EC2 instance.
    This template creates a security group, an EC2 instance, and installs Python and a sample app.

Parameters:
    KeyName:
        Description: Name of an existing EC2 KeyPair to enable SSH access
        Type: AWS::EC2::KeyPair::KeyName

Resources:
    WebServerSecurityGroup:
        Type: AWS::EC2::SecurityGroup
        Properties:
            GroupDescription: Enable SSH and HTTP access
            SecurityGroupIngress:
              - IpProtocol: tcp
                FromPort: 22
                ToPort: 22
                CidrIp: 0.0.0.0/0   # SSH access from anywhere (for demo; restrict in production)
              - IpProtocol: tcp
                FromPort: 80
                ToPort: 80
                CidrIp: 0.0.0.0/0   # HTTP access from anywhere

    WebServerInstance:
        Type: AWS::EC2::Instance
        Properties:
            InstanceType: t2.micro
            KeyName: "your-keypair-name" # replace with your actual key name for local validation
            SecurityGroupIds:
                - Ref: WebServerSecurityGroup
            ImageId: ami-0c02fb55956c7d316 # Amazon Linux 2 AMI (update as needed for your region)
            UserData:
                Fn::Base64:
                    Fn::Sub: |
                        #!/bin/bash
                        yum update -y
                        yum install -y python3 git
                        cd /home/ec2-user
                        # Clone a sample Python app (replace with your repo if needed)
                        git clone https://github.com/heroku/python-getting-started.git
                        cd python-getting-started
                        pip3 install -r requirements.txt
                        # Run the app (Flask example)
                        nohup python3 app.py > app.log 2>&1 &
                        # Optionally, you can use a more robust process manager in production

Outputs:
    InstancePublicIP:
        Description: Public IP of the EC2 instance
        Value: 
          Fn::GetAtt: 
            - WebServerInstance
            - PublicIp
    WebAppURL:
        Description: URL to access the Python web app
        Value: 
          Fn::Sub: "http://${WebServerInstance.PublicDnsName}"
