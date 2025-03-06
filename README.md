# Configuring access to AWS

- We are going to use specific Account to access Parameter Store
- First create policy to access Parameter Store
- For Staging, it is going to be

```json
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": [
                "ssm:GetParameter",
                "ssm:GetParameters",
                "ssm:GetParametersByPath",
                "ssm:DescribeParameters"
            ],
            "Resource": "arn:aws:ssm:eu-central-1:905418385642:parameter/staging/secrets/*"
        }
    ]
}

```
- Where in resource eu-central-1 is region, 905418385642 is number of account that owns the resource, /staging/secrets/* is allowed path to parameters.
- Create group and attach policy to it
- Create user and add it to the group
- In kubernetes create namespace called external-secrets
- TO BE CONTINUED (Still don't know if this is the best way to do it)
