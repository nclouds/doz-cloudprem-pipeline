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

With the custom Cloudprem pipeline, a git repository with the parameters for your infrastructure will be used. In this case you have the options to configure your infrastructure with the parameters required for each of your environments. We offer two options for the custom pipeline: Using CodeCommit or a Github repository.

#### CodeCommit

The diagram below represents the architecture of the pipeline:

![distribution-pipeline-s3](https://app.lucidchart.com/publicSegments/view/b5bb6ea2-f6e3-4145-ba26-1c8dfda53f7a/image.png)

For the CodeCommit pipeline you need to perform two steps:

1. Deploy the *Cloudprem Repository* CloudFormation stack.

2. Deploy the *Cloudprem CodeCommit Pipeline* Stack for each of your environments.


| Stack  | Launch  |
|---|---|
| CloudPrem Repository  |  [![launch_stack](https://s3.amazonaws.com/cloudformation-examples/cloudformation-launch-stack.png)](https://console.aws.amazon.com/cloudformation/home?region=us-west-2#/stacks/new?stackName=cloudprem-repository&templateURL=https://s3.amazonaws.com/nclouds-cloudprem-assets/codecommit.yml) |
| CloudPrem CodeCommit Pipeline   |  [![launch_stack](https://s3.amazonaws.com/cloudformation-examples/cloudformation-launch-stack.png)](https://console.aws.amazon.com/cloudformation/home?region=us-west-2#/stacks/new?stackName=cloudprem-pipeline-dev&templateURL=https://s3.amazonaws.com/nclouds-cloudprem-assets/cc_pipeline.yml) |

#### Github

The diagram below represents the architecture of the pipeline:

![distribution-pipeline-gh](https://app.lucidchart.com/publicSegments/view/fec46c8d-2253-47f2-98d4-57c923307f61/image.png)

For the Github pipeline you need to perform the following steps:

1. Deploy the *Cloudprem Codestar* CloudFormation stack.

2. Go to the [Codestar console](https://us-west-2.console.aws.amazon.com/codesuite/codestar/projects) for the AWS region you are using, select the *cloudprem-github* connection and click on "Update connection". This will ask you to enter your Github credentials to complete the setup

3. Deploy the *Cloudprem Github Pipeline* Stack for each of your environments.


| Stack  | Launch  |
|---|---|
| CloudPrem Repository  |  [![launch_stack](https://s3.amazonaws.com/cloudformation-examples/cloudformation-launch-stack.png)](https://console.aws.amazon.com/cloudformation/home?region=us-west-2#/stacks/new?stackName=cloudprem-repository&templateURL=https://s3.amazonaws.com/nclouds-cloudprem-assets/codecommit.yml) |
| CloudPrem Github Pipeline   |  [![launch_stack](https://s3.amazonaws.com/cloudformation-examples/cloudformation-launch-stack.png)](https://console.aws.amazon.com/cloudformation/home?region=us-west-2#/stacks/new?stackName=cloudprem-pipeline-dev&templateURL=https://s3.amazonaws.com/nclouds-cloudprem-assets/github_pipeline.yml) |

*(Notes: Make sure to use the same environment name on the CloudFormation template and the Terraform parameters)*