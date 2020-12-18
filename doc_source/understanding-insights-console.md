--------

Amazon DevOps Guru is in preview and available in the following AWS Regions: US West \(Oregon\), US East \(N\. Virginia\), US East \(Ohio\), Europe \(Ireland\), and Asia Pacific \(Tokyo\)\.

The preview is open to all AWS accounts\. You do not need to request access\. Features might be added or changed before General Availability is announced\. Contact us at [amazon\-devops\-guru\-feedback@amazon\.com](mailto:amazon-devops-guru-feedback@amazon.com) with feedback\.

--------

# Understanding insights in the DevOps Guru console<a name="understanding-insights-console"></a>

Use the Amazon DevOps Guru console to view useful information in your insights to help you diagnose and address anomalous behavior\. When DevOps Guru analyzes your resources and finds related Amazon CloudWatch metrics, AWS CloudTrail events, and operational data that indicate unusual behavior, it creates an insight that contains recommendations to address the issue and information about the related metrics and events\. Use insight data with [Best practices in DevOps Guru](best-practices.md) to address operational problems detected by DevOps Guru\. 

To view an insight, follow the steps in [View insights](view-insights.md) to find one, then choose its name\. The insight page contains the following details\. <a name="insight-details-page-items"></a>

Insight overview  
Use this section to get a high\-level overview of the insight\. You can see the status of the insight \(*Active* or *Resolved*\),; how many AWS CloudFormation stacks are affected; when the insight started, ended, and was last updated; and the related operations item if there is one\.   
Choose the number of affected stacks to see their names\. The anomalous behavior that created the insight occurred in resources created by the affected stacks\. 

Aggregated metrics  
Choose the **Aggregated metrics** tab to view metrics that are related to the insight\. In the table, each row represents one metric\. You can see which AWS CloudFormation stack created the resource that emitted the metric, the name of the resource, and its type\. Not all metrics are associated with an AWS CloudFormation stack or have a name\.  
When there are multiple resources anomalous at the same time, the timeline view aggregates the resources and presents their anomalous metrics in a single timeline for easy analysis\. The red lines on a timeline indicate spans of time when a metric emitted unusual values\. To zoom in, use your mouse to choose a specific time range\. You can also use the magnifying glass icons to zoom in and out\.   
Choose a red line in the timeline to view detailed information\. In the window that opens, you can:   
+ Choose **View in CloudWatch** to see how the metric looks in the CloudWatch console\. For more information, see [Statistics](https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/cloudwatch_concepts.html#Statistic) and [Dimensions](https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/cloudwatch_concepts.html#Dimension) in the *Amazon CloudWatch User Guide*\. 
+ Hover over the graph to view details about the anomalous metric data and when it occurred\. 
+ Choose the box with the downward arrow to download a PNG image of the graph\. 

Graphed anomalies  
Choose the **Graphed anomalies** tab to view detailed graphs for each of the insight's anomalies\. One tile appears for each anomaly with details about unusual behavior detected in related metrics\. You can investigate and look at an anomaly at the resource level and per statistic\. The graphs are grouped by metric name\. In each tile, you can choose a specific time range in the timeline to zoom\. You can also use the magnifying glass icons to zoom in and out, or choose a predefined duration in hours, days, or weeks \(**1H**, **3H**, **12H**, **1D**, **3D**, **1W**, or **2W**\)\.   
Choose **View all statistics and dimensions** to see details about the anomaly\. In the window that opens, you can:   
+ Choose **View in CloudWatch** to see how the metric looks in the CloudWatch console\. 
+ Hover over the graph to view details about the anomalous metric data and when it occurred\. 
+ Choose **Statistics** or **Dimension** to customize the graph's display\. For more information, see [Statistics](https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/cloudwatch_concepts.html#Statistic) and [Dimensions](https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/cloudwatch_concepts.html#Dimension) in the *Amazon CloudWatch User Guide*\. 

Related events  
In **Related events**, view AWS CloudTrail events that are related to your insight\. Use these events to help understand, diagnose, and address the underlying cause of the anomalous behavior\. 

Recommendations  
In **Recommendations**, you can view suggestions that might help you resolve the underlying problem\. When DevOps Guru detects anomalous behavior, it attempts to create recommendations\. An insight might contain one, multiple, or zero recommendations\. 