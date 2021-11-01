*This is a sample outline for an IAM Pulse Template focused on providing insight around a specific topic as it relates to IAM best practices. Your article doesn't need to follow this prescriptively, just use this as a basic guideline as you think through your writing process.*

----

# Title: Cooking IAM Policies
## Subtitle: The complete recipe
## Author: Loboaveces
## Type: Explainer

**Cloud Provider(s)**
 - [*] AWS
 - [ ] GCP
 - [ ] Azure
 - [ ] Other

**Code Framework(s)**
 - [ ] CloudFormation
 - [ ] Terraform
 - [ ] Pulumi
 - [ ] Ansible
 - [ ] Puppet
 - [ ] Chef
 - [ ] SaltStack
 - [*] Other

**Identity Provider(s)**
 - [ ] Okta
 - [ ] Active Directory
 - [ ] LDAP
 - [*] Other

**Compliance Guideline(s)**
 - [*] AWS CIS
 - [ ] CSA
 - [ ] SOC 2
 - [ ] PCI-DSS
 - [ ] NIST
 - [ ] FedRAMP
 - [ ] Other

**Technical Theme(s)**
 - [ ] Zero Trust
 - [ ] Serverless
 - [ ] Kubernetess

----


## Introduction
I'm not going to lie to you this is not an article (I don't even know how this arrived here) but it's a detailed recipe to make IAM policies.
But wait! don't leave maybe this is what you are looking for because you'll understand how to build an IAM policy, its components, and how all in conjunction make an IAM policy. After this, you'll be able to modify the "recipe" to create policies for different services and use cases.


## The Topic
This explainer is about creating IAM policies. The main goal is to explain in detail how to create an IAM policy understanding its components and how they are related easily. Also, after reading it you'll be able to see any IAM policy and understand what is happening.

## Your Explanation
 
