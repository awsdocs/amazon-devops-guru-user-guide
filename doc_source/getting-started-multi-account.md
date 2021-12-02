# Monitor accounts across your organization<a name="getting-started-multi-account"></a>

If you choose to monitor applications across your organization, log into your organization management account\. You can optionally set up an organization member account as a **delegated administrator**\. You can only have one delegated administrator at a time and can modify the administrator settings later\. Both the management account and the delegated administrator account that you set up have access to all insights across all accounts in your organization\.

**Enable DevOps Guru to view aggregated insights**

1. Open the Amazon DevOps Guru console at [https://console\.aws\.amazon\.com/devops\-guru/](https://console.aws.amazon.com/devops-guru/)\.

1. Choose **Monitor applications across your organizations** as the setup type\.

1. Choose which account you'd like to use as your delegated administrator\. Then, choose **Register delegated administrator**\. This provides access to a consolidated view for any account that has DevOps Guru enabled\. The delegated administrator has a consolidated view of all DevOps Guru insights and metrics across your organization\. You can enable other accounts with SSM quick setup or AWS CloudFormation stack sets\. To learn more about quick setup, see [Configure DevOps Guru with Quick Setup](https://docs.aws.amazon.com/systems-manager/latest/userguide/quick-setup-devops.html)\. To learn more about setting up with stack sets, see [Working with stacks](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/stacks.html) in the *AWS CloudFormation User Guide*, and [Step 2 – Determine coverage for DevOps Guru](setting-up.md#setting-up-determine-coverage)\. and [Use AWS CloudFormation stacks to identify resources in your DevOps Guru applications](working-with-cfn-stacks.md)\.