*This is a sample outline for an IAM Pulse Template focused on providing insight around a specific topic as it relates to IAM best practices. Your article doesn't need to follow this prescriptively, just use this as a basic guideline as you think through your writing process.*

----

# Title: Cokking IAM Policies
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
I'm not going to lie to you, this is not an article (I don't even know how this arrived here). This is a detailed recipe to make IAM policies. 
Are you sure this is what you were looking for? well, maybe it is because here I'll explain to you how to buid an IAM policy decribing all its componets and how all in conjuction made a policy. After this you'll be able to modify the "recipe" to create policies for different services and use cases. 


## The Topic
This explainer is about AWS IAM policies. The main goal is to explain in detail how to create an IAM policy and also how to understand its components and how they are related in an easy way.

## Your Explanation
 
Did you ever eat a layer cake?  
I ask you this because the process of cooking an IAM policy is similar to that of layer cake. So, if you did not eat one (shame on you) or you forgot the taste, consider getting one after reading this just for academic purposes, of course.
[image of the cake]  

Well, to prepare an IAM policy we will divide the process of cooking it into three main layers:  
- Principals: User, role, external user, or application that sent the request and the policies associated with that principal.
- Actions: As the name says, basically are the actions that the principal is attempting to do.
- Resources: Are the AWS resource objects upon which the actions will be performed.
Each of these layers can have multiple ingredients, after preparing them, we will join everything to have the resulting IAM policy.  
As you may know, AWS evaluates the IAM policies when a principal makes a request. Permissions in the policies determine whether the request is allowed or denied. Yes, that is how it works.

To cook an IAM policy you must select which flavor will you use. There are three main flavors that we will cover in this recipe:  
- AWS Managed: Managed by AWS and can be attached to multiple users, groups, and roles.  
- Customer managed: Custom policies that you can create and give you more precise control than managed policies and can be attached to multiple users, groups, and roles.  
- Inline: Embedded directly into a user, group, or role. It's not recommended to use them but they are useful if you would like to maintain s strict one-to-one relationship between a policy and the principal entity where it is applied. 

## Now, let's prepare the ingredients:
For this recipe we'll need:
- Version
- Statement
- Sid
- Effect
- Action
- Resource
[an image of ingredients]

I know, I know... When you'll be in the market buying all this stuff, it can be a little overwhelming knowing how to choose the correct ingredients. But don't worry I will explain to you the characteristics of these ingredients so you can make good shopping.
- version: This is straightforward, you need  
- Statement: These are the main element of a policy, so be careful getting them. Depending on the policy you want to prepare it can contain a single statement or an array of individual statements. (Must be enclosed with curly brackets{}).  
- Sid: Provides a brief description of the policy. (optional)
- Effect: Specify whether the statement will explicitly allow or deny access.
- Action: Describes what type of access should be allowed or denied.
- Resource: Specify the object or objects that the policy statement covers.

## Cooking the policy:

[Here I explain the process with an example]


what does the policy we created do?

[ prepare a graphic with arrows)
[ explain the ghaphic]

The end - [finish with something related to cooking to reinforce the main purpose of IAM policies]
