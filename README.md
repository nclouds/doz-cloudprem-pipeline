# CloudPrem Deployment Pipeline infrastructure

This repository contains the CloudFormation templates to create the CloudPrem deployment pipeline. The pipeline uses CodeBuild and CodePipeline to automate the deployment of the CloudPrem infrastructure with Terraform. 


| Stack  | Launch  |
|---|---|
| CloudPrem Repository  |  [![launch_stack](https://s3.amazonaws.com/cloudformation-examples/cloudformation-launch-stack.png)](https://console.aws.amazon.com/cloudformation/home?region=us-west-2#/stacks/new?stackName=cloudprem-repository&templateURL=https://s3.amazonaws.com/nclouds-cloudprem-assets/repository.yml) |
| CloudPrem Deployment Pipeline   |  [![launch_stack](https://s3.amazonaws.com/cloudformation-examples/cloudformation-launch-stack.png)](https://console.aws.amazon.com/cloudformation/home?region=us-west-2#/stacks/new?stackName=cloudprem-pipeline-dev&templateURL=https://s3.amazonaws.com/nclouds-cloudprem-assets/pipeline.yml) |