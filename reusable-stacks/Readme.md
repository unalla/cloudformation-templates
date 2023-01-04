# Reuse CloudFormation Templates

### AWS Best Practice Reference
[Reuse Templates to Replicate Stacks in Multiple Environments](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/best-practices.html#reuse)


### Create a reusable stack with parameters

aws cloudformation create-stack  --stack-name parameters-example  --template-body file://reusable-parameters.yaml   --region us-west-2 \
  --parameters  ParameterKey=ApplicationName,ParameterValue=tpb  ParameterKey=SubnetAZ,ParameterValue=us-west-2a

Now, create the same stack with a parameters file

aws cloudformation create-stack  --stack-name parameters-file-example  --template-body file://reusable-parameters.yaml  --region us-west-2 --parameters file://parameters.json


### Create a reusable stack with mappings

**Note:** You should remove the previous stack before creating the ones below


aws cloudformation create-stack \
  --stack-name mappings-example \
  --template-body file://reusable-mappings.yaml \
  --region us-west-2 \
  --capabilities CAPABILITY_IAM \
  --parameters \
    ParameterKey=ApplicationName,ParameterValue=hbfl \
    ParameterKey=SubnetAZ,ParameterValue=us-west-2a \
    ParameterKey=Platform,ParameterValue=node


### Create a reusable stack with conditions

**Note: You should remove the previous stack before creating the ones below


aws cloudformation create-stack \
  --stack-name conditions-example \
  --template-body file://reusable-conditions.yaml \
  --region us-west-2 \
  --parameters \
    ParameterKey=ApplicationName,ParameterValue=hbfl \
    ParameterKey=SubnetAZ,ParameterValue=us-west-2a \
    ParameterKey=VPCState,ParameterValue=existing


## Removal

Then, remove the parameters stacks with these commands:

aws cloudformation delete-stack --stack-name parameters-file-example


And, remove the mappings stack with this command:

aws cloudformation delete-stack --stack-name mappings-example


Finally, remove the conditions stack with this command:

aws cloudformation delete-stack   --stack-name conditions-example
