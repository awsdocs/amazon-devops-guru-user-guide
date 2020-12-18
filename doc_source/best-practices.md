--------

Amazon DevOps Guru is in preview and available in the following AWS Regions: US West \(Oregon\), US East \(N\. Virginia\), US East \(Ohio\), Europe \(Ireland\), and Asia Pacific \(Tokyo\)\.

The preview is open to all AWS accounts\. You do not need to request access\. Features might be added or changed before General Availability is announced\. Contact us at [amazon\-devops\-guru\-feedback@amazon\.com](mailto:amazon-devops-guru-feedback@amazon.com) with feedback\.

--------

# Best practices in DevOps Guru<a name="best-practices"></a>

The following are some best practices to help you understand, diagnose, and fix anomalous behavior detected by Amazon DevOps Guru\. Use best practices with [Understanding insights in the DevOps Guru console](understanding-insights-console.md) to address operational problems detected by DevOps Guru\.
+ In an insight's timeline view, look at the highlighted metrics first\. They are often key indicators of the problem\. 
+ Use Amazon CloudWatch to view metrics that occurred immediately before the first highlighted metric in an insight\. This can help you pinpoint when and how behavior changed to help you diagnose and fix the problem\. 
+ Multiple dimensions of the same metric can often be anomalous\. Look at the dimensions in the graphed view to get a deeper understanding of the problem\. 
+ Look in the events section of an insight for deployment or infrastructure events that happened around the time the insight was created\. Knowing which events occurred when an insight's anomalous behavior occurred can help you understand and diagnose the problem\. 
+ Look for tickets in your operational system that happened around the same time as an insight for clues\. 
+ In an insight, read the recommendations and visit the links in recommendations\. These often have troubleshooting steps that can help you diagnose and solve problems quickly\. 
+ Don't ignore resolved insights unless you have already solved the problem\. Once a day, look at new insights, even if they have been resolved\. Try to understand the root cause behind as many of the insights as you can\. Look for a pattern that might be the sign of a systemic problem\. If a systemic problem is left unresolved, it could cause more serious problems in the future\. Fixing transient issues now can help prevent future, more serious, incidents\. 