# AWS Study Guide

## IAM (Identity Accesss Management)
Allows you to manage users and their level of access to the aws console

### Key Terms
* **Users** - end users (people)
* **Groups** - collection of users under a single set of permissions
* **Roles** - create roles and assign them to aws resources
* **Policies** - a document that defines one or more permissions (JSON)

IAM is global, not tied to a specific region.  
Users are given a url link to sign in, found in IAM console.

**Root Account** - email used to sign up with aws, unlimited access to all aws resources.
  - should enable multifactor authentication

### User Access Types
1. **Programmatic** - cli or sdk (access key id, secret access key)
2. **AWS Management Console** - web portal (username, password)

Secret access key can only be viewed once and credentails can be set to inactive.  
Can generate new access key id and secret access key.

Can add permissions to groups or individual users.

Can create a password policy that has rules for password creation and frequency or rotation.

### What are IAM Roles
A way to give permissions to entities that you trust.  
Entities include: 
* IAM user in another aws account
* Application code on EC2 that performs actions on aws resources
* AWS services that need to act on resources to perform their function
* Users from corporate directory using id federation

## STS (Security Token Service) 
Grants users temporary access to aws resources.  
Users can come from 3 sources:
1. Federation (typically with Active Directory)
2. Federation with mobile apps (Facebook, Google)
3. Cross account access

**Federation** - combining or joining a list of users in one domain (such as IAM) with users in another domain (such as Active Directory, Facebook, etc)

**Identity Broker** - a service that allows you to take an identity from point A and join it (federate it) to point B

**Identity Store** - services like Active Directory, Facebook, Google

**Identites** - a user of a service like Facebook
