# Keep Your Resources from Drifting

### AWS Best Practice Reference
[Manage All Stack Resources Through AWS CloudFormation](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/best-practices.html#donttouch)

### Create the vpc-ec2

Create an vpc-subnet-ec2 with this command:
aws cloudformation create-stack --stack-name vpc-ec2 --template-body file://stack.yaml


## Removal

aws cloudformation delete-stack \
  --stack-name vpc-ec2
