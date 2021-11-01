# Using service\-linked roles for DevOps Guru<a name="using-service-linked-roles"></a>

Amazon DevOps Guru uses AWS Identity and Access Management \(IAM\)[ service\-linked roles](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles_terms-and-concepts.html#iam-term-service-linked-role)\. A service\-linked role is a unique type of IAM role that is linked directly to DevOps Guru\. Service\-linked roles are predefined by DevOps Guru and include all the permissions that the service requires to call AWS CloudTrail, Amazon CloudWatch, AWS CodeDeploy, and AWS X\-Ray, on your behalf\. 

A service\-linked role makes setting up DevOps Guru easier because you don’t have to manually add the necessary permissions\. DevOps Guru defines the permissions of its service\-linked roles, and unless defined otherwise, only DevOps Guru can assume its roles\. The defined permissions include the trust policy and the permissions policy, and that permissions policy cannot be attached to any other IAM entity\.

You can delete a service\-linked role only after first deleting its related resources\. This protects your DevOps Guru resources because you can't inadvertently remove permission to access the resources\.

## Service\-linked role permissions for DevOps Guru<a name="slr-permissions"></a>

DevOps Guru uses the service\-linked role named `AmazonDevOpsGuruServiceRolePolicy`\. This is a managed IAM policy with scoped permissions that DevOps Guru needs to run in your account\.

The `AmazonDevOpsGuruServiceRolePolicy` service\-linked role trusts the following service to assume the role:
+ `devops-guru.amazonaws.com`

The role permissions policy allows DevOps Guru to complete the following actions on the specified resources\.

```
{
  "Version": "2012-10-17",
  "Statement": [
  {
    "Effect": "Allow",
    "Action": [
      "autoscaling:DescribeAutoScalingGroups",
      "cloudtrail:LookupEvents",
      "cloudwatch:GetMetricData",
      "cloudwatch:ListMetrics",
      "cloudwatch:DescribeAnomalyDetectors",
      "cloudwatch:DescribeAlarms",
      "cloudwatch:ListDashboards",
      "cloudwatch:GetDashboard",
      "cloudformation:GetTemplate",
      "cloudformation:ListStacks",
      "cloudformation:ListStackResources",
      "cloudformation:DescribeStacks",
      "cloudformation:ListImports",
      "codedeploy:BatchGetDeployments",
      "codedeploy:GetDeploymentGroup",
      "codedeploy:ListDeployments",
      "config:DescribeConfigurationRecorderStatus",
      "config:GetResourceConfigHistory",
      "events:ListRuleNamesByTarget",
      "xray:GetServiceGraph"
    ],
      "Resource": "*"
  },
  {
    "Sid": "AllowPutTargetsOnASpecificRule",
    "Effect": "Allow",
    "Action": [
      "events:PutTargets",
      "events:PutRule"
    ],
    "Resource": "arn:aws:events:*:*:rule/DevOps-Guru-managed-*"
  },
  {
    "Sid": "AllowCreateOpsItem",
    "Effect": "Allow",
    "Action": [
      "ssm:CreateOpsItem"
    ],
    "Resource": "*"
    "Condition": {
      "StringEquals": {
        "aws:RequestTag/DevOps-GuruInsightSsmOpsItemRelated": "true"
      }
    }
  },
  {
    "Sid": "AllowAddTagsToOpsItem",
    "Effect": "Allow",
    "Action": [
        "ssm:AddTagsToResource"
    ],
    "Resource": "arn:aws:ssm:*:*:opsitem/*"
    "Condition": {
      "StringEquals": {
        "aws:RequestTag/DevOps-GuruInsightSsmOpsItemRelated": "true"
      }
    }
  },
  {
    "Sid": "AllowAccessOpsItem",
    "Effect": "Allow",
    "Action": [
      "ssm:GetOpsItem",
      "ssm:UpdateOpsItem"
    ],
    "Resource": "*",
    "Condition": {
      "StringEquals": {
        "aws:ResourceTag/DevOps-GuruInsightSsmOpsItemRelated": "true"
        }
      }
    }
  ]
}
```

## Creating a service\-linked role for DevOps Guru<a name="create-slr"></a>

You don't need to manually create a service\-linked role\. When you create an insight in the AWS Management Console, the AWS CLI, or the AWS API, DevOps Guru creates the service\-linked role for you\. 

**Important**  
This service\-linked role can appear in your account if you completed an action in another service that uses the features supported by this role; for example, it can appear if you added DevOps Guru to a repository from AWS CodeCommit\. 

## Editing a service\-linked role for DevOps Guru<a name="edit-slr"></a>

DevOps Guru does not allow you to edit the `AmazonDevOpsGuruServiceRolePolicy` service\-linked role\. After you create a service\-linked role, you cannot change the name of the role because various entities might reference the role\. However, you can edit the description of the role using IAM\. For more information, see [Editing a Service\-Linked Role](https://docs.aws.amazon.com/IAM/latest/UserGuide/using-service-linked-roles.html#edit-service-linked-role) in the *IAM User Guide*\.

## Deleting a service\-linked role for DevOps Guru<a name="delete-slr"></a>

If you no longer need to use a feature or service that requires a service\-linked role, we recommend that you delete that role\. That way you don’t have an unused entity that is not actively monitored or maintained\. However, you must disassociate from all repositories before you can manually delete it\. 

**Note**  
If the DevOps Guru service is using the role when you try to delete the resources, the deletion might fail\. If that happens, wait for a few minutes and try the operation again\.

**To manually delete the service\-linked role using IAM**

Use the IAM console, the AWS CLI, or the AWS API to delete the `AmazonDevOpsGuruServiceRolePolicy` service\-linked role\. For more information, see [Deleting a Service\-Linked Role](https://docs.aws.amazon.com/IAM/latest/UserGuide/using-service-linked-roles.html#delete-service-linked-role) in the *IAM User Guide*\.