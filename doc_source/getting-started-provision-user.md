# Step 1: Provision an IAM User<a name="getting-started-provision-user"></a>

Follow these instructions to prepare an IAM user to use AWS CodeDeploy:

1. Create an IAM user or use an existing one associated with your AWS account\. For more information, see [Creating an IAM User](http://docs.aws.amazon.com/IAM/latest/UserGuide/Using_SettingUpUser.html#Using_CreateUser_console) in *IAM User Guide*\.

1. Grant the IAM user access to AWS CodeDeploy—and AWS services and actions AWS CodeDeploy depends on—by copying the following policy and attaching it to the IAM user:

   ```
   {
     "Version": "2012-10-17",
     "Statement" : [
       {
         "Effect" : "Allow",
         "Action" : [
           "autoscaling:*",
           "codedeploy:*",
           "ec2:*",
           "lambda:*",
           "elasticloadbalancing:*",
           "iam:AddRoleToInstanceProfile",
           "iam:CreateInstanceProfile",
           "iam:CreateRole",
           "iam:DeleteInstanceProfile",
           "iam:DeleteRole",
           "iam:DeleteRolePolicy",
           "iam:GetInstanceProfile",
           "iam:GetRole",
           "iam:GetRolePolicy",
           "iam:ListInstanceProfilesForRole",
           "iam:ListRolePolicies",
           "iam:ListRoles",
           "iam:PassRole",
           "iam:PutRolePolicy",
           "iam:RemoveRoleFromInstanceProfile", 
           "s3:*"
         ],
         "Resource" : "*"
       }    
     ]
   }
   ```

   The preceding policy grants the IAM user the access required to deploy to both an AWS Lambda compute platform and an EC2/On\-Premises compute platform\.

    To learn how to attach a policy to an IAM user, see [Working with Policies](http://docs.aws.amazon.com/IAM/latest/UserGuide/ManagingPolicies.html#AddingPermissions_Console)\. To learn how to restrict users to a limited set of AWS CodeDeploy actions and resources, see [Authentication and Access Control for AWS CodeDeploy](auth-and-access-control.md)\.

   You can use the AWS CloudFormation templates provided in this documentation to launch Amazon EC2 instances that are compatible with AWS CodeDeploy\. To use AWS CloudFormation templates to create applications, deployment groups, or deployment configurations, you must grant the IAM user access to AWS CloudFormation—and AWS services and actions that AWS CloudFormation depends on—by attaching an additional policy to the IAM user, as follows:

   ```
   {
     "Version": "2012-10-17",
     "Statement": [
       {
         "Effect": "Allow",
         "Action": [                
           "cloudformation:*"        
         ],
         "Resource": "*"
       }
     ]
   }
   ```

   For information about other AWS services listed in these statements, see:

   + [Overview of AWS IAM Policies](http://docs.aws.amazon.com/IAM/latest/UserGuide/PoliciesOverview.html)

   + [Controlling User Access to Your Load Balancer](http://docs.aws.amazon.com/elasticloadbalancing/latest/userguide/UsingIAM.html)

   + [Controlling Access to Your Auto Scaling Resources](http://docs.aws.amazon.com/autoscaling/latest/userguide/IAM.html)

   + [Controlling AWS CloudFormation Access with AWS Identity and Access Management](http://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/using-iam-template.html)