*This is a sample outline for an IAM Pulse Template focused on providing insight around a specific topic as it relates to IAM best practices. Your article doesn't need to follow this prescriptively, just use this as a basic guideline as you think through your writing process.*

----

# Title: {IAM users, roles, groups and roles explained in an airport}
## Subtitle: {An analogy for cloud enthusiasts and travelers}
## Author: {Loboaveces}
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
Hi, I'm Carlos, a Cloud enthusiast just like you. I'm a telecommunication Engineer with almost nine years of experience in IT, I started with bare metal Linux servers, Cisco network devices configuration and Data Centers cabling stuff, but in the way I was absorved by the Cloud world (thanks god!) and since then I've been discovering this fascinating world every day. currently I'm a DevOps Engineer and I define my self as a lifelong learner.
I love to write, I write every day small pharaghaphs about different things just for fun, but my native language is spanish (Bolivia), so for me it's a challenge to write "well" in English and that is the most exiting part of this.

## The Topic
This explainer is about AWS IAM basics, the main goal is to explain AWS IAM and how to define the policies related to them in an easy way, I'll use a real-world analogy so anyone who read this can understand.

## Your Explanation

### First, what is this IAM thing about?

Imagine a really big airport, like Hartsfield–Jackson Airport in Atlanta (U.S) or Beijing International Airport (China) with hundreds of airline offices, a lot of flights arriving and leaving, employees doing their different jobs, and many people going around. Even if we don't know exactly how everything works in an airport, we can be sure that it works.  
Well, to understand Identity access management (IAM) we can think of Amazon Web Services (AWS) as a big Airport with hundreds of services (airlines), traffic between services (flights), and many users with different roles taking advantage of cloud services (people).  
![Airport](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/3oypxe2occxlx053i6vh.jpg)  

