# blockchain-on-fargate
Project for Blockchain on AWS Fargate


Deployment on Fargate using ECS Runtime:

aws cloudformation deploy --template-file=deployment/ecs-cf-template/vpc-stack.yaml --stack-name=FargateECSNetworkingStack --capabilities CAPABILITY_IAM

