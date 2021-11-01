# Permissions for cross account Amazon SNS topics<a name="sns-required-permissions"></a>

Use the information in this topic only if you want to configure Amazon DevOps Guru to deliver Amazon SNS topics owned by a different account than yours\. 

For DevOps Guru to deliver an Amazon SNS topic owned by a different account, you must attach to it a policy that grants DevOps Guru permissions to send notifications to it\. If you configure DevOps Guru to deliver Amazon SNS topics owned by your account, then DevOps Guru adds a policy to the topics for you\.

**Note**  
DevOps Guru currently only supports cross\-account access in the same Region\. 

To use an Amazon SNS topic from another account, attach the following policy to the existing Amazon SNS topic\. For the `Resource` key, *topic\-owner\-account\-id* is the account ID of the topic owner, *topic\-sender\-account\-id* is the account ID of the user who set up DevOps Guru, and *devops\-guru\-user\-name* is the individual IAM user\. You must substitute appropriate values for *region\-id* \(for example, `us-west-2`\) and *my\-topic\-name*\. 

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
      },
      "Condition" : {
        "StringEquals" : {          
          "AWS:SourceAccount": "topic-sender-account-id"
      }
    },
    {
      "Action": "sns:Publish",
      "Effect": "Allow",
      "Resource": "arn:aws:sns:region-id:topic-owner-account-id:my-topic-name",
      "Principal": {
        "AWS": "arn:aws:iam::topic-sender-account-id:user/devops-guru-user-name"      	
      }
    }
  ]
}
```



After you add a topic, we recommend that you make your policy more secure by specifying permissions for only the DevOps Guru notification channel that contains your topic\.

**Update your Amazon SNS topic policy with a notification channel \(recommended\)**

1. Run the `list-notification-channels` DevOps Guru AWS CLI command\.

   ```
   aws devops-guru list-notification-channels
   ```

1. In the `list-notification-channels` response, make a note of the channel ID that contains your Amazon SNS topic's ARN\. The channel ID is a guid\.

   For example, in the following response, the channel ID for the topic with the ARN `arn:aws:sns:region-id:111122223333:topic-name` is `e89be5f7-989d-4c4c-b1fe-e7145037e531`

   ```
   {
     "Channels": [
       {
         "Id": "e89be5f7-989d-4c4c-b1fe-e7145037e531",
         "Config": {
         "Sns": {
             "TopicArn": "arn:aws:sns:region-id:111122223333:topic-name"
           }
         }
       }
     ]
   }
   ```

1. In the `Condition` statement of your policy, add the line that specifies the `SourceArn`\. The ARN contains your Region ID \(for example, `us-east-1`\), the AWS account number of the topic's sender, and the channel ID you made a note of\. 

   Your updated `Condition` statement looks like the following\.

   ```
   "Condition" : {
     "StringEquals" : {
       "AWS:SourceArn": "arn:aws:devops-guru:us-east-1:111122223333:channel/e89be5f7-989d-4c4c-b1fe-e7145037e531",
       "AWS:SourceAccount": "111122223333"
      } 
    }
   ```