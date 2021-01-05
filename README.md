# CloudPrem Distribution Pipelines

This repository contains the CloudFormation templates for the CloudPrem distribution pipelines. The pipelines use CodeBuild and CodePipeline to automate the deployment of the CloudPrem Terraform infrastructure.

There are two options for your Cloudprem deployment mechanism, a managed and a custom version:

### Managed Pipeline

With the managed Cloudprem pipeline, you will use the pre-defined parameters managed and configured by Dozuki for each of the defined environments. In this case you will not be able to overwrite any of those parameters as the infrastructure configuration will be managed by Dozuki. The diagram below represents the architecture of the pipeline:

![distribution-pipeline-s3](https://app.lucidchart.com/publicSegments/view/07ae6aa6-5e42-40a3-8f20-3b3edf056286/image.png)

To deploy the pipeline click on the following Launch Stack button and follow the steps in the AWS console filling the required parameters.

| Stack  | Launch  |
|---|---|
| Cloudprem Managed Pipeline  |  [![launch_stack](https://s3.amazonaws.com/cloudformation-examples/cloudformation-launch-stack.png)](https://console.aws.amazon.com/cloudformation/home?region=us-west-2#/stacks/new?stackName=cloudprem-pipeline-dev&templateURL=https://s3.amazonaws.com/nclouds-cloudprem-assets/s3_pipeline.yml) |

You can create as many pipelines as you require for each of your environments, just keep in mind that you will require a different license file for each environment.

### Custom Pipeline

With the custom Cloudprem pipeline, a CodeCommit repository with the parameters for your infrastructure will be created. In this case you have the options to configure your infrastructure with the parameters required for each of your environments. The diagram below represents the architecture of the pipeline:

![distribution-pipeline-s3](https://app.lucidchart.com/publicSegments/view/b5bb6ea2-f6e3-4145-ba26-1c8dfda53f7a/image.png)

For the custom pipeline you need to perform two steps:

1. Deploy the *Cloudprem Repository* CloudFormation stack.

2. Deploy the *Cloudprem Custom Pipeline* Stack for each of your environments.


| Stack  | Launch  |
|---|---|
| CloudPrem Repository  |  [![launch_stack](https://s3.amazonaws.com/cloudformation-examples/cloudformation-launch-stack.png)](https://console.aws.amazon.com/cloudformation/home?region=us-west-2#/stacks/new?stackName=cloudprem-repository&templateURL=https://s3.amazonaws.com/nclouds-cloudprem-assets/codecommit.yml) |
| CloudPrem Custom Pipeline   |  [![launch_stack](https://s3.amazonaws.com/cloudformation-examples/cloudformation-launch-stack.png)](https://console.aws.amazon.com/cloudformation/home?region=us-west-2#/stacks/new?stackName=cloudprem-pipeline-dev&templateURL=https://s3.amazonaws.com/nclouds-cloudprem-assets/cc_pipeline.yml) |