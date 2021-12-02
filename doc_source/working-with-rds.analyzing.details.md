# Viewing the detailed analysis of an RDS anomaly<a name="working-with-rds.analyzing.details"></a>

In this stage, drill down in the anomaly to get the detailed analysis and recommendations for your Amazon Aurora DB instances\. 

The detailed analysis is only available for Amazon Aurora DB instances that have Performance Insights turned on\.

**To drill down to the anomaly details page**

1. On the insight page, find an aggregated metric with the resource type **AWS/RDS**\.

1. Choose **View analysis**\.

   The anomaly details page appears\. The title begins with **Database performance anomaly** and names the resource show\. The console defaults to the anomaly with the highest severity, regardless of when the anomaly occurred\.

1. \(Optional\) If multiple resources are affected, choose a different resource from the list at the top of the page\.

Following, you can find descriptions for the components of the details page\.

## Resource overview<a name="working-with-rds.analyzing.details.overview"></a>

The top section of the details page is **Resource overview**\. This section summarizes the performance anomaly experienced by your Amazon Aurora DB instance\.

![\[The overview of the anomaly details page\]](http://docs.aws.amazon.com/devops-guru/latest/userguide/images/rds-insight-overview.png)

This section has the following fields:
+ **Resource name** – The name of the DB instance that is experiencing the anomaly\. In this example, the resource is named **prod\_db\_678**\.
+ **DB engine** – The name of the DB instance that experiencing the anomaly\. In this example, the engine is **Aurora MySQL**\.
+ **Anomaly severity** – The measure of the negative impact of the anomaly on your instance\. Possible severities are **High**, **Medium**, and **Low**\.
+ **Anomaly summary** – A brief summary of the issue\. A typical summary is **Unusually high DB load**\.
+ **Start time** and **End time** – The time when the anomaly began and ended\. If the end time is **Ongoing**, the anomaly is still occurring\.
+ **Duration** – The duration of the anomalous behavior\. In this example, the anomaly is ongoing and has been occurring for 3 hours and 2 minutes\.

## Primary metric<a name="working-with-rds.analyzing.details.what-we-found"></a>

The **Primary metric** section summarizes the casual anomaly, which is the top\-level anomaly within the insight\. You can think of the causal anomaly as the general problem experienced by your DB instance\.

![\[The What we found section of the anomaly details page\]](http://docs.aws.amazon.com/devops-guru/latest/userguide/images/rds-primary-metric.png)

The left panel provides more details about the issue\. In this example, the summary includes the following information:
+ **Database load \(DB load\)** – A categorization of the anomaly as a database load issue\. The corresponding metric in Performance Insights is `DBLoad`\. This metric is also published to Amazon CloudWatch\.
+ **db\.r5\.4xlarge** – The DB instance class\. The number of vCPUs, which is 16 in this example, corresponds to the dotted line in the **Average active sessions \(AAS\)** chart\.
+ **24 \(6x spike\)** – The DB load, measured in average active sessions \(AAS\) during the time interval reported in the insight\. Thus, at any given time during the period of the anomaly, an average of 24 sessions were active on the database\. The DB load is 6 times the normal DB load for this instance\.
+ **Typically: DB load up to 4** – The baseline of DB load, measured in AAS, during a typical workload\. The value 4 means that, during normal operations, an average of 4 or fewer sessions are active on the database at any given time\.

By default, the load chart is sliced by wait events\. This means that for each bar in the chart, the largest colored area represents the wait event that is contributing most to total DB load\. The chart shows the time \(in red\) when the issue began\. Focus your attention on the wait events that take up the most space in the bar:
+ `CPU`
+ `IO:wait/io/sql/table/handler`

The preceding wait events appear more than normal for this Aurora MySQL database\. To learn how to tune performance using wait events, see [Tuning with wait events for Aurora MySQL](https://docs.aws.amazon.com/AmazonRDS/latest/AuroraUserGuide/AuroraMySQL.Managing.Tuning.html) and [Tuning with wait events for Aurora PostgreSQL](https://docs.aws.amazon.com/AmazonRDS/latest/AuroraUserGuide/AuroraPostgreSQL.Tuning.html) in the *Amazon Aurora User Guide*\.

## Related metrics<a name="working-with-rds.analyzing.details.relevant-metrics"></a>

The **Related metrics** section lists the contextual anomalies, which are specific findings within the causal anomaly\. These findings give additional information about the performance issue\.s

![\[The Related metrics section of the details page\]](http://docs.aws.amazon.com/devops-guru/latest/userguide/images/rds-related-metrics.png)

The **Related metrics** table has two columns: **Metrics name** and **Timeline \(UTC\)**\. Every row in the table corresponds to a specific metric\.

The first column of every row has the following pieces of information:
+ ****Name**** – The name of the metric\. The first row identifies the metric as **CPU running tasks**\.
+ **Currently** – The current value of the metric\. In the first row, the current value is **162 processes \(3x\)**\. 
+ **Normally** – The baseline of this metric for this database when it is functioning normally\. DevOps Guru for RDS calculates the baseline as the 95th percentile value over 1 week of history\. The first row indicates that 56 processes are typically running on the CPU\.
+ **Contributing to** – The finding associated with this metric\. In the first row, the **CPU running tasks** metric is associated with the **CPU capacity exceeded** anomaly\.

The **Timeline** column shows a line chart for the metric\. The shaded area shows the time interval when DevOps Guru for RDS designated the finding as high severity\.

## Analysis and recommendations<a name="working-with-rds.analyzing.details.findings"></a>

Whereas the causal anomaly describes the overall issue, a contextual anomaly describes a specific finding that requires investigation\. Each finding corresponds to a set of related metrics\.

In the following example of an **Analysis and recommendations** section, the high DB load anomaly has two findings\.

![\[The Analysis and recommendations section of the details page\]](http://docs.aws.amazon.com/devops-guru/latest/userguide/images/rds-analysis-recs.png)

The table has the following columns:
+ **Anomaly** – A general description of this contextual anomaly\. In this example, the first anomaly is high\-load wait events, and the second is CPU capacity exceeded\.
+ **Analysis** – A detailed explanation of the anomaly\.

  In the first anomaly, three wait types contribute to 90% of DB load\. In the second anomaly, the CPU run queue exceeded 150, which means that at any given time, more than 150 sessions were waiting for CPU time\. CPU utilization was over 97%, which means that for the duration of the issue, the CPU was busy 97% of the time\. Thus, the CPU was almost continually occupied while an average of 150 sessions waited to run on the CPU\.
+ **Recommendations** – The suggested user response to the anomaly\.

  In the first anomaly, DevOps Guru for RDS recommends that you investigate the wait events `cpu` and `io/table/sql/handler`\. To learn how to tune your database performance based on these events, see [cpu](https://docs.aws.amazon.com/AmazonRDS/latest/AuroraUserGuide/ams-waits.cpu.html) and [io/table/sql/handler](https://docs.aws.amazon.com/AmazonRDS/latest/AuroraUserGuide/ams-waits.waitio.html) in the *Amazon Aurora User Guide*\.

  In the second anomaly, DevOps Guru for RDS recommends that you reduce CPU consumption by tuning three SQL statements\. You can hover over the links to see the SQL text\.
+ **Related metrics** – Metrics that give you specific measurements for the anomaly\. For more information about these metrics, see [Amazon Aurora metrics](https://docs.aws.amazon.com/AmazonRDS/latest/AuroraUserGuide/Aurora.AuroraMySQL.Monitoring.Metrics.html) in the *Amazon Aurora User Guide*\.

  In the first anomaly, DevOps Guru for RDS recommends that compare DB load to the maximum CPU for your instance\. In the second anomaly, the recommendation is to look at CPU run queue, CPU utilization, and SQL execution rate\.