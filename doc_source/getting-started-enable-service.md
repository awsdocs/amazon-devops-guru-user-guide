# Step 2: Enable DevOps Guru<a name="getting-started-enable-service"></a>

To configure Amazon DevOps Guru to use for the first time, you must choose which AWS resources in your account and Region is covered, or analyzed, and specify one or two Amazon Simple Notification Service topics that are used to notify you when an insight is created\. You can update these settings later as needed\. 

**Enable DevOps Guru**

1. Open the Amazon DevOps Guru console at [https://console\.aws\.amazon\.com/devops\-guru/](https://console.aws.amazon.com/devops-guru/)\.

1. In **DevOps Guru analysis coverage**, choose one of the following\. 
   + **Analyze all AWS resources in the current AWS account**: DevOps Guru analyzes all AWS resources in your account\. 
   + **Choose AWS resources to analyze later**: DevOps Guru analyzes only AWS resources that are defined in AWS CloudFormation stacks that you specify later\. 

   DevOps Guru can analyze any resource that is associated with the AWS it supports\. For more information about the supported services and resources, see [Amazon DevOps Guru pricing](http://aws.amazon.com/devops-guru/pricing/)\.

1. You can add up to two topics\. DevOps Guru uses the topic or topics to notify you about important DevOps Guru events, such as the creation of a new insight\. If you don't specify a topic now, you can add one later by choosing **Settings** in the navigation pane\. 

   1. In **Specify an Amazon SNS topic**, choose a topic to use\. 

   1.  To add an Amazon SNS topic, do one of the following\. 
      +  Choose **Chose an existing SNS topic in your AWS account**\. Then, from **Choose a topic in your AWS account**, choose the topic you want to use\. 
      +  Choose **Create a new SNS topic**\. Then, in **Create a new topic**, enter the name for your new topic\. 
      +  Choose **Use an SNS topic ARN to specify an existing account**\. Then, in **Enter an ARN for a topic**, enter the topic ARN\. The ARN is the topic's Amazon Resource Name\. You can specify a topic in a different account\. If you use a topic in another account, you must add a resource policy to the topic\. For more information, see [Permissions for cross account Amazon SNS topics](sns-required-permissions.md)\. 

   1.  Choose **Add SNS topic** if you want to add a second topic\. 

   1.  Choose **Save**\. 

1.  Choose **Enable**\. 