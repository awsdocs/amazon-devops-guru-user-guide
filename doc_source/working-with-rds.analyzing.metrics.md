# Viewing anomalies for RDS resources<a name="working-with-rds.analyzing.metrics"></a>

Within an insight, find the anomalies for Amazon RDS resources\.

**To view RDS anomalies**

1. Look for aggregated metrics that show the resource type **AWS/RDS**\. 

   If only one resource is experiencing the anomaly, the resource name is shown\. If multiple resources have the anomaly, DevOps Guru for RDS lists the number\.

1. If multiple resources are affected, choose the text\.

   DevOps Guru for RDS lists each affected resource and its DB load\.

1. \(Optional\) Choose the timeline next to the **AWS/RDS** metric\.

   A message shows the service name, resource names, stack, and duration\. For example, it might show the issue as **64 AAS \(3x spike\) DB load**\. 

   To jump to the details, choose **View analysis**\. The detailed analysis is only available for Amazon Aurora DB instances that have Performance Insights turned on\.