# Use tags to identify resources in your DevOps Guru applications<a name="working-with-resource-tags"></a>

You can use tags to identify the AWS resources that Amazon DevOps Guru analyzes\. You use a tag's *key* to identify the resources, then use *values* with that *key* to group resources into your applications\. For example, you can tag your resources with the *key* `devops-guru-applications`, then use that *key* with a different *value* for each of your applications\. You might use the tag *key*\-*value* pairs `devops-guru-applications/database`, `devops-guru-applications/cicd`, and `devops-guru-applications/monitoring` to identify three applications in your account\. Each application is made up of related resources that contain the same tag *key*\-*value* pair\. You add tags to your resources using the AWS service to which they belong\. For more information, see [Add AWS tags to AWS resources](#add-tags-to-aws-resources)\.

After you add a tag to the resources in your application, you can filter your insights by the tags on resources that generated them\. For more information about how to filter your insights using a tag, see [View DevOps Guru insights](working-with-insights.md#view-insights)\.

For more information about the supported services and resources, see [Amazon DevOps Guru pricing](http://aws.amazon.com/devops-guru/pricing/)\.

**Topics**
+ [What is an AWS tag?](#what-is-a-tag)
+ [Define a DevOps Guru application using a tag](#define-a-devops-guru-application-using-a-tag)
+ [Choose tags to identify resources for DevOps Guru to analyze](#choose-tags)
+ [Add AWS tags to AWS resources](#add-tags-to-aws-resources)

## What is an AWS tag?<a name="what-is-a-tag"></a>

Tags help you identify and organize your AWS resources\. Many AWS services support tagging, so you can assign the same tag to resources from different services to indicate that the resources are related\. For example, you can assign the same tag to an Amazon DynamoDB table resource that you assign to an AWS Lambda function\. For more information about using tags, see the [Tagging best practices](https://d1.awsstatic.com/whitepapers/aws-tagging-best-practices.pdf) whitepaper\. 

Each AWS tag has two parts\. 
+ A tag *key* \(for example, `CostCenter`, `Environment`, `Project`, or `Secret`\)\. Tag *keys* are case\-sensitive\.
+ An optional field known as a tag *value* \(for example, `111122223333`, `Production`, or a team name\)\. Omitting the tag *value* is the same as using an empty string\. Like tag *keys*, tag *values* are case\-sensitive\.

Together these are known as *key*\-*value* pairs\. 

## Define a DevOps Guru application using a tag<a name="define-a-devops-guru-application-using-a-tag"></a>

To define your Amazon DevOps Guru application using a tag, add that tag to the AWS resources in your account that make up your application\. Your tag contains a *key* and a *value*\. We recommend that you add a tag to each of your AWS resources analyzed by DevOps Guru that has the same *key*\. Use a different *value* in the tag to group resources into your applications\. For example, you might assign tags with the *key* `devops-guru-analysis-boundary` to all the AWS resources in your coverage boundary\. Use different *values* with that *key* to identify applications in your account\. You might use the *values* `containers`, `database`, and `monitoring` for three applications\. For more information, see [Update your AWS analysis coverage in DevOps Guru](update-settings.md#update-coverage)\.

If you use AWS tags to specify which resources to analyze, you can use tags with only one *key*\. You can pair your tags' *key* paired with any *value*\. Use the *value* to group the resources that contain your *key* into your operational applications\.

**Important**  
The string used for a *key* in a tag that you use to define your resource coverage must begin with the prefix `Devops-guru-`\. For example, the tag *key* might be `Devops-guru-deployment-application` or `Devops-guru-rds-application`\. While *keys* are case\-sensitive, the case of *key* characters don't matter to DevOps Guru\. For example, DevOps Guru works with a *key* named `devops-guru-rds` and a *key* named `DevOps-Guru-RDS`\. Possible *key*\-*value* pairs in your application might be `Devops-Guru-production-application/RDS` or `Devops-Guru-production-application/containers`\.

## Choose tags to identify resources for DevOps Guru to analyze<a name="choose-tags"></a>

Specify the AWS tags that identify the AWS resources that you want Amazon DevOps Guru to analyze\. These resources are your resource coverage boundary\. You can choose one *key* and zero or more *values*\.

**To choose your tags**

1. Open the Amazon DevOps Guru console at [https://console\.aws\.amazon\.com/devops\-guru/](https://console.aws.amazon.com/devops-guru/)\.

1. Open the navigation pane, then expand **Settings**\. 

1. In **Analyzed resources**, choose **Edit**\. 

1. Choose **Tags** if you want DevOps Guru to analyze all resources that contain the tags you choose\. Choose a *key*, then choose one of the following options\. 
   + **All resources with this tag key** – All resources with tags that have this *key* are analyzed and grouped into an application, regardless of the tag's *value*\.
   + **Choose specific tag values** – All resources that contain a tag with the *key* you chose and one of the *values* you select are analyzed\. DevOps Guru groups your resources into applications by your tag's *values*\.

   The tag's *key* must begin with the prefix `devops-guru-`\. This prefix isn't case\-sensitive\. For example, a valid *key* is `DevOps-Guru-Production-Applications`\. For more information, see [Use tags to identify resources in your DevOps Guru applications](#working-with-resource-tags)\.

1. Choose **Save**\. 

## Add AWS tags to AWS resources<a name="add-tags-to-aws-resources"></a>

You can add tags to your resources using the AWS service to which each resource belongs, or using the AWS Tag Editor\.
+ To manage tags using your resources' service, use the console, AWS Command Line Interface, or SDK of the service to which a resource belongs\. For example, you can tag an Amazon Kinesis stream resource or an Amazon CloudFront distribution resource\. These are two examples of services with resources that can be tagged\. Most resources that DevOps Guru can analyze support tags\. For more information, see [Tagging your streams](https://docs.aws.amazon.com/streams/latest/dev/tagging.html) in the *Amazon Kinesis Developer Guide* and [Tagging a distribution](https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/tagging.html) in the *Amazon CloudFront Developer Guide*\. To learn how to add tags to other types of resources, see the user guide or developer guide for the AWS service to which they belong\.
+ You can use the AWS Tag Editor to manage tags by resources in your Region and by resources in specific AWS services\. For more information, see [Tag editor](https://docs.aws.amazon.com/ARG/latest/userguide/tag-editor.html) in the *AWS Resource Group and Tags User Guide*\.

When you add a tag to a resource, you can add the *key* only, or the *key* and a *value*\. For example, you can create a tag with the *key* `DevOps` for all the resources that are part of your DevOps application\. You can also add a tag with the *key* `DevOps` and the *value* `RDS`, then add that *key*\-*value* pair to only the Amazon RDS resources in your application\. This is useful if you want to view insights in the console that are generated from only the Amazon RDS resources in your application\.