--------

Amazon DevOps Guru is in preview and available in the following AWS Regions: US West \(Oregon\), US East \(N\. Virginia\), US East \(Ohio\), Europe \(Ireland\), and Asia Pacific \(Tokyo\)\.

The preview is open to all AWS accounts\. You do not need to request access\. Features might be added or changed before General Availability is announced\. Contact us at [amazon\-devops\-guru\-feedback@amazon\.com](mailto:amazon-devops-guru-feedback@amazon.com) with feedback\.

--------

# Resilience in Amazon DevOps Guru<a name="disaster-recovery-resiliency"></a>

The AWS global infrastructure is built around AWS Regions and Availability Zones\. AWS Regions provide multiple physically separated and isolated Availability Zones, which are connected with low\-latency, high\-throughput, and highly redundant networking\. DevOps Guru operates in multiple Availability Zones and stores artifact data and metadata in Amazon S3 and Amazon DynamoDB\. Your encrypted data is redundantly stored across multiple facilities and multiple devices in each facility, making it highly available and highly durable\.

For more information about AWS Regions and Availability Zones, see [AWS Global Infrastructure](https://aws.amazon.com/about-aws/global-infrastructure/)\.