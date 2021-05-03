# Amazon DevOps Guru permissions reference<a name="auth-and-access-control-permissions-reference"></a>

You can use AWS\-wide condition keys in your DevOps Guru policies to express conditions\. For a list, see [IAM JSON Policy Elements Reference](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_elements.html#AvailableKeys) in the *IAM User Guide*\. 

 You specify the actions in the policy's `Action` field\. To specify an action, use the `devops-guru:` prefix followed by the API operation name \(for example, `devops-guru:SearchInsights` and `devops-guru:ListAnomalies`\)\. To specify multiple actions in a single statement, separate them with commas \(for example, `"Action": [ "devops-guru:SearchInsights", "devops-guru:ListAnomalies" ]`\)\. 

 **Using wildcard characters** 

 You specify an Amazon Resource Name \(ARN\), with or without a wildcard character \(\*\), as the resource value in the policy's `Resource` field\. You can use a wildcard to specify multiple actions or resources\. For example, `devops-guru:*` specifies all DevOps Guru actions and `devops-guru:List*` specifies all DevOps Guru actions that begin with the word `List`\. The following example refers to all insights with a universally unique identifier \(UUID\) that begins with `12345`\. 

```
arn:aws:devops-guru:us-east-2:123456789012:insight:12345*
```

 You can use the following table as a reference when you are setting up [Authenticating with identities](security-iam.md#security_iam_authentication) and writing permissions policies that you can attach to an IAM identity \(identity\-based policies\)\. 