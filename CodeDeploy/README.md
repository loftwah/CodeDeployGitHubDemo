# Usage

[Create IAM instance profile](https://docs.aws.amazon.com/codedeploy/latest/userguide/getting-started-create-iam-instance-profile.html) | [Setting up AWS Systems Manager for EC2 instances](https://docs.aws.amazon.com/systems-manager/latest/userguide/systems-manager-setting-up-ec2.html) | [AWS Quick Setup](https://us-west-2.console.aws.amazon.com/systems-manager/quick-setup/?region=ap-southeast-2) | [Deploy the application to the instance](https://docs.aws.amazon.com/codedeploy/latest/userguide/tutorials-github-deploy-application.html)

Make sure you have AWS credentials in your environment. You can use the [AWS CLI](https://aws.amazon.com/cli/) to configure them.

- EC2 roles

```bash
aws iam create-role --role-name CodeDeployDemo-EC2-Instance-Profile --assume-role-policy-document file://CodeDeployDemo-EC2-Trust.json
aws iam put-role-policy --role-name CodeDeployDemo-EC2-Instance-Profile --policy-name CodeDeployDemo-EC2-Permissions --policy-document file://CodeDeployDemo-EC2-Permissions.json
aws iam attach-role-policy --policy-arn arn:aws:iam::aws:policy/AmazonSSMManagedInstanceCore --role-name CodeDeployDemo-EC2-Instance-Profile
aws iam create-instance-profile --instance-profile-name CodeDeployDemo-EC2-Instance-Profile
aws iam add-role-to-instance-profile --instance-profile-name CodeDeployDemo-EC2-Instance-Profile --role-name CodeDeployDemo-EC2-Instance-Profile
```

- CodeDeploy Roles

```bash
aws iam create-role --role-name CodeDeployServiceRole --assume-role-policy-document file://CodeDeployDemo-Trust.json
aws iam attach-role-policy --role-name CodeDeployServiceRole --policy-arn arn:aws:iam::aws:policy/service-role/AWSCodeDeployRole # varies if you use lamba or ecs
```

## Notes

Some of these steps were done in the console and could also be done via CLI. I just wanted to do them in the console to get an idea of which parts are going together.
