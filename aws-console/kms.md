# AWS Key Management Service: Console Walkthrough

**Mental model:** A KMS key is a policy-controlled cryptographic key used directly or by AWS services to protect data keys. Key policy is central: creating a key does not automatically mean every IAM principal can use it.

Related note: [AWS SSL-TLS.md](../../AWS%20SSL-TLS.md)

## Create a customer-managed symmetric key

1. Open [AWS KMS](https://console.aws.amazon.com/kms), choose the Region, then **Customer managed keys → Create key**.
2. Choose **Symmetric** and **Encrypt and decrypt** for the common service-encryption case. Choose multi-Region only when a specific cross-Region use case requires it.
3. Add an alias and description that contain no secret or personal data. Choose key administrators and key users deliberately. Keep key administration separate from routine use when possible.
4. Review the key policy carefully. Ensure you retain a controlled recovery/admin path; an unusable policy can lock out operators.
5. Add non-sensitive tags, review rotation settings and key policy, then create the key.
6. In a service such as S3 or EBS, choose the key from that service's encryption settings and verify the service principal and user role have the required permissions.

## Verify, rotate, and retire

Check key state, Region, aliases, policy, grants, rotation status, and CloudTrail usage. Key deletion is scheduled with a waiting period and can make data permanently unrecoverable after the key is deleted. Never schedule deletion until you have confirmed no encrypted data, backup, or service depends on it. Customer-managed keys have key and request charges; check current pricing.

**Remember:** **key metadata identifies; key policy authorizes; encrypted data depends on the key**.

**Official references:** [Create a KMS key](https://docs.aws.amazon.com/kms/latest/developerguide/create-keys.html) · [Create a symmetric key](https://docs.aws.amazon.com/kms/latest/developerguide/create-symmetric-cmk.html)
