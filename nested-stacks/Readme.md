# Use Nested Stacks

### AWS Best Practice Reference
[Use Nested Stacks to Reuse Common Template Patterns](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/best-practices.html#nested)


### Create a nested stack

**Note:** You should remove the previous stack before creating the ones below

Run the bash script deploy_and_run.sh to create the nested stack

## Removal

Remove the nested stack with the command:
aws cloudformation delete-stack  --stack-name nested-stack-example

