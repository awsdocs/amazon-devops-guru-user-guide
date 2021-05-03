# Estimate Amazon DevOps Guru resource analysis costs<a name="cost-estimate"></a>

You can estimate your monthly cost for Amazon DevOps Guru to analyze your AWS resources\. You pay for the number of hours analyzed for each active AWS resource in your specified resource coverage\. A resource is active if it produces metrics, events, or logs within an hour\.

DevOps Guru scans your selected resources to create a monthly cost estimate\. You can view the resources, their hourly billable price, and their estimated monthly charge\. The cost estimator assumes as a default that the analyzed active resources are utilized 100 percent of the time\. You can change this percentage for each analyzed service based on your estimated usage to create an updated monthly cost estimate\. The estimate is for the cost to analyze your resources and does not include costs associated with DevOps Guru API calls\. 

You can create one cost estimate at a time\. The time it takes to generate a cost estimate depends on the number of resources you specify when you create the cost estimate\. When you specify a lot of resources, it can take up to four hours to complete\. Your actual costs vary and depend on the percentage of time your analyzed active resources are utilized\.

**Note**  
For a cost estimate, you can specify only one AWS CloudFormation stack\. For your actual coverage boundary, you can specify up to 500 stacks\.

**To create a monthly resource analysis cost estimate**

1. Open the Amazon DevOps Guru console at [https://console\.aws\.amazon\.com/devops\-guru/](https://console.aws.amazon.com/devops-guru/)\.

1. Choose **Cost estimator** in the navigation pane\. 

1. If you have not enabled DevOps Guru, you must create an IAM role\. In **Create IAM role for DevOps Guru**, choose **Create IAM role**\. If you have aleady enabled DevOps Guru, the role has already been created so this option does not appear\.

1. Choose the resources you want to use to create your estimate\.
   + If you want to estimate the cost for DevOps Guru to analyze the resources defined by one AWS CloudFormation stack, do the following\.

     1. Choose **CloudFormation stack**\.

     1. Enter the name of an AWS CloudFormation stack in your AWS account in **Enter CloudFormation stack name**\. For information about working with and viewing your stacks, see [Working with stacks](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/stacks.html) in the *AWS CloudFormation User Guide*\.

     1. \(Optional\) If you use an AWS CloudFormation stack that you are currently not analyzing, choose **Enable resource analysis** to enable DevOps Guru to start analyzing its resources\. This option is not available if you have not enabled DevOps Guru or if you are already analyzing the resources in the stack\.
   + If you want to estimate the cost for DevOps Guru to analyze the resource in your AWS account and Region, choose **Current AWS account**\.

1. Choose **Estimate monthly cost**\.

1. \(Optional\) In the **Active resource utilization %** column, enter an updated percentage value for one or more AWS services\. The default *active resource utilization %* is 100%\. This means that DevOps Guru generates the estimate for the AWS service by calculating the cost of one hour of analyzing its resources, then extrapolating that over 30 days for a total of 360 hours\. If a service is active less than 100% of the time, you can update the percentage based on your estimated usage for a more accurate estimate\. For example, if you update a service's active resource utilization to 75%, the one hour cost of analyzing its resources is extrapolated over \(360 x 0\.75\) hours, or 270 hours\. 

If your estimate is zero dollars, then the resources you chose likely do not include resources supported by DevOps Guru\. For more information about the supported services and resources, see [Amazon DevOps Guru pricing](http://aws.amazon.com/devops-guru/pricing/)\. 