# Welcome to Home Temperature Monitoring Project

## Project Elements Overview

* [Raspberry Pi](https://www.raspberrypi.org/) - Micro computer
* [DHT11 Sensors]() - Can be purchased in various forms. This project uses sensors with intergrated resistors.
* [Python](https://www.python.org/) - Programming language
    * [Adafruit Python DHT library](https://github.com/adafruit/Adafruit_Python_DHT) - Python library for accessing sensors
    * [Boto3 Python library](https://boto3.amazonaws.com/v1/documentation/api/latest/index.html) - Python library to access AWS API calls from Python
* [Terraform](https://serverless.com/) - Management of local & cloud infrastructure
* [Ansible](https://serverless.com/) - Management of local & cloud infrastructure
* [Serverless Framework](https://serverless.com/) - Management of cloud infrastructure
* [AWS](https://aws.amazon.com/) - Cloud provider
    * [AWS CLI](https://aws.amazon.com/cli/) - AWS command line interface
    * [AWS IAM](https://aws.amazon.com/cli/) - AWS Identity Access Management
    * [AWS API Gateway](https://aws.amazon.com/api-gateway/) - AWS API Gateway
    * [AWS Lambda](https://aws.amazon.com/lambda/) - AWS lambda
    * [AWS DynamoDB](https://aws.amazon.com/dynamodb/) - AWS DynamoDB
    * [AWS EC2](https://aws.amazon.com/ec2/) - AWS EC2
        * [AWS ASG](https://docs.aws.amazon.com/autoscaling/ec2/userguide/AutoScalingGroup.html) - AWS Auto Scaling Groups
    * [AWS Elastc Load Balancing](https://aws.amazon.com/elasticloadbalancing/) - AWS ELB

More may be added as discovered & remembered.
Python libraries in Raspberry script


# Overview

## Data Gathering

The DHT sensors collect temperature and humidity information. This is passed to the Raspberry Pi over the GPIO pins, (NUMBERS), and used in a python script. The Pyhton script, (VERSION), is executed via cron every 15 minutes. The python script packages as JSON and sent via a POST to and API endpoint on AWS (API gateway).

### Data Gathering Hardware
Two Raspberry Pi zero W's are used, a Raspberry Pi 3 B and a Raspberry Pi 3 B +.
DHT11 sensors with inbuilt resistors are used to gather the data.


## Data Transmit
AWS API Gateway receives the call. When the call is received it triggers a lambda function that puts the data into a DynamoDB table. The lambda is written in Python, (VERSION), and uses the Boto3 library to interact with other AWS infrastructure, namely a Put call to DynamoDB. IAM also plays a role as the Lmabda function requires specific permissions to interact with other services in AWS. The principle of least privilege is used so as not to expose the underlying data stare to a bigger surface area of attack than is necessary.


## Data Storage
The DynamoDB table is then used as data source. Other elements access this to retrieve the data. Security Groups are used to limit possible access to the DynamoDB.

## Front End Infrastructure
This front end consists of a number of EC2 instances in an ASG (Auto Scaling Group) which is located behind a load balancer.

## Front End Software
To be decided upon.

## Who Monitors the Monitors
Datadog is used to monitor the over all project. Various metrics are used to ensure that the system is operating as intended and various alarms are in place to alert if there is an issue. This monitoring of the system is integrated into Slack.

ELK stack may also be implemented but further testing of this is required.
