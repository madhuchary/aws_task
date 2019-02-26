Apache using Docker in AWS

# Setup your environment 

## AWS Account

* Create an AWS account

* Create IAM user and assign administration access "AdministratorAccess" policy.

* Download accesskey and secretkey of above user.


## AWS Local Environment

* Install AWS CLI (For this demo I am using Ubuntu as my local workstation)

* sudo apt-get update

* sudo apt-get install python-pip

* sudo pip install awscli

* aws configure (paste your accesskey and secretkey key which you downloaded)

    * accesskey

    * secretkey

    * region (us-east-1)

    * output format

## Create ssh key

* ssh-keygen

## Import ssh key into AWS

* aws ec2 import-key-pair --key-name lncdemo --public-key-material file://~/.ssh/id_rsa.pub

## Setup ansible in your local environment

```
sudo apt-get update
sudo apt-get install -y software-properties-common
sudo apt-add-repository --yes --update ppa:ansible/ansible
sudo apt-get install -y ansible
sudo apt-get install -y python-pip
sudo pip install boto
sudo pip install boto3
```
## Clone 

git clone [https://github.com/harsha486264/assignment.git](https://github.com/harsha486264/assignment.git)

## Run ansible playbook

* cd assignment

* ansible-playbook lnc-demo.yml

## Get Instance public IP

* aws ec2 describe-instances --filters "Name=tag:Name,Values=lncinstance" |grep "PublicIpAddress"|awk -F: '{print "http://"$2}'|tr -d ' '|tr -d '"' | tr -d ','

* copy paste the url in the browser