Did you ever eat a layer cake?  
I ask you this because cooking an IAM policy is similar to that of layer cake. So, if you did not eat one (shame on you) or you forgot the taste, consider getting one after reading this just for research purposes, of course.
![Image description](https://assets.tmecosys.com/image/upload/t_web767x639/img/recipe/ras/Assets/feb740ee-6c3f-4246-9c75-93ab2fa82cad/Derivates/04674732-149d-4629-a176-e358d8098287.jpg)

Well, to prepare an IAM policy prevously we need three main components defined:  
- Principals: User, role, external user, or application that sent the request and the policies associated with that principal.
So, always remenber the question: Who? --> Who is requesting something with this policy?
- Actions: As the name says, basically are the actions that the principal is attempting to do.
The question for this component is: What? --> What we want for the principal to do?
- Resources: Are the AWS resource objects upon which the actions will be performed.
Each of these layers can have multiple ingredients, after preparing them, we will join everything to have the resulting IAM policy.  
Question for this is: Which? --> Which Resource will the Principal take Action on? (target)
As you may thinking, AWS evaluates the IAM policies when a principal makes a request. Permissions in the policies determine whether the request is allowed or denied. Yes, as simple as that.

To cook an IAM policy you must select which flavor will you use. There are three main flavors that we will cover in this recipe:  
- AWS Managed: Managed by AWS and can be attached to multiple users, groups, and roles.  
- Customer managed: Custom policies that you can create and give you more precise control than managed policies and can be attached to multiple users, groups, and roles.  
- Inline: Embedded directly into a user, group, or role. It's not recommended to use them but they are useful if you would like to maintain s strict one-to-one relationship between a policy and the principal entity where it is applied. 

## Now, let's prepare the ingredients:
For this recipe we'll need:  
![IAM ingredients](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/ng8mlzb1is60f4nr7l0d.png)  
  
I know, I know... When you'll be in the market buying all this stuff, it can be a little overwhelming knowing how to choose the correct ingredients. But don't worry, I will explain to you the characteristics of these ingredients so you can make good shopping.  
- version: It specifies the language syntax rules that are to be used to process a policy. To use all of the available policy features, include the following Version:  
```
"Version": "2012-10-17"
``` 
- Statement: These are the main element of a policy, so be careful getting them. The Statement element can contain a single statement or an array of individual statements. Each individual statement block must be enclosed in curly braces { }. For multiple statements, the array must be enclosed in square brackets [ ].  
- Sid: Provides a brief description of the policy. (optional)
- Effect: Specify whether the statement will explicitly allow or deny access.
- Action: Describes what type of access should be allowed or denied. Each AWS service has its own set of Actions or NotActions that describe tasks that you can perform with that service. (NotAction is an advanced policy element that explicitly matches everything except the specified list of actions.)
- Resource: Specifies the object or objects that the statement covers. Statements must include either a Resource or a NotResource element. You specify a resource using an ARN. (NotResource is an advanced policy element that explicitly matches every resource except those specified.  
- Conditions: The Condition element (or Condition block) lets you specify conditions for when a policy is in effect. The Condition element is optional. In the Condition element, you build expressions in which you use condition operators (equal, less than, etc.)  

## Directions:

Now that we have all the ingredients that we need let's start preparing the policy. In this case, as an example, we will make an IAM policy that allows managing Amazon EC2 security groups associated with a specific virtual private cloud (VPC). This policy also provides the permissions necessary to complete this action on the console. 
Do you remember that I told you that baking an IAM policy is much similar to a layer cake preparation? well, it is! "Statements" are the key. We can define one or multiple statements, one by one, just like layers. For this case, and to make our preparation example short but complete, we will have two layers, which means two statements that will allow us to achieve what we want.  
Step 1: Grab the version you got and put it at the beginning of the file.  
Step 2: We will start with the first statement (layer). So, we need:  
- 2.1 The Action you chose, remember that each resource has its list of actions defined. (For example, you can consult the actions available for EC2 here: https://docs.aws.amazon.com/AWSEC2/latest/APIReference/API_Operations.html
- 2.2 Add the resource that will be covered by this statement. If you want to apply it for all, you can put an "*".
- 2.3 Finally, add the effect, you can choose to allow or deny the action(s) for the chosen resource.
Step 3: Now we can add our second statement, the process is similar for all statements, but of course with the ingredients we choose.
- 3.1 One more time we will choose the actions that we want from the list of available actions.
- 3.2 Then we will add the resource, in the previous statement we used "*", now we will use a specific resource by using its ARN (Amazon Resource Name).
- 3.3 Then comes the effect, choose the effect (allow or deny) for these actions on the resource.
- 3.4 In this case, and to have a complete example, we will use conditions when this statement has an effect, in this case, for a specific VPC.  

And that's it! Let's see how it looks:

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Action": [
                "ec2:DescribeSecurityGroups",
                "ec2:DescribeSecurityGroupReferences",
                "ec2:DescribeStaleSecurityGroups",
                "ec2:DescribeVpcs"
            ],
            "Resource": "*",
            "Effect": "Allow"
        },
        {
            "Action": [
                "ec2:AuthorizeSecurityGroupEgress",
                "ec2:AuthorizeSecurityGroupIngress",
                "ec2:DeleteSecurityGroup",
                "ec2:RevokeSecurityGroupEgress",
                "ec2:RevokeSecurityGroupIngress"
            ],
            "Resource": [
                "arn:aws:ec2:::security-group/*"
            ],
            "Effect": "Allow",
            "Condition": {
                "StringEquals": {
                    "ec2:Vpc": "arn:aws:ec2:::vpc/"
                }
            }
        }
    ]
}
```

What do you think? Do you dare to prepare this recipe? Remember that it can be adapted according to your needs. Give it a try!
Finally, I did this image with the recipe, so feel free to grab it. If you want you can save it, share it, or print it so you can have it on hand. 
![IAM recipe](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/zqjs6v6hwh3qs7wbdo3g.png)  

## Conclusion  

As you can see creating or understanding IAM Policies is not a complex task, actually is very simple. Now you have all the elements to create your own policy and also, and maybe more important, understand what policies do in detail seeing the content and not only the name of the policy. Sometimes we apply policies just because it's name seems adecuate or some tutorial says so, it's is better to check what we are applying and verify if all the actions we are allowing or denying are the ines that we want.
