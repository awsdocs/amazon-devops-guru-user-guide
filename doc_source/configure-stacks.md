--------

Amazon DevOps Guru is in preview and available in the following AWS Regions: US West \(Oregon\), US East \(N\. Virginia\), US East \(Ohio\), Europe \(Ireland\), and Asia Pacific \(Tokyo\)\.

The preview is open to all AWS accounts\. You do not need to request access\. Features might be added or changed before General Availability is announced\. Contact us at [amazon\-devops\-guru\-feedback@amazon\.com](mailto:amazon-devops-guru-feedback@amazon.com) with feedback\.

--------

# Step 3: Specify AWS CloudFormation stacks for DevOps Guru resource coverage<a name="configure-stacks"></a>

If you chose to specify AWS resources later than when you enable DevOps Guru, you need to choose which AWS CloudFormation stacks in your AWS account create the resources you want analyzed\. An AWS CloudFormation stack is a collection of AWS resources that you manage as a single unit\. You can use one or more stacks to include all the resources required to run your operational applications, then specify them so that they are analyzed by DevOps Guru\. If you don't specify stacks, then DevOps Guru analyzes all the AWS resources in your account\. For more information, see [Working with stacks](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/stacks.html) in the *AWS CloudFormation User Guide*, and [Determine coverage for DevOps Guru](setting-up.md#setting-up-determine-coverage)\. and [Working with AWS CloudFormation stacks in DevOps Guru](working-with-cfn-stacks.md)

**Note**  
For a list of AWS services that can be analyzed by DevOps Guru, see [Supported AWS services in DevOps Guru](quotas.md#services-devops-guru)\. 

**Specify AWS CloudFormation stacks for DevOps Guru resource coverage**

1. Open the Amazon DevOps Guru console at [https://console\.aws\.amazon\.com/codeguru/devops\-guru/](https://console.aws.amazon.com/codeguru/devops-guru/)\. 

1. Choose **Settings** in the navigation pane\. 

1. In **DevOps Guru analysis coverage**, choose **Manage**\.

1. If you have not enabled any stacks, in **CloudFormation stacks**, choose **Manage analysis coverage**\. 

1. Select up to 200 stacks that contain the resources that you want analyzed\. You can enter the name of a stack in **Find stacks** to quickly locate a specific stack\. 

1. Choose **Save**\. 