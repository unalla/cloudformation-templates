# Use IAM Service Roles for CloudFormation permissions

### AWS Best Practice Reference
[Use IAM to Control Access](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/best-practices.html#use-iam-to-control-access)



### Create an IAM service role
Create an IAM role with only these permissions:
- `dynamodb:CreateTable`
- `dynamodb:DescribeTable`
- `dynamodb:DeleteTable`
Or

Create the IAM service role with this command:
aws cloudformation create-stack  --stack-name service-role --template-body file://service-role.yaml   --capabilities CAPABILITY_NAMED_IAM


### Create the stack with the service role

Get the role ARN

Create the stack with the command:
aws cloudformation create-stack  --stack-name iam-service-roles   --template-body file://stack.yaml   --role-arn "<insert iam role arn>"


## Removal

Remove the example stack with the command:
aws cloudformation delete-stack   --stack-name iam-service-roles

Then, remove the role stack with this command:
aws cloudformation delete-stack  --stack-name service-role
