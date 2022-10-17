# Usage

Make sure you have AWS credentials in your environment. You can use the [AWS CLI](https://aws.amazon.com/cli/) to configure them.

```bash
aws iam create-role --role-name CodeDeployDemo-EC2-Instance-Profile --assume-role-policy-document file://CodeDeployDemo-EC2-Trust.json
```