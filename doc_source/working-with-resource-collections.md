# Define applications Using AWS resources<a name="working-with-resource-collections"></a>

Amazon DevOps Guru groups the resources that are in the coverage boundary that specifies which resources it analyzes for operational insights\. The resources are grouped by resources in AWS CloudFormation stacks or by resources with tags\. You choose the stacks or tags when you set up DevOps Guru\. You can also update the stacks or tags later\. We recommend that you think of your resource groups as applications\. For example, you might have all resources that you use for a monitoring application defined in one stack\. Or you might add the same tag to all the resources that you use in a database application\. the boundary that defines which resources DevOps Guru analyzes\. All the resources in the collection are inside this boundary\. Any resources in your account that are not in your resource collection are outside the boundary and are not analyzed\. For more information about the supported services and resources, see [Amazon DevOps Guru pricing](http://aws.amazon.com/devops-guru/pricing/)\.

You can define your coverage boundary that contains the resources in your applications three ways\.
+ Specify that all supported AWS resources in your AWS account and Region\. This makes your account and Region your resource boundary\. With this option, DevOps Guru analyzes every supported resource in your account and Region\. All resources that are in one stack are grouped into an application\. Any resources that are not in a stack are grouped into their own application\.
+ Use AWS CloudFormation stacks to specify the resources in your applications\. A stack contains resources that are generated using AWS CloudFormation\. In DevOps Guru, you choose stacks in your account\. The resources you in each stack you choose are grouped into an application\. All resources in the stacks are analyzed by DevOps Guru for insights\.
+  Use AWS tags to specify the resources in your applications\. An AWS tag contains a *key* and a *value*\. In DevOps Guru, choose one tag *key* and optionally choose one or more *values* that are paired with that *key*\. You can use the *values* to group your resources into applications\.

For more information, see [Update your AWS analysis coverage in DevOps Guru](update-settings.md#update-coverage)\.

**Topics**
+ [Use tags to identify resources in your DevOps Guru applications](working-with-resource-tags.md)
+ [Use AWS CloudFormation stacks to identify resources in your DevOps Guru applications](working-with-cfn-stacks.md)