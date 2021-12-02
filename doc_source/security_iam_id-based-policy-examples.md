# Identity\-based policies for Amazon DevOps Guru<a name="security_iam_id-based-policy-examples"></a>

By default, IAM users and roles don't have permission to create or modify DevOps Guru resources\. They also can't perform tasks using the AWS Management Console, AWS CLI, or AWS API\. An IAM administrator must create IAM policies that grant users and roles permission to perform actions on the resources that they need\. The administrator must then attach those policies to the IAM users or groups that require those permissions\.

To learn how to create an IAM identity\-based policy using these example JSON policy documents, see [Creating policies on the JSON tab](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies_create.html#access_policies_create-json-editor) in the *IAM User Guide*\.

**Topics**
+ [Policy best practices](#security_iam_service-with-iam-policy-best-practices)
+ [Using the DevOps Guru console](#security_iam_id-based-policy-examples-console)
+ [Allow users to view their own permissions](#security_iam_id-based-policy-examples-view-own-permissions)
+ [AWS managed \(predefined\) policies for DevOps Guru](#managed-policies)

## Policy best practices<a name="security_iam_service-with-iam-policy-best-practices"></a>

Identity\-based policies are very powerful\. They determine whether someone can create, access, or delete DevOps Guru resources in your account\. These actions can incur costs for your AWS account\. When you create or edit identity\-based policies, follow these guidelines and recommendations:
+ **Get started using AWS managed policies** – To start using DevOps Guru quickly, use AWS managed policies to give your employees the permissions they need\. These policies are already available in your account and are maintained and updated by AWS\. For more information, see [Get started using permissions with AWS managed policies](https://docs.aws.amazon.com/IAM/latest/UserGuide/best-practices.html#bp-use-aws-defined-policies) in the *IAM User Guide*\.
+ **Grant least privilege** – When you create custom policies, grant only the permissions required to perform a task\. Start with a minimum set of permissions and grant additional permissions as necessary\. Doing so is more secure than starting with permissions that are too lenient and then trying to tighten them later\. For more information, see [Grant least privilege](https://docs.aws.amazon.com/IAM/latest/UserGuide/best-practices.html#grant-least-privilege) in the *IAM User Guide*\.
+ **Enable MFA for sensitive operations** – For extra security, require IAM users to use multi\-factor authentication \(MFA\) to access sensitive resources or API operations\. For more information, see [Using multi\-factor authentication \(MFA\) in AWS](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_credentials_mfa.html) in the *IAM User Guide*\.
+ **Use policy conditions for extra security** – To the extent that it's practical, define the conditions under which your identity\-based policies allow access to a resource\. For example, you can write conditions to specify a range of allowable IP addresses that a request must come from\. You can also write conditions to allow requests only within a specified date or time range, or to require the use of SSL or MFA\. For more information, see [IAM JSON policy elements: Condition](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_elements_condition.html) in the *IAM User Guide*\.

## Using the DevOps Guru console<a name="security_iam_id-based-policy-examples-console"></a>

To access the Amazon DevOps Guru console, you must have a minimum set of permissions\. These permissions must allow you to list and view details about the DevOps Guru resources in your AWS account\. If you create an identity\-based policy that is more restrictive than the minimum required permissions, the console won't function as intended for entities \(IAM users or roles\) with that policy\.

You don't need to allow minimum console permissions for users that are making calls only to the AWS CLI or the AWS API\. Instead, allow access to only the actions that match the API operation that you're trying to perform\.

To ensure that users and roles can still use the DevOps Guru console, also attach the DevOps Guru `AmazonDevOpsGuruReadOnlyAccess` or `AmazonDevOpsGuruFullAccess` AWS managed policy to the entities\. For more information, see [Adding permissions to a user](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_users_change-permissions.html#users_change_permissions-add-console) in the *IAM User Guide*\.

## Allow users to view their own permissions<a name="security_iam_id-based-policy-examples-view-own-permissions"></a>

This example shows how you might create a policy that allows IAM users to view the inline and managed policies that are attached to their user identity\. This policy includes permissions to complete this action on the console or programmatically using the AWS CLI or AWS API\.

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "ViewOwnUserInfo",
            "Effect": "Allow",
            "Action": [
                "iam:GetUserPolicy",
                "iam:ListGroupsForUser",
                "iam:ListAttachedUserPolicies",
                "iam:ListUserPolicies",
                "iam:GetUser"
            ],
            "Resource": ["arn:aws:iam::*:user/${aws:username}"]
        },
        {
            "Sid": "NavigateInConsole",
            "Effect": "Allow",
            "Action": [
                "iam:GetGroupPolicy",
                "iam:GetPolicyVersion",
                "iam:GetPolicy",
                "iam:ListAttachedGroupPolicies",
                "iam:ListGroupPolicies",
                "iam:ListPolicyVersions",
                "iam:ListPolicies",
                "iam:ListUsers"
            ],
            "Resource": "*"
        }
    ]
}
```

## AWS managed \(predefined\) policies for DevOps Guru<a name="managed-policies"></a>

AWS addresses many common use cases by providing standalone IAM policies that are created and administered by AWS\. These AWS\-managed policies grant necessary permissions for common use cases so you can avoid having to investigate what permissions are needed\. For more information, see [AWS Managed Policies](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies_managed-vs-inline.html#aws-managed-policies) in the *IAM User Guide*\.

To create and manage DevOps Guru service roles, you must also attach the AWS\-managed policy named `IAMFullAccess`\.

You can also create your own custom IAM policies to allow permissions forDevOps Guru actions and resources\. You can attach these custom policies to the IAM users or groups that require those permissions\.

The following AWS\-managed policies, which you can attach to users in your account, are specific to DevOps Guru\.

**Topics**
+ [AmazonDevOpsGuruFullAccess](#managed-full-access)
+ [AmazonDevOpsGuruReadOnlyAccess](#managed-read-only-access)
+ [AmazonDevOpsGuruOrganizationsAccess](#organizations-policy)

### AmazonDevOpsGuruFullAccess<a name="managed-full-access"></a>

`AmazonDevOpsGuruFullAccess` – Provides full access to DevOps Guru, including permissions to create Amazon SNS topics, access Amazon CloudWatch metrics, and access AWS CloudFormation stacks\. Apply this only to administrative\-level users to whom you want to grant full control over DevOps Guru\. 

The `AmazonDevOpsGuruFullAccess` policy contains the following statement\.

```
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "DevOpsGuruFullAccess",
	"Effect": "Allow",
	"Action": [
         "devops-guru:*"
       ],
	 "Resource": "*"
    },
    {
      "Sid": "CloudFormationListStacksAccess",      
      "Effect": "Allow",
	"Action": [
	  "cloudformation:DescribeStacks",
	  "cloudformation:ListStacks"
       ],
      "Resource": "*"
   },
   {
      "Sid": "CloudWatchGetMetricDataAccess",
      "Effect": "Allow",
      "Action": [
        "cloudwatch:GetMetricData"
      ],
      "Resource": "*"
    },
    {
      "Sid": "SnsListTopicsAccess",
      "Effect": "Allow",
      "Action": [
        "sns:ListTopics"
      ],
      "Resource": "*"
    },
    {
      "Sid": "SnsTopicOperations",
      "Effect": "Allow",
      "Action": [
        "sns:CreateTopic",
        "sns:GetTopicAttributes",
        "sns:SetTopicAttributes",
        "sns:Publish"
    ],
    "Resource": "arn:aws:sns:*:*:DevOps-Guru-*"
    },
    {
      "Sid": "DevOpsGuruSlrCreation",
      "Effect": "Allow",
      "Action": "iam:CreateServiceLinkedRole",
      "Resource": "arn:aws:iam::*:role/aws-service-role/devops-guru.amazonaws.com/AWSServiceRoleForDevOpsGuru",
      "Condition": {
        "StringLike": {
          "iam:AWSServiceName": "devops-guru.amazonaws.com"
        }
      }
    },
    {
      "Sid": "DevOpsGuruSlrDeletion",        
      "Effect": "Allow",
      "Action": [
        "iam:DeleteServiceLinkedRole",
        "iam:GetServiceLinkedRoleDeletionStatus"
      ],
      "Resource": "arn:aws:iam::*:role/aws-service-role/devops-guru.amazonaws.com/AWSServiceRoleForDevOpsGuru"
    },
    {
        "Sid": "RDSDescribeDBInstancesAccess",
        "Effect": "Allow",
        "Action": [
            "rds:DescribeDBInstances"
        ],
        "Resource": "*"
    }
  ]
}
```

### AmazonDevOpsGuruReadOnlyAccess<a name="managed-read-only-access"></a>

`AmazonDevOpsGuruReadOnlyAccess` – Grants read\-only access to DevOps Guru and related resources in other AWS services\. Apply this policy to users to whom you want to grant the ability to view insights, but not to make any updates to DevOps Guru's analysis coverage boundary, Amazon SNS topics, or Systems Manager OpsCenter integration\. 

The `AmazonDevOpsGuruReadOnlyAccess` policy contains the following statement\.

```
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "AmazonDevOpsGuruReadOnlyAccess",
      "Effect": "Allow",
      "Action": [
        "devops-guru:DescribeAccountHealth",
        "devops-guru:DescribeAccountOverview",
        "devops-guru:DescribeAnomaly",
        "devops-guru:DescribeFeedback",
        "devops-guru:DescribeInsight",
        "devops-guru:DescribeResourceCollectionHealth",
        "devops-guru:DescribeServiceIntegration",
        "devops-guru:GetCostEstimation",
        "devops-guru:GetResourceCollection",
        "devops-guru:ListAnomaliesForInsight",
        "devops-guru:ListEvents",
        "devops-guru:ListInsights",
        "devops-guru:ListNotificationChannels",
        "devops-guru:ListRecommendations",
        "devops-guru:SearchInsights",
        "devops-guru:StartCostEstimation"
      ],
      "Resource": "*"
    },
    {
      "Sid": "CloudFormationListStacksAccess",
      "Effect": "Allow",
      "Action": [
        "cloudformation:DescribeStacks",
        "cloudformation:ListStacks"
      ],
      "Resource": "*"
    },
    {
	  "Effect": "Allow",
	  "Action": [
	  "iam:GetRole"
	  ],
	  "Resource": "arn:aws:iam::*:role/aws-service-role/devops-guru.amazonaws.com/AWSServiceRoleForDevOpsGuru"
    },
    {
      "Sid": "CloudWatchGetMetricDataAccess",
      "Effect": "Allow",
      "Action": [
          "cloudwatch:GetMetricData"
        ],
        "Resource": "*"
    },
    {
        "Sid": "RDSDescribeDBInstancesAccess",
        "Effect": "Allow",
        "Action": [
            "rds:DescribeDBInstances"
        ],
        "Resource": "*"
    }
  ]
}
```

### AmazonDevOpsGuruOrganizationsAccess<a name="organizations-policy"></a>

` AmazonDevOpsGuruOrganizationsAccess` – Provides Organizations administrators access to the DevOps Guru multi\-account view within an organization\. Apply this policy to your organization's administrator\-level users for whom you want to grant full access to DevOps Guru within an organization\. You can apply this policy in your organization's management account and delegated administrator account for DevOps Guru\. You can apply `AmazonDevOpsGuruReadOnlyAccess` or `AmazonDevOpsGuruFullAccess` in addition to this policy to provide read\-only or full access to DevOps Guru\. 

The `AmazonDevOpsGuruOrganizationsAccess` policy contains the following statement\.

```
{
	"Version": "2012-10-17",
	"Statement": [
		{
			"Sid": "AmazonDevOpsGuruOrganizationsAccess",
			"Effect": "Allow",
			"Action": [
				"devops-guru:DescribeOrganizationHealth",
				"devops-guru:DescribeOrganizationResourceCollectionHealth",
				"devops-guru:DescribeOrganizationOverview",
				"devops-guru:ListOrganizationInsights",
				"devops-guru:SearchOrganizationInsights"
			],
			"Resource": "*"
		},
		{
			"Sid": "OrganizationsDataAccess",
			"Effect": "Allow",
			"Action": [
				"organizations:DescribeAccount",
				"organizations:DescribeOrganization",
				"organizations:ListAWSServiceAccessForOrganization",
				"organizations:ListAccounts",
				"organizations:ListChildren",
				"organizations:ListOrganizationalUnitsForParent",
				"organizations:ListRoots"
			],
			"Resource": "arn:aws:organizations::*:"
		},
		{
			"Sid": "OrganizationsAdminDataAccess",
			"Effect": "Allow",
			"Action": [
				"organizations:DeregisterDelegatedAdministrator",
				"organizations:RegisterDelegatedAdministrator",
				"organizations:ListDelegatedAdministrators",
				"organizations:EnableAWSServiceAccess",
				"organizations:DisableAWSServiceAccess"
			],
			"Resource": "*",
			"Condition": {
				"StringEquals": {
					"organizations:ServicePrincipal": [
						"devops-guru.amazonaws.com"
					]
				}
			}
		}
	]
}
```