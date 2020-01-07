# blockchain-on-fargate
Project for Blockchain on AWS Fargate


Deployment on Fargate using ECS Runtime:

1. The first step is to deploy the VPC Fargate Networking stack:

aws cloudformation deploy --template-file=deployment/ecs-cf-template/vpc-stack.yaml --stack-name=FargateECSNetworkingStack --capabilities CAPABILITY_IAM
 
2. Please note the name of the stack-name previously provided in the command, i.e. FargateECSNetworkingStack. The previous stack exports several values which are later used in the deployment of Blockchain service stack. 

3. Final step is to deploy the service stack:

aws cloudformation deploy --template-file=deployment/ecs-cf-template/service-stack.yaml --stack-name=FargateECSServiceStack --capabilities CAPABILITY_IAM


4. Once created, we need to enable to Container Insights.

$ aws ecs put-account-setting --name "containerInsights" --value "enabled" --profile rvd-test-dev

and then

$ aws ecs update-cluster-settings --cluster FargateNetworkingStack-ECSCluster-BW652L6JV184 --settings name=containerInsights,value=enabled --profile=rvd-test-dev