What I'm trying with this example, is to explain how IAM users, groups, and roles work, because I see many new developers struggling with these concepts. If you read this I hope that clarifies everything for you. Let me know in a comment how it was, and how it can improve.
OK, let's do this!  
I think that we've all been to the airport at least one time, right? Well, I don't know if you noticed but in airports, there is a complex access control system to keep individuals out of restricted areas and maintain the facilities secure, it is composed of a lot of people with different roles, scanners, cameras, and many other devices and equipment. All of them are there to maintain the security of the airport (infrastructure, airlines, and passengers)  
Ok, we can say that Identity Access Management is the same, is the service that provides access control in AWS, so it controls all the access to AWS resources. Is important to say that IAM is not the only service that provides security, but is the most important. And is also composed of different elements, features, and tools.  
### The root user:  
In an airport, airlines rent offices to operate and offer flights to their customers. There are big international airlines and also small airlines with local operations. (Just like the users of AWS) When an airline company wants to operate in the airport they sign a contract (terms of use) to use the airport services. Let's say that the contract is signed by the regional manager who represents the airline in that airport, We could say that he gets the office keys that allow him to access anywhere.  
When you create an AWS account, you accept some terms and conditions for the service, and immediately you have access to all the services. This account is called the root account and with this account, you have all the permissions to create resources, assign new users and manage all your infrastructure and applications in AWS services.  
Let's continue, the manager shouldn't do everything, right? he or she can't run an airline office by itself, there have to be a lot of people that work for the company. What he can do is hire more staff. There can be sales agents, operations agents, baggage handlers, flight dispatchers, administrative support staff, among others. In the end, the manager will only sit at his desk eating donuts like a boss. (I don't know if that's the case of a true manager but for this example it is).  
When you first create an AWS account, you begin with a single sign-in identity that has complete access to all the services and resources in the account. This identity is called the AWS account root user. You can sign in as the root user using the email address and password that you used to create the account.  
AWS strongly recommends that you do not use the root user for your everyday tasks, even the administrative ones. Instead, create IAM users and assign them different permissions to perform different tasks. Then securely lock away the root user credentials and use them to perform only a few account and service management tasks. Let that account rest eating donuts.  
### IAM Users:  
Airports are divided into landside and airside zones. The landside is subject to fewer special laws and is part of the public realm, while access to the airside zone is tightly controlled. The airside area includes all parts of the airport around the aircraft and the parts of the buildings that are restricted to staff.  
Let's suppose that the manager hired some people to perform different jobs and gave them credentials and different permissions to access different areas. For example, the sales agents are at the counter in contact with clients but will never enter the airside area; the baggage handlers on the other hand are allowed to enter the airside area to carry the luggage to the aircraft.  
Well, in AWS is almost the same. An IAM user is an entity that you create in AWS to represent the person or application that uses it to interact with AWS. A user in AWS consists of a name and credentials that can access AWS in different ways depending on what services and resources it is allowed to use.  
A brand new IAM user created using the AWS CLI or AWS API has no credentials of any kind. You must create the type of credentials for an IAM user based on the needs of your user.  
### IAM Groups:  
Do you know RFID cards? These are the cards that are used to grant access to restricted areas to the cardholder. So you can program which doors will open with that card.
In this case, the manager decided to give the employees RFID cards of different colors depending on the access permissions that they need. For example, there is a group of ten people in charge of the maintenance of aircraft. All of them, who received the orange card, can access the same restricted areas in the airside zone.  
Let's suppose that an employee is promoted to a new job. What happens then? Well, it's simple, he will be part of another group, so he will return his card and receive a new one.  
An IAM user group is a collection of IAM users. User groups let you specify permissions for multiple users, which can make it easier to manage the permissions for those users. For example, you could have a user group called "Devs" and give that user group the types of permissions that developers typically need. Any user in that user group automatically has the permissions that are assigned to the user group. If a new user joins your organization and needs developer privileges, you can assign the appropriate permissions by adding the user to that user group. Similarly, if a person changes jobs in your organization, instead of editing that user's permissions, you can remove him or her from the old user groups and add him or her to the appropriate new user groups.  
### IAM Roles:  
Imagine that every three months a third-party auditory team must enter the office and check how all operations are being carried out. The manager is not going to generate RFID cards for them, because they may not be the same people who visit the office every time, and because they are not part of the company.  
To resolve this, the manager decides to create predefined cards with all the permissions that they will need in their auditors' role. So these people get these cards only for the period that they remain in the offices, later when they have done with their job, they have to return the cards and they lose all the access that had granted.  
An IAM role is an IAM identity that you can create in your account that has specific permissions. An IAM role is similar to an IAM user. However, instead of being uniquely associated with one person, a role is intended to be assumable by anyone who needs it. Also, a role does not have standard long-term credentials such as a password or access keys associated with it. Instead, when you assume a role, it provides you with temporary security credentials for your role session.  
You can use roles to delegate access to users, applications, or services that don't normally have access to your AWS resources. For example, you might want to grant users in your AWS account access to resources they don't usually have, or grant users in one AWS account access to resources in another account. Or you might want to allow a mobile app to use AWS resources, but not want to embed AWS keys within the app (where they can be difficult to rotate and where users can potentially extract them). Sometimes you want to give AWS access to users who already have identities defined outside of AWS, such as in your corporate directory. Or, you might want to grant access to your account to third parties so that they can perform an audit on your resources.  

## Conclusion
*Add any additional materials or further reading. What else should the reader know about this topic, and where can they go to learn more?*


----

### Inserting Code Blocks & Images
*View the markdown to copy*

**Code**

```
Code:
{Your Code Here: make it easy to see what's a variable, like uppercase values.}
```
```
Docs:
{Code Docs Here: make note of any variables to replace or elements to customize.}
```

**Images**
![enter image caption here](https://i.picsum.photos/id/864/200/200.jpg?hmac=enPW23d2MpTvv2RfL7CtuO_cKSvCg4DGCYtNPc4-48M)
