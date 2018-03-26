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

Roles are more secure than using access keys for resources in aws  
If not using an aws resource to access other aws resources than you need the key

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

## EC2 (Elastic Compute Cloud)
Web service that provides resizable compute capacity in the cloud.  
Allows for quick scaling up and down.

### Pricing
1. **On Demand** - allows you to pay a fixed rate by the hour or second with no commitment
  * Users want low cost and flexibility without up front payment
  * short term, unpredictable workloads that cannot be interrupted
  * testing app for first time
2. **Reserved** - sign a 1 to 3 year contract at a discount, some up front or all
  * steady state or predicatable usage 
  * get discount
3. **Spot** - enable you to bid whatever price you want for instance capacity
  * flexible start and end times
  * only feasible at very low compute prices
  * if you terminate the instance you pay for the hour
  * if aws terminates the instance because price gone above bid, free
4. **Dedicated Host** - get a physical EC2 server for you to use, no multi-tenant
  * good for license issues
  * can be on demand or reserved
  
### Instance Types
**D2** - Dense storage, Hadoop, data warehousing  
**R4** - Memory optimized, memory intensive Apps/DBs  
**M4** - General purpose, Application servers  
**C4** - Compute optimized, CPU intensive apps  
**G2** - Graphics intensive, Video encoding, 3D  
**I2** - High speed storage, NoSQL, data warehousing  
**F1** - Field programmable gate array, Hardware acceleration  
**T2** - Lowest cost general purpose, web servers, small DBs  
**P2** - Graphics, general purpose GPU, Machine learning, Bit Coin mining  
**X1** - Memory optimized, Apache Spark  

**DrMcGiftPx**

## EBS (Elastic Block Store) 
Allows you to create storage volumes and attach them to EC2 instances.  
Once attached you can create a filesystem, run a database, or use them in any other way you would use a block device

Volumes are placed in a specific AZ where they are automatically replicated to protect you from failure 

You cannot mount 1 EBS volume to multiple EC2 instances, instead use EFS

### Volume Types
1. General Purpose SSD (GP2)
  * general purpose balances both price and performance
  * 3 IOPS per gig up to 10,000 IOPS
2. Provisioned IOPS SSD (IO1)
  * above 10,000 IOPS
  * up to 20,000 IOPS per volume
3. Throughput Optimized HDD (ST1)
  * large amount of sequential data
  * big data (hadoop)
  * logs
  * data warehousing
  * cannot be a boot volume
4. Cold HDD (SC1)
  * lowest cost storage for infrequently accessed workloads
  * cannot be a boot volume
5. Magnetic (Standard)
  * lowest cost per gig of all EBS volume types 
  * infrequent access
  * bootable
  
## Security Groups
A virtual firewall controlling traffic to instances

You can have any number of EC2 instances in a security group  
When you first launch an EC2 instance you associate it with one or more security groups

All inbound traffic is blocked, and all outbound traffic is allowed by default when you create a security group

Specify ports and IP addresses to allow traffic on

Editing rules applies immediately

Security groups are **stateful** meaning adding inbound rules add outbound rules automatically

You can't specify traffic to deny on security groups, you only specify what is allowed 



