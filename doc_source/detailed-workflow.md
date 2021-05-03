# Detailed DevOps Guru workflow<a name="detailed-workflow"></a>

 The DevOps Guru workflow integrates with several AWS services, including Amazon CloudWatch, AWS CloudTrail, Amazon Simple Notification Service, and AWS Systems Manager\. The following diagram shows a detailed workflow that includes how it works with other AWS services\. 

![\[Image NOT FOUND\]](http://docs.aws.amazon.com/devops-guru/latest/userguide/)![\[Image NOT FOUND\]](http://docs.aws.amazon.com/devops-guru/latest/userguide/)

This diagram shows a scenario in which DevOps Guru coverage is specified by the AWS resources that are defined in AWS CloudFormation stacks\. If no stacks are chosen, then DevOps Guru coverage analyzes all AWS resources in your account\. 

1. During setup, you specify one or two Amazon SNS topics that are used to notify you about important DevOps Guru events, such as when an insight is created\. Next, you can specify AWS CloudFormation stacks that define the resources you want analyzed\. You can also enable Systems Manager to generate an OpsItem for each insight to help you manage your insights\. 

1. After DevOps Guru is configured, it starts analyzing CloudWatch metrics and events that are emitted from your resources and AWS CloudTrail data related to the CloudWatch metrics\. If your operations include CodeDeploy deployments, DevOps Guru also analyzes deployment events\. 

   DevOps Guru creates insights when it identifies unusual, anomalous behavior in the analyzed data\. Each insight contains one or more recommendations, a list of the metrics used to generate the insight, and a list of the events used to generate the insight\. Use this information to address the identified problem\. 

1. After each insight is created, DevOps Guru sends a notification using the Amazon SNS topic or topics specified during DevOps Guru set up\. If you enabled DevOps Guru to generate an OpsItem in Systems Manager OpsCenter, then each insight also triggers a new Systems Manager OpsItem\. You can use Systems Manager to manage your insight OpsItems\. 