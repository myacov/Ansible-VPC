# Ansible-VPC

## Cloud Automation with Ansible

Setting up a VPC 
- Security 
- High availability

Things to consider while setting up a VPC:
- Subnets, Nat Gateways, Internet Gateways, Route Tables
- NACL rules, security groups, instances, elastic IP
- Bastion Host (Jump server)
- dealing with future changes

Solution must include:
- configuration Management
- Automatic setup
- Centralized Change managment
- Version Control (IaaC)

## Architecture:
![Project diagram](./images/proj6.jpg)

## Tools and Services Used
| Tools | USE | 
| ------------- | ------------- | 
|🖥️ EC2 |  |
|🤖 Ansible | Automation tool |
| GitHub | Version control |



## Learning Objectives


## Implementation

1. **Launch EC2 Instance** 
control-machine for running ansible playbook
- pre installed with Ansible and Boto
2. **Create IAM role for Instance**
3. **Create Variable files for VPC & Bation host**
4. **Create VPC & Bation host setup playbooks**
5. **Create Site.yml playbook**


## Prerequisites:
- active AWS account

## Detailed Steps
### 1.  Security Groups Setup and EC2 Instances
#### Ansible Security group (**Ansible-SG**):

Inbound rules:
- SSH (Port 22) from **MY IP**
    Description: Allow SSH

#### control-machine Instance
- Name: **`control-machine`**
- Project: `Ansible-VPC`
- AMI: `Ubuntu Server 22.04 LTS`
- type: `t2.micro`
- Key pair: `ansible-ohio-key`
- Network settings: Security group: **ansible-SG**
- Advanced details: User data : 
```bash
    #!/bin/bash
    sudo apt update
    sudo apt install ansible -y
    sudo apt install awscli -y
    sudo apt install python3-boto3 -y
```

### 2. **Create IAM Role** 
1. we select appropriate policy and asign role to EC2 Instance

    test by runing:
``` 
    aws sts get-caller-identity
```

### 3. Create variable files: 
- [vpc_setup](vpc_setup)
- [bastion_setup](bastion_setup)


#### References and Documentation: 


 