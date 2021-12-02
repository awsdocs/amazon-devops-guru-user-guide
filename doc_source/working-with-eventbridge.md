# Working with Amazon EventBridge<a name="working-with-eventbridge"></a>

Amazon DevOps Guru integrates with Amazon EventBridge to notify you of certain events relating to insights and corresponding insight updates\. Events from AWS services are delivered to EventBridge in near real time\. You can write simple rules to indicate which events are of interest to you and what automated actions to take when an event matches a rule\. The actions that can be automatically initiated include the following examples:
+ Invoking an AWS Lambda function
+ Invoking an Amazon Elastic Compute Cloud run command
+ Relaying the event to Amazon Kinesis Data Streams
+ Activating a Step Functions state machine
+ Notifying an Amazon SNS or an Amazon SQS

You can select any of the following predefined patterns to filter events or create a custom pattern rule to initiate actions in a supported AWS resources\.
+ DevOps Guru New Insight Open
+ DevOps Guru New Anomaly Association
+ DevOps Guru Insight Severity Upgraded
+ DevOps Guru New Recommendation Created
+ DevOps Guru Insight Closed

## Events for DevOps Guru<a name="eventbridge-examples"></a>

The following are example events from DevOps Guru\. Events are emitted on a best\-effort basis\. To learn more about event patterns, see [Getting started with Amazon EventBridge](https://docs.aws.amazon.com/eventbridge/latest/userguide/eb-get-started.html) or [Amazon EventBridge event patterns](https://docs.aws.amazon.com/eventbridge/latest/userguide/eb-event-patterns.html)\.

### DevOps Guru New Insight Open Event<a name="w174aac29c11b5"></a>

When DevOps Guru opens a new insight, it sends the following event\.

```
{    
    "version" : "0",
    "id" : "08108845-ef90-00b8-1ad6-2ee5570ac6c4",
    "detail-type" : "DevOps Guru New Insight Open",
    "source" : "aws.devops-guru",
    "account" : "123456789012",
    "time" : "2021-11-01T17:06:10Z",
    "region" : "us-east-1",
    "resources" : [ ],
    "detail" : {
      "insightSeverity" : "high",
      "insightDescription" : "ApiGateway 5XXError Anomalous In Stack TestStack",
      "insightType" : "REACTIVE",
      "anomalies" : [
        {
          "startTime" : "1635786000000",
          "id" : "AL41JDFFQPYlZlXD8cpREkAAAAF83HGGgC9TmTr9lbfJ7sCiISlWMeFCbHY_XXXX",
          "sourceDetails" : [
            {
              "dataSource" : "CW_METRICS",
              "dataIdentifiers" : {
                "period" : "60",
                "stat" : "Average",
                "unit" : "None",
                "name" : "5XXError",
                "namespace" : "AWS/ApiGateway",
                "dimensions" : [
                  {
                    "name" : "ApiName",
                    "value" : "Test API Service"
                  },
                  {
                    "name" : "Stage",
                    "value" : "prod"
                  }
                ]
              }
            }
          ]
        }
      ],
      "accountId" : "123456789012",
      "messageType" : "NEW_INSIGHT",
      "insightUrl" : "https://us-east-1.console.aws.amazon.com/devops-guru/#/insight/reactive/AIYH6JxdbgkcG0xJmypiL4MAAAAAAAAAL0SLEjkxiNProXWcsTJbLU07EZ7XXXX",
      "startTime" : "1635786120000",
      "insightId" : "AIYH6JxdbgkcG0xJmypiL4MAAAAAAAAAL0SLEjkxiNProXWcsTJbLU07EZ7XXXX",
      "region" : "us-east-1"
    }
  },
```

### Custom sample event pattern for high severity new Insight<a name="w174aac29c11b7"></a>

Rules use event patterns to select events and route them to targets\. The following is a sample DevOps Guru event pattern\.

```
{
  "source": [
    "aws.devops-guru"
  ],
  "detail-type": [
    "DevOps Guru New Insight Open"
  ],
  "detail": {
    "insightSeverity": [
         "high"
         ]
  }
}
```