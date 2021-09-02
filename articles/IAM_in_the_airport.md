*This is a sample outline for an IAM Pulse Template focused on providing insight around a specific topic as it relates to IAM best practices. Your article doesn't need to follow this prescriptively, just use this as a basic guideline as you think through your writing process.*

----

# Title: IAM users, roles, groups and roles explained in an airport
## Subtitle: An analogy for cloud enthusiasts and travelers
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
Hi, I'm Carlos, a Cloud enthusiast just like you. I'm a Telecommunications Engineer with almost ten years of experience in IT, I started with bare-metal Linux servers, Cisco network devices configuration, and Data Centers cabling stuff, but in the way, I was absorbed by the "cloud" (thank god!) and since then I've been discovering this fascinating world every day. currently, I'm a DevOps Engineer and I define myself as a lifelong learner.

## The Topic
This explainer is about AWS IAM basics, the main goal is to explain AWS IAM and how to define the policies related to them in an easy way, I'll use a real-world analogy so anyone who reads this can understand.

## Your Explanation

### First, what is this IAM thing about?

Imagine a really big airport, like Hartsfield–Jackson Airport in Atlanta (U.S) or Beijing International Airport (China) with hundreds of airline offices, a lot of flights arriving and leaving, employees doing their different jobs, and many people going around. Even if we don't know exactly how everything works in an airport, we can be sure that it works.  
Well, to understand Identity access management (IAM) we can think of Amazon Web Services (AWS) as a big Airport with hundreds of services (airlines), traffic between services (flights), and many users with different roles taking advantage of cloud services (people).  
![Airport](https://res.cloudinary.com/practicaldev/image/fetch/s--QBL_V5re--/c_imagga_scale,f_auto,fl_progressive,h_420,q_auto,w_1000/https://dev-to-uploads.s3.amazonaws.com/uploads/articles/o310lcw1l8qlg7f9kgee.jpg)  

What I'm trying with this example, is to explain how IAM users, groups, and roles work and how to define yheir policies, because I see many people struggling with these concepts.
OK, let's do this!  
I think that we've all been to the airport at least one time, right? Well, I don't know if you noticed but in airports, there is a complex access control system to keep individuals out of restricted areas and maintain the facilities secure, it is composed of a lot of people with different roles, scanners, cameras, and many other devices and equipment. All of them are there to maintain the security of the airport (infrastructure, airlines, and passengers)  
Ok, we can say that Identity Access Management is the same, is the service that provides access control in AWS, so it controls all the access to AWS resources. Is important to say that IAM is not the only service that provides access control and security, but is the most important. And is also composed of different elements, features, and tools.  
The main concept on IAM is policies, you manage access in AWS by creating policies and attaching them to IAM identities (users, groups of users, or roles) or AWS resources. A policy is an object in AWS that, when associated with an identity or resource, defines their permissions. AWS evaluates these policies when an IAM principal (user or role) makes a request  
### The root user:  
In an airport, airlines rent offices to operate and offer flights to their customers. There are big international airlines and also small airlines with local operations. (Just like the different users of AWS) When an airline company wants to operate in the airport they sign a contract (terms of use) to use the airport services. Let's say that the contract is signed by the regional manager who represents the airline in that airport, We could say that he gets the office keys that allow him to access anywhere.  
When you create an AWS account, you accept some terms and conditions for the service, and immediately you have access to all the services. This account is called the root account and with this account, you have all the permissions to create resources, assign new users and manage all your infrastructure and applications in AWS services.  
But let's continue with our example, the manager shouldn't do everything, right? he or she can't run an airline office by itself, there have to be a lot of people that work for the company. What he can do is hire more staff. There can be sales agents, operations agents, baggage handlers, flight dispatchers, administrative support staff, among others. In the end, the manager will only sit at his desk eating donuts like a boss. (I don't know if that's the case of a true airline manager but for this example it is).  
When you first create an AWS account, you begin with a single sign-in identity that has complete access to all the services and resources in the account. This identity is called the AWS account root user. You can sign in as the root user using the email address and password that you used to create the account.  
AWS strongly recommends that you do not use the root user for your everyday tasks, even the administrative ones. Instead, create IAM users and assign them different permissions to perform different tasks. Then securely lock away the root user credentials and use them to perform only a few account and service management tasks. Let that account eating donuts.  
The AWS account root user can create IAM identities as the manager can hire people. An IAM identity provides access to an AWS account, represents a user, and can be authenticated and then authorized to perform actions in AWS. Each IAM identity can be associated with one or more policies. Policies determine what actions a user, role, or member of a user group can perform, on which AWS resources, and under what conditions. Let's see this in detail:

### IAM Users:  
Airports are divided into landside and airside zones. The landside is subject to fewer special laws and is part of the public realm, while access to the airside zone is tightly controlled. The airside area includes all parts of the airport around the aircraft and the parts of the buildings that are restricted to staff.  
Let's suppose that the manager hired some people to perform different jobs and gave them RFID credentials (IAM identities) with different permissions to access different areas (Policies). For example, the sales agents are at the counter in contact with clients but will never enter the airside area; the baggage handlers on the other hand are allowed to enter the airside area to carry the luggage to the aircraft.  
Well, in AWS is almost the same. An IAM user is an entity that you create in AWS to represent the person or application that uses it to interact with AWS. A user in AWS consists of a name and credentials that can access AWS in different ways depending on what services and resources it is allowed to use. When you create an IAM user, you grant it permissions by making it a member of a user group that has appropriate permission policies attached (recommended), or by directly attaching policies to the user.  
**How the policies look like?**  
To continue with our example, the policies are the job functions manual. When someone is hired, they receive a contract and a job manual specifying what functions they can perform and in the case of the airport, which places they can enter, right?  
well, policies are the same. We attach policies to identities or resources to define their permissions. That's it.  
Let's define the policy for a baggage handler, he **puts** baggage to the baggage carousel device, he also **gets** baggage from there to upload them to the plane. Additionally, he can remove suspicious baggage (**deletes** it) and generates a **list** with all the baggage information, their destiny or current **location**, etc.  
Ok, Let's suppose that every aircraft is an S3 bucket and the objects are the baggage from passengers that are uploaded to the aircraft. The person that can do this is the baggage handler, so we have to define a **inline policy** for this person that should look as follows:
```
{
   "Version":"2012-10-17",
   "Statement":[
      {
         "Effect":"Allow",
         "Action": "s3:ListAllMyBuckets",
         "Resource":"*"
      },
      {
         "Effect":"Allow",
         "Action":["s3:ListBucket","s3:GetBucketLocation"],
         "Resource":"arn:aws:s3:::awsexamplebucket1"
      },
      {
         "Effect":"Allow",
         "Action":[
            "s3:PutObject",
            "s3:PutObjectAcl",
            "s3:GetObject",
            "s3:GetObjectAcl",
            "s3:DeleteObject"
         ],
         "Resource":"arn:aws:s3:::awsexamplebucket1/*"
      }
   ]
}
```

s3:PutObject, s3:GetObject, and s3:DeleteObject permissions to the user, the policy also grants the s3:ListAllMyBuckets, s3:GetBucketLocation, and s3:ListBucket permissions. These are the additional permissions required by the console. Also, the s3:PutObjectAcl and the s3:GetObjectAcl actions are required to be able to copy, cut, and paste objects in the console.  
That's it! now the baggage handler can do his job without problems. When you create an IAM user, you grant it permissions by directly attaching policies to the user or by making it a member of a user group that has appropriate permission policies attached (recommended). And because we have many baggage handlers we are going to see how IAM groups work.

### IAM Groups:  
Do you know RFID credentials? These are the cards that are used to grant access to restricted areas to the cardholder. So you can program which doors will open with that card.
In this case, the manager decided to give the employees RFID cards of different colors depending on the access permissions that they need. For example, there is a group of ten people in charge of the maintenance of aircraft. All of them, who received the orange card, can access the same restricted areas in the airside zone.  
Let's suppose that an employee is promoted to a new job. What happens then? Well, it's simple, he will be part of another group, so he will return his card and receive a new one.  
An IAM user group is a collection of IAM users. User groups let you specify permissions for multiple users, which can make it easier to manage the permissions for those users. For example, you could have a user group called "Devs" and give that user group the types of permissions that developers typically need. Any user in that user group automatically has the permissions that are assigned to the user group. If a new user joins your organization and needs developer privileges, you can assign the appropriate permissions by adding the user to that user group. Similarly, if a person changes jobs in your organization, instead of editing that user's permissions, you can remove him or her from the old user groups and add him or her to the appropriate new user groups.  
In the case of the baggage handlers, we will create a group named "baggagers" and we will attach a policie so they can perform their jobs.

Grant group-level permissions

Once again, as we defined for the single users, they need to be able to do the following:

Let's define the policy for a baggage handler, they **put** baggage to the baggage carousel device, they also **get** baggage from there to upload them to the plane. Additionally, they can remove suspicious baggage (**delete** it) and generate a **list** with all the baggage information, their destiny or current **location**, etc.  
Ok, Let's suppose that every aircraft is an S3 bucket and the objects are the baggage from passengers that are uploaded to the aircraft. The person that can do this is the baggage handler, so we have to create a policy that grants these permissions, and then attach it to the "baggagers" group. 


```
{
   "Version":"2012-10-17",
   "Statement":[
      {
         "Effect":"Allow",
         "Action": "s3:ListAllMyBuckets",
         "Resource":"*"
      },
      {
         "Effect":"Allow",
         "Action":["s3:ListBucket","s3:GetBucketLocation"],
         "Resource":"arn:aws:s3:::awsexamplebucket1"
      },
      {
         "Effect":"Allow",
         "Action":[
            "s3:PutObject",
            "s3:PutObjectAcl",
            "s3:GetObject",
            "s3:GetObjectAcl",
            "s3:DeleteObject"
         ],
         "Resource":"arn:aws:s3:::awsexamplebucket1/*"
      }
   ]
}
```

s3:PutObject, s3:GetObject, and s3:DeleteObject permissions to the user, the policy also grants the s3:ListAllMyBuckets, s3:GetBucketLocation, and s3:ListBucket permissions. These are the additional permissions required by the console. Also, the s3:PutObjectAcl and the s3:GetObjectAcl actions are required to be able to copy, cut, and paste objects in the console.  
That's it! now all the baggage handlers can do their job.


### IAM Roles:  
Imagine that every three months a third-party auditory team must enter the office and check how all operations are being carried out. The manager is not going to generate RFID cards for them, because they may not be the same people who visit the office every time, and because they are not part of the company.  
To resolve this, the manager decides to create predefined RFID cards with all the permissions that they will need in their auditors' role. So these people get these cards only for the period that they remain in the offices, later when they have done with their job, they have to return the cards and they lose all the access that had granted.  
An IAM role is an IAM identity that you can create in your account that has specific permissions. An IAM role is similar to an IAM user. However, instead of being uniquely associated with one person, a role is intended to be assumable by anyone who needs it. Also, a role does not have standard long-term credentials such as a password or access keys associated with it. Instead, when you assume a role, it provides you with temporary security credentials for your role session.  
You can use roles to delegate access to users, applications, or services that don't normally have access to your AWS resources. For example, you might want to grant users in your AWS account access to resources they don't usually have, or grant users in one AWS account access to resources in another account. Or you might want to allow a mobile app to use AWS resources, but not want to embed AWS keys within the app (where they can be difficult to rotate and where users can potentially extract them). Sometimes you want to give AWS access to users who already have identities defined outside of AWS, such as in your corporate directory. Or, you might want to grant access to your account to third parties so that they can perform an audit on your resources.  

I our example let's say that the auditory team need to check some paperes and registries. To do this the manager conceed them access to this information that is available in the "Airtrail room".
Yes as you may imagine we are going to grant access to AWS Cloudtrail service to the auditors creating a role.  
A typical approach is to create an IAM role that has the appropriate permissions. For example, you might create an IAM role for users who should have access to CloudTrail actions to view trail information but not create or change trails. We will create a new role named "auditor_role" and attach a AWS managed policy (Created by AWS), find and select the following policiy for CloudTrail:  
**AWSCloudTrailReadOnlyAccess:** This policy lets users in the group view the CloudTrail console, including recent events and event history. These users can also view existing trails and their buckets. Users can download a file of event history, but they cannot create or update trails.  
This seems simple enough for the usage that they need. Right? 
*Remember allways granting the least privilege, or granting only the permissions required to perform a task.  
AWSCloudTrailReadOnlyAccess looks like this:  
```
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": [
        "cloudtrail:DescribeTrails",
        "cloudtrail:GetTrail",
        "cloudtrail:GetTrailStatus",
        "cloudtrail:LookupEvents",
        "cloudtrail:ListPublicKeys",
        "cloudtrail:ListTags",
        "s3:ListAllMyBuckets",
        "kms:ListAliases",
        "lambda:ListFunctions"
      ],
      "Resource": "*"
    }
  ]
}
```
In the policy statements, the ***Effect*** element specifies whether the actions are allowed or denied. The ***Action*** element lists the specific actions that the user is allowed to perform. The ***Resource*** element lists the AWS resources the user is allowed to perform those actions on. For policies that control access to CloudTrail actions, the Resource element is usually set to *, a wildcard that means "all resources."

The read-only policy doesn't grant user permission for the CreateTrail, UpdateTrail, StartLogging, and StopLogging actions. Users with this policy are not allowed to create trails, update trails, or turn logging on and off.

## Conclusion

This was just an introduction to AWS IAM service and policies in an easy way, I really hope that everything it's clear now for you. If you want to learn further the best thing that I can recommend is read the oficial AWS Documentation or other articles here IAM Pulse and try to understand them by your own, also try to get your hand on some demos, because that is the best way to learn.  
Now, the next time you'll be at the airport, you'll know how it works ;)
Have a good day and keep learning.
