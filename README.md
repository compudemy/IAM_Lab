# IAM_Lab

Lab 3.1.2: Customer Managed Policy
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


