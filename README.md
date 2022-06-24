# IAM_Labs

# Lab 3.1.: Customer Managed Policy
How to Create Customer-Managed Policies in AWS

When you initially create your AWS (Amazon Web Services) account, only one AWS-managed policy is in place: AdministratorAccess. However, after you create the first user and log in to AWS using your new administrator account, you can access a large number of AWS-managed policies.

Whenever possible, you should use the AWS-managed policies to ensure that the policy receives automatic updates that reflect changes in AWS functionality. When using a customer-managed policy, you must perform any required updates manually. The following steps get you started using customer-managed policies

Steps to creating a Customer-Management Policies in AWS

Step 1

Sign in to AWS using your administrator account.

Step 2

Navigate to the IAM Management Console.

Step 3

Select Policies in the Navigation pane. You see the Welcome to Managed Policies page.

![image](https://user-images.githubusercontent.com/103466963/175073156-93a7fca8-6f17-412b-ad32-ffaa7ec83770.png)

Click on create policy, it takes you to the image. you can either create the policy using the visual editor or json, you can also use policy generator. In this example we will use the visual editor. so go ahead and select the visual editor. it should look similar to the image below

![image](https://user-images.githubusercontent.com/103466963/175075501-6af25830-db34-4a5e-ad23-ae140ff97c52.png)

Click on service to select the service you want the user/group/role to have access to. In the action pane, select the action you will like the entity to perform. 

![image](https://user-images.githubusercontent.com/103466963/175089890-a96656cc-37d9-42b2-9a29-a88d22518165.png)

Here we are giving the user ec2 list whhich means the user cannot do anything other than that, if he tries to tag, write he will have an access denied
 You must specify the resource for which you want the action to apply to. see image below 

![image](https://user-images.githubusercontent.com/103466963/175095735-581d648e-aefd-496e-9885-20e7cae94bd0.png)

Click on add tags, Tags will will help you identitify the specific policy you want to attach to the entity. You might have so many policies you have created, so adding tags helps to differentiate these policies for easy accessibility

![image](https://user-images.githubusercontent.com/103466963/175098413-9434381e-a340-4b7f-b797-049b582ba8d0.png)

Click on review, here you are prompted to enter the policy name and you can also see all what you defined earlier

![image](https://user-images.githubusercontent.com/103466963/175099501-1fd08872-5169-4e19-af11-d017e4ddf937.png)

Scroll down and click on create policy, it shows you a success message of the policy and you can also view the policy among ythe list of policies already existing

![image](https://user-images.githubusercontent.com/103466963/175100348-4facce65-a916-4658-9320-2ccc05966ac7.png)

Next we will create an IAM uswer by name **compudemy** and attach the policy we just created to the user

Just follow thesame procedure for creating users

![image](https://user-images.githubusercontent.com/103466963/175107812-2614f0e0-a810-4e1b-ab61-ccbfdb712ee2.png)

Now that your user has been created, go ahead and attach the policy to the user

To attach the policy to the user , click on the user and go to the permission section then add permission

![image](https://user-images.githubusercontent.com/103466963/175108288-408d4527-fa2b-4050-91fd-a1a7fae29374.png)

Click on attach existing policicies directly, the easiest way to access the policy is to filter the name as see on the image below

![image](https://user-images.githubusercontent.com/103466963/175111449-e3237350-7eff-4dcf-9788-574a43612ce2.png)

Click on Review then finally add permissions. you have successfully attached this policy to the user

Now lets go into the console and see what the user can do with the policy assigned to them.

Open the console in another browser enter the name of the user you created and the user password, then go to the EC2 service and test permission

WHen you open the EC2 service you are able to view instances, from the image below there are two instances running, when you try to terminate instances, there is an access denied because the oplicy doesnt give us that permission to terminate, launch , start or stop instances. All what we are able to do is to list the instances.

# 3.1.2: Creating IAM Roles for an IAM User
Creating a Role for an IAM User using AWS Management Console

1. To create an IAM role via AWS console first you need to login to your AWS account and select IAM which comes under Security, Identity, and Compliance 

![image](https://user-images.githubusercontent.com/103466963/175316392-682b9bb7-0fa6-42ec-b8f2-c0e80b71a432.png)

Specify the account ID that you want to grant the access to the resources, and then click on Next Permissions button.
If you selected the option "Require external ID" means that it allows the users from the third party to access the resources. You need to enter the external ID provided by the administrator of the third party. This condition is automatically added to the trust policy that allows the user to assume the role.
If you selected the option "Require MFA" is used to restrict the role to the users who provide Multi-factor authentication.
Select a policy that you want to attach with the role. A policy contains the permissions that specify the actions that they can take and resources that they can access.

![image](https://user-images.githubusercontent.com/103466963/175319332-54fd1312-7bb3-4752-8bd0-f4d10141a9db.png)

In the role name box, enter the role name and the role description.

![Image](https://user-images.githubusercontent.com/103466963/175321016-be6029a4-19e7-462c-986f-326f8875a8b5.png)

Then scroll down and click on create role


# IAM CLI Labs

The following commands create a new user named njoya and confirm that the user now exists:

$ aws iam create-user ––user-name njoya 

$ aws iam create-group --group-name compudemy3

$ aws iam add-user-to-group --group-name compudemy3 --user-name njoya

$ aws iam get-user ––user-name njoya

The list‐policies command will return a long list of the preset policies IAM provides. Among them is AmazonEC2ReadOnlyAccess, which permits its assignee only descriptions of running EC2 resources. You can attach a policy to a user by supplying the policy's Amazon Resource Name (ARN) as follows:

$ aws iam list-policies
$ aws iam attach-user-policy 
   ––policy-arn arn:aws:iam::aws:policy/AmazonEC2ReadOnlyAccess 
   ––user-name njoya

Here's the AmazonEC2ReadOnlyAccess policy in JSON format:


{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": "ec2:Describe*",
            "Resource": "*"
        },
        {
            "Effect": "Allow",
            "Action": "elasticloadbalancing:Describe*",
            "Resource": "*"
        },
        {
            "Effect": "Allow",
            "Action": [
                "cloudwatch:ListMetrics",
                "cloudwatch:GetMetricStatistics",
                "cloudwatch:Describe*"
            ],
            "Resource": "*"
        },
        {

            "Effect": "Allow",
            "Action": "autoscaling:Describe*",
            "Resource": "*"
        }
    ]
}
The list‐access‐keys command will return the names of any existing keys associated with the specified username. If you don't specify a name, keys belonging to root will be returned. The create‐access‐key command will create a new key (make sure you copy and save the key data that's returned), and delete‐access‐key will delete the specified key.

$ aws iam list-access-keys ––user-name steve
$ aws iam create-access-key ––user-name steve
$ aws iam delete-access-key ––user-name steve ––access-key-id AKIA


