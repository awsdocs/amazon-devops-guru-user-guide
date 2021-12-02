# Key concepts for database performance tuning<a name="working-with-rds.overview.tuning"></a>

DevOps Guru for RDS assumes that you're familiar with a few key performance concepts\. To learn more about these concepts, see [Overview of Performance Insights](https://docs.aws.amazon.com/AmazonRDS/latest/AuroraUserGuide/USER_PerfInsights.Overview.html) in the *Amazon Aurora User Guide*\.

**Topics**
+ [DB load](#working-with-rds.overview.tuning.db-load)
+ [Wait events](#working-with-rds.overview.tuning.waits)

## DB load<a name="working-with-rds.overview.tuning.db-load"></a>

The key concept for database tuning is *database load \(DB load\)*\. The DB load represents how busy your database is at any given time\. An increase in DB load means an increase in database activity\.

A *database session* represents an application's dialogue with a relational database\. An *active session* is a session that is in the process of running a database request\. A session is active when it's either running on CPU or waiting for a resource to become available so that it can proceed\. For example, an active session might wait for a page to be read into memory, and then consume CPU while it reads data from the page\.

The `DBLoad` metric in Performance Insights is measured in *average active sessions \(AAS\)*\. To calculate AAS, Performance Insights samples the number of active sessions every second\. For a specific time period, the AAS is the total number of active sessions divided by the total number of samples\. An AAS value of 2 means that, on average, 2 sessions were active in requests at any given time\.

An analogy for DB load is activity in a warehouse\. Suppose that the warehouse employs 100 workers\. If 1 order comes in, 1 worker fulfills the order while the other workers are idle\. If 100 or more orders come in, all 100 workers fulfill orders simultaneously\. If you periodically sample how many workers are active over a given time period, you can calculate the average number of active workers\. The calculation shows that, on average, *N* workers are busy fulfilling orders at any given time\. If the average was 50 workers yesterday and 75 workers today, the activity level in the warehouse increased\. In the same way, DB load increases as session activity increases\.

To learn more, see [DB load](https://docs.aws.amazon.com/AmazonRDS/latest/AuroraUserGuide/USER_PerfInsights.Overview.html) in the *Amazon Aurora User Guide*\.

## Wait events<a name="working-with-rds.overview.tuning.waits"></a>

A *wait event* is a type of database instrumentation that tells you which resource a database session is waiting for so it can proceed\. When Performance Insights counts active sessions to calculate database load, it also records the wait events that are causing the active sessions to wait\. This technique allows Performance Insights to show you which wait events are contributing to DB load\.

Every active session is either running on the CPU or waiting\. For example, sessions consume CPU when they search memory, perform a calculation, or run procedural code\. When sessions aren't consuming CPU, they might be waiting for a data file to be read or a log to be written to\. The more time that a session waits for resources, the less time it runs on the CPU\.

When you tune a database, you often try to find the resources that sessions are waiting for\. For example, two or three wait events might account for 90% of DB load\. This measure means that, on average, active sessions are spending most of their time waiting for a small number of resources\. If you can find out the cause of these waits, you can try to remedy the problem\.

Consider the analogy of a warehouse worker\. An order comes in for a book\. The worker might be delayed in fulfilling the order\. For example, a different worker might be currently restocking the shelves, or a trolley might not be available\. Or the system used to enter the order status might be slow\. The longer the worker waits, the longer the order takes to fulfill\. Waiting is a natural part of the warehouse workflow, but if wait time become excessive, productivity decreases\. In the same way, repeated or lengthy session waits can degrade database performance\.

For more information, see [Tuning with wait events for Aurora PostgreSQL](https://docs.aws.amazon.com/AmazonRDS/latest/AuroraUserGuide/AuroraPostgreSQL.Tuning.html) and [Tuning with wait events for Aurora MySQL](https://docs.aws.amazon.com/AmazonRDS/latest/AuroraUserGuide/AuroraMySQL.Managing.Tuning.html) in the *Amazon Aurora User Guide*\.