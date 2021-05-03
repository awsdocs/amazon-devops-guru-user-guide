# Working with AWS CloudFormation stacks in DevOps Guru<a name="working-with-cfn-stacks"></a>

You can use AWS CloudFormation stacks to specify which AWS resources you want DevOps Guru to analyze\. A stack is a collection of AWS resources that are managed as a single unit\. The resources in the stacks you choose make up your DevOps Guru coverage boundary\. For each stack you choose, operational data in its supported resources are analyzed for anomalous behavior\. Those issues are then grouped into related anomalies to create insights\. Each insight includes one or more recommendations to help you address them\. The maximum number of stacks you can specify is 500\. For more information, see [Working with stacks](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/stacks.html) in the *AWS CloudFormation User Guide* and [Update your AWS analysis coverage in DevOps Guru](update-settings.md#update-coverage)\. 

After you choose a stack, DevOps Guru immediately starts to analyze any resource you add to it\. If you remove a resource from a stack, it is no longer analyzed\. 

**Note**  
If you choose to have DevOps Guru analyze all supported resources in your account \(this means your account is your DevOps Guru coverage boundary\), then DevOps Guru analyzes and creates insights for every supported resource in your account\. While all your insights appear in the console, only the insights created for a resource that belongs to one of the first 500 stacks analyzed appear as part of a stack\. 

## Choose stacks for DevOps Guru to analyze<a name="choose-stacks"></a>

Specify the resources that you want Amazon DevOps Guru to analyze by choosing the AWS CloudFormation stacks that create them\. You can do this using the AWS Management Console or the SDK\. 

**Topics**
+ [Choose stacks for DevOps Guru to analyze \(console\)](#choose-stacks-console)
+ [Choose stacks for DevOps Guru to analyze \(DevOps Guru SDK\)](#choose-stacks-sdk)

### Choose stacks for DevOps Guru to analyze \(console\)<a name="choose-stacks-console"></a>

 You can add AWS CloudFormation stacks using the console\. 

**To choose the stacks that contain the resources to analyze**

1. Open the Amazon DevOps Guru console at [https://console\.aws\.amazon\.com/devops\-guru/](https://console.aws.amazon.com/devops-guru/)\.

1. Open the navigation pane, then choose **Settings**\. 

1. In **DevOps Guru analysis coverage**, choose **Manage**\. 

1. If you have not enabled any stacks, in **CloudFormation stacks**, choose **Manage analysis coverage**\. 

1. Select up to 500 stacks that contain the resources that you want analyzed\. You can enter the name of a stack in **Find stacks** to quickly locate a specific stack\. 

1. Choose **Save**\. 

### Choose stacks for DevOps Guru to analyze \(DevOps Guru SDK\)<a name="choose-stacks-sdk"></a>

To specify AWS CloudFormation stacks using the Amazon DevOps Guru SDK, use the `UpdateResourceCollection` method\. For more information, see [UpdateResourceCollection](https://docs.aws.amazon.com/devops-guru/latest/APIReference/API_UpdateResourceCollection.html) in the *Amazon DevOps Guru API Reference*\. 