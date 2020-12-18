--------

Amazon DevOps Guru is in preview and available in the following AWS Regions: US West \(Oregon\), US East \(N\. Virginia\), US East \(Ohio\), Europe \(Ireland\), and Asia Pacific \(Tokyo\)\.

The preview is open to all AWS accounts\. You do not need to request access\. Features might be added or changed before General Availability is announced\. Contact us at [amazon\-devops\-guru\-feedback@amazon\.com](mailto:amazon-devops-guru-feedback@amazon.com) with feedback\.

--------

# Permissions for AWS KMS–encrypted Amazon SNS topics<a name="sns-kms-permissions"></a>

 

 The Amazon SNS topic you specify might be encrypted by AWS Key Management Service\. To allow DevOps Guru to work with encrypted topics, you must first create a customer\-managed key \(CMK\) and then add the following statement to the policy of the CMK\. For more information, see [Encrypting messages published to Amazon SNS with AWS KMS](http://aws.amazon.com/blogs/compute/encrypting-messages-published-to-amazon-sns-with-aws-kms/), [Key identifiers \(KeyId\)](https://docs.aws.amazon.com/kms/latest/developerguide/concepts.html#key-id) in the *AWS KMS User Guide*, and [Data encryption](https://docs.aws.amazon.com/sns/latest/dg/sns-data-encryption.html) in the *Amazon Simple Notification Service Developer Guide*\.

```
{
    "Version": "2012-10-17",
    "Id": "your-kms-key-policy",
    "Statement": [
        {
            "Effect": "Allow",
            "Principal": {
                "Service": "devops-guru.amazonaws.com"
            },
            "Action": [
                "kms:GenerateDataKey*",
                "kms:Decrypt"
            ],
            "Resource": "*"
        }
      ]
}
```