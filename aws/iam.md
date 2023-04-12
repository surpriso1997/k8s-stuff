#### Note on IAM role vs user
An IAM role can’t have long-term AWS credentials associated with it. Rather, an authorized principal (an IAM user, AWS service, or other authenticated identity) assumes the IAM role and inherits the permissions assigned to that role.
Credentials associated with an IAM role are temporary and expire.
An IAM role has a trust policy that defines which conditions must be met to allow other principals to assume it.

[AWS Permissions boundary Docs. Good one](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies_boundaries.html)