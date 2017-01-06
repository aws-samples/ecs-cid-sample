# ECS Container draining
Amazon EC2 Container Service (Amazon ECS) is a container management service that makes it easy to run, stop, and manage Docker containers on a cluster of Amazon EC2 instances.  When you run tasks using Amazon ECS, you place them on a cluster, which is a logical grouping of EC2 instances. Amazon ECS downloads your container images from a registry that you specify, and runs those images on the container instances within your cluster.

There are times when EC2 instances need to be removed from the cluster, for example cluster scale-down or updating an AMI. Today we have delivered Container Instance Draining to simplify these scenarios. The draining state prevents new tasks from being started on the container instance, notifies the service scheduler to move tasks that are running on the instance to other instances in the cluster, and enables you to wait until tasks have successfully moved before terminating the instance.  



# Overview of steps
1. Download index.zip from this repository

2. Upload the downloaded index.zip containing Lambda code index.py to [Your_AWS_Account_S3_Bucket]

3. Download the Cloudformation template

4. Launch Cloudformation template that creates below AWS resources
    •	Cloudformation will require S3 bucket name as one of the parameters you created in Step 2 above.
    •	The VPC and associated network elements (subnets, security groups, route table, etc)
    •	ECS Cluster, ECS service, a sample ECS task definition
    •	Auto scaling group with two EC2 instances and a termination lifecycle hook
    •	Lambda function, permissions to invoke lambda, and lambda execution roles
    •	SNS topic, policy

For the full solution overview visit [Blog link](URL link here).

## Cloudformation template
 - cform/ecs.yaml

## Solution code
 - code/index.py

***

Copyright 2016 Amazon.com, Inc. or its affiliates. All Rights Reserved.

Licensed under the Amazon Software License (the "License"). You may not use this file except in compliance with the License. A copy of the License is located at

    http://aws.amazon.com/asl/

or in the "license" file accompanying this file. This file is distributed on an "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, express or implied. See the License for the specific language governing permissions and limitations under the License.
