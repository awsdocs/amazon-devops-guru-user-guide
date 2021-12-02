# Step 3: Specify your DevOps Guru resource coverage<a name="choose-coverage"></a>

If you chose to specify AWS resources later when you enabled DevOps Guru, you need to choose the AWS CloudFormation stacks in your AWS account that create the resources you want analyzed\. An AWS CloudFormation stack is a collection of AWS resources that you manage as a single unit\. You can use one or more stacks to include all the resources required to run your operational applications, then specify them so that they are analyzed by DevOps Guru\. If you don't specify stacks, then DevOps Guru analyzes all the AWS resources in your account\. For more information, see [Working with stacks](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/stacks.html) in the *AWS CloudFormation User Guide*, and [Determine coverage for DevOps Guru](setting-up.md#setting-up-determine-coverage)\. and [Use AWS CloudFormation stacks to identify resources in your DevOps Guru applications](working-with-cfn-stacks.md)\.

**Note**  
For more information about supported services and resources, see [Amazon DevOps Guru pricing](http://aws.amazon.com/devops-guru/pricing/)\.

**Specify AWS CloudFormation stacks for DevOps Guru resource coverage**

1. Open the Amazon DevOps Guru console at [https://console\.aws\.amazon\.com/devops\-guru/](https://console.aws.amazon.com/devops-guru/)\.

1. Expand **Settings** in the navigation pane\. 

1. In **Analyzed resources**, choose **Edit**\.

1. Choose one of the following coverage options\. 
   + Choose **All account resources** if you want DevOps Guru to analyze all supported resources in your AWS account and Region\. If you choose this option, your AWS account is your resource analysis coverage boundary\. All resources in each stack in your account are grouped into their own application\. Any remaining resources that are not in a stack are grouped into their own application\.
   + Choose **CloudFormation stacks** if you want DevOps Guru to analyze the resources that are in stacks you choose, then choose one of the following options\.
     + **All resources** – All resources that are in stacks in your account are analyzed\. Resources in each stack are grouped into their own application\. Any resources in your account that are not in a stack are not analyzed\.
     + **Select stacks** – Select the stacks that you want DevOps Guru to analyze\. The resources in each stack you select are grouped into their own application\. You can enter the name of a stack in **Find stacks** to quickly locate a specific stack\. You can select up to 1,000 stacks\.

     For more information, see [Use AWS CloudFormation stacks to identify resources in your DevOps Guru applications](working-with-cfn-stacks.md)\.
   + Choose **Tags** if you want DevOps Guru to analyze all resources that contain the tags you choose\. Choose a *key*, then choose one of the following options\. 
     + **All resources with this tag key** – All resources with tags that have this *key* are analyzed and grouped into an application, regardless of the tag's *value*\.
     + **Choose specific tag values** – All resources that contain a tag with the *key* you chose and one of the *values* you select are analyzed\. DevOps Guru groups your resources into applications by your tag's *values*\.

     The tag's *key* must begin with the prefix `devops-guru-`\. This prefix isn't case\-sensitive\. For example, a valid *key* is `DevOps-Guru-Production-Applications`\. For more information, see [Use tags to identify resources in your DevOps Guru applications](working-with-resource-tags.md)\.
   +  Choose **None** if you do not want DevOps Guru to analyze any resources\. This option disables DevOps Guru so that you stop incurring charges from resource analyzation\.

1. Choose **Save**\. 