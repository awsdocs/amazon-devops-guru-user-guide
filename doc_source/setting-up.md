--------

Amazon DevOps Guru is in preview and available in the following AWS Regions: US West \(Oregon\), US East \(N\. Virginia\), US East \(Ohio\), Europe \(Ireland\), and Asia Pacific \(Tokyo\)\.

The preview is open to all AWS accounts\. You do not need to request access\. Features might be added or changed before General Availability is announced\. Contact us at [amazon\-devops\-guru\-feedback@amazon\.com](mailto:amazon-devops-guru-feedback@amazon.com) with feedback\.

--------

# Setting up Amazon DevOps Guru<a name="setting-up"></a>

Complete the tasks in this section to set up Amazon DevOps Guru for the first time\. If you already have an AWS account, know which AWS account or accounts you want to analyze, and have an Amazon Simple Notification Service topic to use for insight notifications, you can skip ahead to [Getting started with DevOps Guru](getting-started.md)\. 

**Topics**
+ [Sign up for AWS](#setting-up-aws-sign-up)
+ [Determine coverage for DevOps Guru](#setting-up-determine-coverage)
+ [Identify your Amazon SNS notifications topic](#setting-up-notifications)

## Sign up for AWS<a name="setting-up-aws-sign-up"></a>

If you do not have an AWS account, complete the following steps to create one\.

**To sign up for an AWS account**

1. Open [https://portal\.aws\.amazon\.com/billing/signup](https://portal.aws.amazon.com/billing/signup)\.

1. Follow the online instructions\.

   Part of the sign\-up procedure involves receiving a phone call and entering a verification code on the phone keypad\.

## Determine coverage for DevOps Guru<a name="setting-up-determine-coverage"></a>

Think about how you want to configure coverage for Amazon DevOps Guru\. Coverage determines the AWS resources that are covered, or analyzed, to detect anomalous behavior\. You want DevOps Guru to cover the AWS resources that are created by the AWS services that make up your operational solutions\. You have two options\. 

1. By default, DevOps Guru analyzes all supported AWS resources in your AWS Region and account\. If you do not specify AWS CloudFormation stacks that define specific resources to cover, then all resources in your account are covered\. 

1. You can use AWS CloudFormation stacks to specify which resources are analyzed by DevOps Guru\. Think about which resources you need, then create AWS CloudFormation templates that define and generate those resources for you\. You specify your stacks when you configure DevOps Guru\. You can also update your stacks at any time\. For more information, see [Working with AWS CloudFormation stacks in DevOps Guru](working-with-cfn-stacks.md)\. 

 For more information, see [Getting started with DevOps Guru](getting-started.md)\. For more information about the supported services and resources, see [Amazon DevOps Guru pricing](http://aws.amazon.com/devops-guru/pricing/)\. 

## Identify your Amazon SNS notifications topic<a name="setting-up-notifications"></a>

You use one or two Amazon SNS topics to generate notifications about important DevOps Guru events, such as when an insight is created\. This ensures you know about issues that DevOps Guru finds as soon as possible\. Have your topics ready when you set up DevOps Guru\. When you use the DevOps Guru console to set up DevOps Guru, you specify a notification topic using its name or its Amazon Resource Name \(ARN\)\. For more information, see [Enable DevOps Guru](https://docs.aws.amazon.com/devops-guru/latest/userguide/getting-started-enable-service.html)\. You can use the Amazon SNS console to view the name and ARN for each of your topics\. If you don't have a topic, you can create one when you enable DevOps Guru using the DevOps Guru console\. For more information, see [Creating a topic](https://docs.aws.amazon.com/sns/latest/dg/sns-tutorial-create-topic.html) in the *Amazon Simple Notification Service Developer Guide*\. 