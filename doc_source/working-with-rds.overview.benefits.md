# Benefits of DevOps Guru for RDS<a name="working-with-rds.overview.benefits"></a>

If you're responsible for an Amazon Aurora database, you might not know that an event or regression that is affecting that database is occurring\. When you learn about the issue, you might not know why it's occurring or what to do about it\. Rather than turning to a database administrator \(DBA\) for help or relying on third\-party tools, you can follow recommendations from DevOps Guru for RDS\. 

You gain the following advantages from the detailed analysis of DevOps Guru for RDS:

**Fast diagnosis**  
DevOps Guru for RDS continuously monitors and analyzes database telemetry\. Performance Insights, Enhanced Monitoring, and Amazon CloudWatch collect telemetry data for your database cluster\. DevOps Guru for RDS uses statistical and machine learning techniques to mine this data and detect anomalies\. To learn more about telemetry data, see [Monitoring DB load with Performance Insights on Amazon Aurora](https://docs.aws.amazon.com/AmazonRDS/latest/AuroraUserGuide/USER_PerfInsights.html) and [Monitoring the OS by using Enhanced Monitoring](https://docs.aws.amazon.com/AmazonRDS/latest/AuroraUserGuide/USER_Monitoring.OS.html) in the *Amazon Aurora User Guide*\.

**Fast resolution**  
Each anomaly identifies the performance issue and suggests avenues of investigation or corrective actions\. For example, DevOps Guru for RDS might recommend that you investigate specific wait events\. Or it might recommend that you tune your application pool settings to limit the number of database connections\. Based on these recommendations, you can resolve performance issues more quickly than by troubleshooting manually\.

**Deep knowledge of Amazon engineers**  
To detect performance issues and help you resolve bottlenecks, DevOps Guru for RDS relies on machine learning \(ML\)\. Amazon database engineers contributed to the development of the DevOps Guru for RDS findings, which encapsulate many years of managing hundreds of thousands of databases\. By drawing on this collective knowledge, DevOps Guru for RDS can teach you best practices\.