# Setting up Amazon DevOps Guru<a name="setting-up"></a>

Complete the tasks in this section to set up Amazon DevOps Guru for the first time\. If you already have an AWS account, know which AWS account or accounts you want to analyze, and have an Amazon Simple Notification Service topic to use for insight notifications, you can skip ahead to [Getting started with DevOps Guru](getting-started.md)\. 

Optionally, you can use Quick Setup, a capability of AWS Systems Manager, to set up DevOps Guru and quickly configure its options\. To use Quick Setup in Systems Manager, you must have the following prerequisites in place\.
+ An organization with AWS Organizations\. For more information, see [AWS Organizations terminology and concepts](https://docs.aws.amazon.com/organizations/latest/userguide/orgs_getting-started_concepts.html) in the *AWS Organizations User Guide*\.
+ Two or more organizational units \(OUs\)\.
+ One or more target AWS accounts in each OU\.
+ One administrator account with privileges to manage the target accounts\.

To learn how to set up DevOps Guru using Quick Setup, see [Configure DevOps Guru with Quick Setup](https://docs.aws.amazon.com/systems-manager/latest/userguide/quick-setup-devops.html) in the *AWS Systems Manager User Guide*\.

Use the following steps to set up DevOps Guru without Quick Setup\.
+ [Step 1 – Sign up for AWS](#setting-up-aws-sign-up)
+ [Step 2 – Determine coverage for DevOps Guru](#setting-up-determine-coverage)
+ [Step 3 – Identify your Amazon SNS notifications topic](#setting-up-notifications)

## Step 1 – Sign up for AWS<a name="setting-up-aws-sign-up"></a>

If you do not have an AWS account, complete the following steps to create one\.

**To sign up for an AWS account**

1. Open [https://portal\.aws\.amazon\.com/billing/signup](https://portal.aws.amazon.com/billing/signup)\.

1. Follow the online instructions\.

   Part of the sign\-up procedure involves receiving a phone call and entering a verification code on the phone keypad\.

## Step 2 – Determine coverage for DevOps Guru<a name="setting-up-determine-coverage"></a>

Your boundary coverage determines the AWS resources that are analyzed by Amazon DevOps Guru for anomalous behavior\. We recommend that you group your resources into your operational applications\. All the resources in your resource boundary should comprise one or more of your applications\. If you have one operational solution, then your coverage boundary should include all of its resources\. If you have multiple applications, choose the resources that make up each solution and group them together using AWS CloudFormation stacks or AWS tags\. All of the combined resources you specify, whether they define one or more applications, are analyzed by DevOps Guru and make up its coverage boundary\. 

Use one of the following methods to specify the resources in your operational solutions\.
+ Choose to have your AWS Region and account define your coverage boundary\. With this option, DevOps Guru analyzes all resources in your account and Region\. This is a good option to choose if you use your account for only one application\.
+ Use AWS CloudFormation stacks to define the resources in your operational application\. AWS CloudFormation templates define and generate your resources for you\. Specify the stacks that create your application resources when you configure DevOps Guru\. You can update your stacks at any time\. All of the resources in the stacks that you choose define your boundary coverage\. For more information, see [Use AWS CloudFormation stacks to identify resources in your DevOps Guru applications](working-with-cfn-stacks.md)\. 
+ Use AWS tags to specify AWS resources in your applications\. DevOps Guru analyzes only the resources that contain the tags you choose\. Those resources make up your boundary\.

  An AWS tag consists of a tag *key* and a tag *value*\. You can specify one tag *key* and you can specify one or more *values* with that *key*\. Use one *value* for all the resources in one of your applications\. If you have multiple applications, then use a tag with the same *key* for all of them, and group the resources into your applications using the tags' *values*\. All of the resources with the tags that you choose make up the coverage boundary for DevOps Guru\. For more information, see [Use tags to identify resources in your DevOps Guru applications](working-with-resource-tags.md)\.

If your boundary coverage includes resources that make up more than one application, you can use tags to filter your insights by to view them by one application at a time\. For more information, see Step 4 in [View DevOps Guru insights](working-with-insights.md#view-insights)\.

For more information, see [Define applications Using AWS resources](working-with-resource-collections.md)\. For more information about the supported services and resources, see [Amazon DevOps Guru pricing](http://aws.amazon.com/devops-guru/pricing/)\. 

## Step 3 – Identify your Amazon SNS notifications topic<a name="setting-up-notifications"></a>

You use one or two Amazon SNS topics to generate notifications about important DevOps Guru events, such as when an insight is created\. This ensures you know about issues that DevOps Guru finds as soon as possible\. Have your topics ready when you set up DevOps Guru\. When you use the DevOps Guru console to set up DevOps Guru, you specify a notification topic using its name or its Amazon Resource Name \(ARN\)\. For more information, see [Enable DevOps Guru](https://docs.aws.amazon.com/devops-guru/latest/userguide/getting-started-enable-service.html)\. You can use the Amazon SNS console to view the name and ARN for each of your topics\. If you don't have a topic, you can create one when you enable DevOps Guru using the DevOps Guru console\. For more information, see [Creating a topic](https://docs.aws.amazon.com/sns/latest/dg/sns-tutorial-create-topic.html) in the *Amazon Simple Notification Service Developer Guide*\. 

### Permissions added to your Amazon SNS topic<a name="permissions-added-to-sns-topic"></a>

An Amazon SNS topic is a resource that contains an AWS Identity and Access Management \(IAM\) resource policy\. When you specify a topic here, DevOps Guru appends the following permissions to its resource policy\.

```
{
    "Sid": "DevOpsGuru-added-SNS-topic-permissions",
    "Effect": "Allow",
    "Principal": {
        "Service": "region-id.devops-guru.amazonaws.com"
    },
    "Action": "sns:Publish",
    "Resource": "arn:aws:sns:region-id:topic-owner-account-id:my-topic-name",
    "Condition" : {
      "StringEquals" : {
        "AWS:SourceArn": "arn:aws:devops-guru:region-id:topic-owner-account-id:channel/devops-guru-channel-id",
        "AWS:SourceAccount": "topic-owner-account-id"
    }
  }
}
```

These permissions are required for DevOps Guru to publish notifications using a topic\. If you prefer to not have these permissions on the topic, you can safely remove them and the topic will continue to work as it did before you chose it\. However, if these appended permissions are removed, DevOps Guru cannot use the topic to generate notifications\. 