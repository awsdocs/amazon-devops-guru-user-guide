# Enable AWS services for DevOps Guru analysis<a name="enable-services-for-devops-guru"></a>

Amazon DevOps Guru can analyze the performance of any AWS resource that it supports\. When it finds anomalous behavior, it generates an insight with details about the behavior and how to address it\. For more information about the supported services and resources, see [Amazon DevOps Guru pricing](http://aws.amazon.com/devops-guru/pricing/)\.

DevOps Guru uses Amazon CloudWatch metrics, AWS CloudTrail events, and more to help analyze resources\. Most of the resources it supports generate the metrics required for DevOps Guru analysis automatically\. However, a few AWS services require extra action to generate the required metrics\. For some services, enabling these metrics provides additional analysis to existing DevOps Guru coverage\. For others, analysis is not possible until you enable these metrics\. For more information, see [Determine coverage for DevOps Guru](setting-up.md#setting-up-determine-coverage) and [Update your AWS analysis coverage in DevOps Guru](update-settings.md#update-coverage)\.

**Services that require action for DevOps Guru analysis**
+ Amazon Elastic Container Service – To generate additional metrics that improve DevOps Guru coverage of its resources, follow the steps in [Setting up container insights on Amazon ECS](https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/deploy-container-insights-ECS.html)\. Doing this might incur Amazon CloudWatch charges\. 
+ Amazon Elastic Kubernetes Service – To generate metrics for DevOps Guru to analyze, follow the steps in [Setting up container insights on Amazon EKS and Kubernetes](https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/deploy-container-insights-EKS.html)\. DevOps Guru doesn't analyze any Amazon EKS resources until generation of these metrics is set up\. Doing this might incur Amazon CloudWatch charges\.

For more information, see [Amazon CloudWatch pricing](http://aws.amazon.com/cloudwatch/pricing/)\.