# Working with insights in DevOps Guru<a name="working-with-insights"></a>

Amazon DevOps Guru generates an *insight* when it detects anomalous behavior in your operational applications\. DevOps Guru analyzes the metrics, events, and more in the AWS resources you specified when you set up DevOps Guru\. Each insight contains one or more recommendations for you to take to mitigate the issue\. It also contains a list of the metrics and a list of the events that were used to identify the unusual behavior\. 

There are two insight types\.
+ *Reactive* insights have recommendations you can take to address issues that are happening now\. 
+ *Proactive* insights have recommendations that address issues that DevOps Guru predicts will occur in the future\. 

**Topics**
+ [View DevOps Guru insights](#view-insights)
+ [Understanding insights in the DevOps Guru console](#understanding-insights-console)
+ [Understanding how anomalous behaviors are grouped into insights](#how-insights-are-grouped)
+ [Understanding insight severities](#understanding-insights-severities)

## View DevOps Guru insights<a name="view-insights"></a>

 You can view your insights using the AWS Management Console\. 

**View your DevOps Guru insights**

1. Open the Amazon DevOps Guru console at [https://console\.aws\.amazon\.com/devops\-guru/](https://console.aws.amazon.com/devops-guru/)\.

1. Open the navigation pane, then choose **Insights**\. 

1. On the **Reactive** tab, you can see a list of reactive insights\. On the **Proactive** tab, you can see a list of proactive insights\. 

1. \(Optional\) Use one or more of the following filters to find the insights you are looking for\. 
   + Choose the **Reactive** or **Proactive** tab, depending on the type of insight for which you are looking\. 
   + Choose **Filter insights by status, severity, or resource name**, then choose the **Status**, **Severity**, or **Resource name** option to specify a filter\. You can add a status, severity, and resource filter\.
   + Choose or specify a time range to filter by insight creation time\.
     +  **12h** shows insights created in the past 12 hours\.
     +  **1d** shows insights created in the past day\.
     +  **1w** shows insights created in the past week\.
     +  **1m** shows insights created in the past month\.
     +  **Custom** lets you specify another time range\. The maximum time range you can use to filter insights is 180 days\. 

1. To view details about an insight, choose its name\. 

## Understanding insights in the DevOps Guru console<a name="understanding-insights-console"></a>

Use the Amazon DevOps Guru console to view useful information in your insights to help you diagnose and address anomalous behavior\. When DevOps Guru analyzes your resources and finds related Amazon CloudWatch metrics, AWS CloudTrail events, and operational data that indicate unusual behavior, it creates an insight that contains recommendations to address the issue and information about the related metrics and events\. Use insight data with [Best practices in DevOps Guru](best-practices.md) to address operational problems detected by DevOps Guru\. 

To view an insight, follow the steps in [View insights](#view-insights) to find one, then choose its name\. The insight page contains the following details\. <a name="insight-details-page-items"></a>

Insight overview  
Use this section to get a high\-level overview of the insight\. You can see the status of the insight \(*Ongoing* or *Closed*\), how many AWS CloudFormation stacks are affected, when the insight started, ended, and was last updated, and the related operations item if there is one\.   
If an insight is grouped at the *stack level*, then you can choose the number of affected stacks to see their names\. The anomalous behavior that created the insight occurred in resources created by the affected stacks\. If an insight is grouped at the *account level*, then the number is zero or does not appear\.  
For more information, see [Understanding how anomalous behaviors are grouped into insights](#how-insights-are-grouped)\.

Insight name  <a name="how-insight-is-named"></a>
The name of an insight depends on whether it is grouped at the *stack level* or the *account level*\.   
+ *Stack level* insight names include the name of the stack that contains the resource with its anomalous behavior\.
+ *Account level* insight names do not include a stack name\.
For more information, see [Understanding how anomalous behaviors are grouped into insights](#how-insights-are-grouped)\.

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

## Understanding how anomalous behaviors are grouped into insights<a name="how-insights-are-grouped"></a>

An insight is grouped at the *stack level* or the *account level*\. If an insight is generated for a resource that is in an AWS CloudFormation stack, then it is a *stack level* insight\. Otherwise, it is an *account level* insight\.

How a stack is grouped can depend on how you configured your resource analysis coverage in Amazon DevOps Guru\.<a name="insight-grouping-by-resource-coverage"></a>

**If your coverage is defined by AWS CloudFormation stacks**  
All resources contained in the stacks you choose are analyzed, and all detected insights are grouped at the *stack level*\.

**If your coverage is your current AWS account and Region**  
All resources in your account and Region are analyzed, and there are three possible grouping scenarios for detected insights\.  
+ An insight generated from a resource that is not part of a stack is grouped at the *account level*\.
+ An insight generated from a resource that is in one of the first 10,000 analyzed stacks is grouped at the *stack level*\.
+ An insight generated from a resource that is not in one of the first 10,000 analyzed stacks is grouped at the *account level*\. For example, an insight generated for a resource in the 10,001st analyzed stack is grouped at the *account level*

For more information, see [Determine coverage for DevOps Guru](setting-up.md#setting-up-determine-coverage)\.

## Understanding insight severities<a name="understanding-insights-severities"></a>

An insight can have one of three severities, *high*, *medium*, or *low*\. An insight is created by Amazon DevOps Guru after it detects related anomalies and assigns each anomaly a severity\. DevOps Guru assigns an anomaly a severity of *high*, *medium*, or *low* using domain knowledge and years of collective experience\. An insight's severity is determined by the most severe anomaly that contributed to creating the insight\. 
+ If the severity of all the anomalies that generated the insight is *low*, then the insight's severity is *low*\.
+ If the highest severity of all the anomalies that generated the insight is *medium*, then the insight's severity is *medium*\. The severity of some of the anomalies that generated the insight might be *low*\.
+ If the highest severity of all the anomalies that generated the insight is *high*, then the insight's severity is *high*\. The severity of some of the anomalies that generated the insight might be *low* or *medium*\.