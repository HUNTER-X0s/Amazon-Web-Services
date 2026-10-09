# AWS Secrets Manager: Console Walkthrough

**Mental model:** A secret is encrypted sensitive data with a managed version history. Applications should request it at runtime using an IAM role; they should not copy a value into source code or an image.

Related notes: [AWS RDS.md](../../AWS%20RDS.md) · [AWS DynamoDB.md](../../AWS%20DynamoDB.md)

## Store a practice secret

1. Open [Secrets Manager](https://console.aws.amazon.com/secretsmanager/), choose the Region, and select **Store a new secret**.
2. Choose the right type: database credentials for a supported database, or **Other type of secret** for a test token/key. Enter only a sandbox value; do not use a production credential for a tutorial.
3. Choose the KMS encryption key. The AWS managed Secrets Manager key is suitable for many cases; a customer-managed key allows additional policy control but adds key configuration and possible charges.
4. Give the secret a neutral name and description. Do not put the secret value, personal data, or passwords in the name, description, or tags.
5. Review resource permissions and replication. Keep resource access narrow. Set up automatic rotation only after the target system and rotation schedule are prepared.
6. Choose **Store**. Open the secret and confirm its name, current version, Region, and KMS key.

## Let an application retrieve it

1. Add `secretsmanager:GetSecretValue` for this secret's ARN to the application's IAM role; add `kms:Decrypt` only when required by the selected customer-managed key.
2. Configure the application to retrieve the secret from Secrets Manager at runtime and avoid logging its value.
3. Test with a sandbox secret and check CloudTrail for access events. For RDS, consider the database service's managed-secret integration and rotation support.

## Clean up

Schedule deletion only after dependent applications are updated. Secrets Manager charges per secret and API calls; replicated secrets and customer-managed keys can add costs.

**Remember:** **store once → grant by role → retrieve at runtime → rotate deliberately**.

**Official references:** [Create a secret](https://docs.aws.amazon.com/secretsmanager/latest/userguide/create_secret.html) · [Retrieve a secret in the console](https://docs.aws.amazon.com/secretsmanager/latest/userguide/retrieving-secrets-console.html)
