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
