# Azure_tflint_setup.ado
Use this template in Azure devops pipeline for the setting up the environment or dependencies for TFLint.

## Parameters:

The pipeline requires the following parameters to be defined:


| Name  | Displayname | type | Default | Values | Opional/Required | Comments |
| ------------- | ------------- | ------------- | ------------- | ------------- | ------------- | ------------- |
| workingDirectory | Name of the directory | string |  | | Required | This defines Path to the directory containing the Terraform configuration files to be linted |
| initbackend | Remote Backend to be used for Terraform | string | 'azure' | 'azure' | Required | This defines which backend to be taken into consideration |
| ProjectName | Name of the Project | string | 'Testing' | | Required | This enables to use different display name for the pipeline |
| terraformVersion | Terraform version | string |  | | Required | This defines the version of Terraform to be used |
| Agent.OS  | Name of the agent pool | string | 'Linux' | 'Linux' / 'Windows_NT' | Required | This defines which Agent pool to be used |



These parameters provide multiple use case options for the template, enable/disable flags for the utilization of different templates as per the requirements.


## Use Cases

You can directly call a particular template as per the requirement. for example: 

  ```yaml
  # azure-pipeline.yml
  resources:
  repositories:
    - repository: Template
      type: github
      name: your_username/Azure_tflint_setup.ado
      ref: <respective branch name>
      endpoint: 'githubServiceConnectioNname'

  steps:
  # passing the parameters
  - template: Azure_tflint_setup.yml
    parameters:
       workingDirectory: '${{ parameters.workingDirectory}}'
        
Make sure to adjust the repository name, branch name, and parameter values according to your project's requirements.

  ```
