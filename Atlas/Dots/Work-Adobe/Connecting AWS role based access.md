
> [!NOTE] I DID NOT USE THIS
> ## Warning
> We recommend using IRSA (IAM Roles For Service Accounts) to leverage AWS IAM roles for accessing your AWS resources on EKS clusters instead of using the kube2iam approach (described in this doc below). Please refer to the following [doc](https://devhome.corp.adobe.com/docs/default/component/ethos-flex/docs/iam_role_using_service_account/) instead to use the appropriate/recommended approach.


We recommend using IRSA (IAM Roles For Service Accounts) to leverage AWS IAM roles for accessing your AWS resources on EKS clusters instead of using the kube2iam approach (described in this doc below). Please refer to the following [doc](https://devhome.corp.adobe.com/docs/default/component/ethos-flex/docs/iam_role_using_service_account/) instead to use the appropriate/recommended approach.

### Task
I wanted to setup a token cache for my service Auto Reflow. After discussion, DynamoDB was a simple enough solution for a small use-case.

I created new table in DynamoDB using the Dynamicmedia-development account. I also created a new role allowing it 3rd party access
[Developer Home](https://devhome.corp.adobe.com/docs/default/component/ethos-flex/docs/iam_roles_and_external_id)

I was able to find the AWS account ID (461989703686) from the page
[wiki.corp.adobe.com/login.action?os\_destination=%2Fpages%2Fviewpage.action%3FpageId%3D1082019405&permissionViolation=true](https://wiki.corp.adobe.com/pages/viewpage.action?pageId=1082019405)