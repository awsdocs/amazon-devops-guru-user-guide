--------

Amazon DevOps Guru is in preview and available in the following AWS Regions: US West \(Oregon\), US East \(N\. Virginia\), US East \(Ohio\), Europe \(Ireland\), and Asia Pacific \(Tokyo\)\.

The preview is open to all AWS accounts\. You do not need to request access\. Features might be added or changed before General Availability is announced\. Contact us at [amazon\-devops\-guru\-feedback@amazon\.com](mailto:amazon-devops-guru-feedback@amazon.com) with feedback\.

--------

# Permissions for cross account Amazon SNS topics<a name="sns-required-permissions"></a>

Use the information in this topic only if you want to configure Amazon DevOps Guru to deliver Amazon SNS topics owned by a different account than yours\. DevOps Guru must have permissions to send notifications to an Amazon SNS topic\. DevOps Guru adds the required policy on your behalf to send notifications using Amazon SNS topics in your AWS account\.

**Note**  
DevOps Guru currently only supports cross\-account access in the same Region\. 

If you want to use an Amazon SNS topic from another account, you must attach the following policy to the existing Amazon SNS topic\.

```
 {
  "Version": "2012-10-17",
  "Statement": [
    {
      "Action": "sns:Publish",
      "Effect": "Allow",
      "Resource": "arn:aws:sns:region-id:topic-owner-account-id:my-topic-name",
      "Principal": {
        "Service": "region-id.devops-guru.amazonaws.com"
      }
    },
    {
      "Action": "sns:Publish",
      "Effect": "Allow",
      "Resource": "arn:aws:sns:region:topic-owner-account-id:my-topic-name",
      "Principal": {
        "AWS": "arn:aws:iam::topic-sender-account-id:user/devops-guru-user-name"      	
       }
    }
  ]
}
```

For the `Resource` key, *topic\-owner\-account\-id* is the account ID of the topic owner, *topic\-sender\-account\-id* is the account ID of the user who set up DevOps Guru, and *devops\-guru\-user\-name* is the individual IAM user\. You must substitute appropriate values for *region\-id* \(for example, `us-west-2`\) and *my\-topic\-name*\. 