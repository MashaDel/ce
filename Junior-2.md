# Cloud-simply Engineering Curriculum
Level: `Junior 1` | `Elementary`

---
### Exercise 1
Create a new AWS (***Amazon Web Services***) account (and account root user)
  | [text](https://aws.amazon.com/premiumsupport/knowledge-center/create-and-activate-aws-account/)
  | [video](https://www.youtube.com/watch?v=v3WLJ_0hnOU)
<details><summary>Show details</summary>

* **What we have as a result (to check/validate)**
  * AWS account root user credentials: email, password; 12-digit AWS account ID
</details>

---
### Exercise 2
Sign in to AWS Console (***AWS Management Console***) as an account root user	
  | [text](https://docs.aws.amazon.com/IAM/latest/UserGuide/console.html#root-user-sign-in-page)
<details><summary>Show details</summary>

* **What we have as a result (to check/validate)**
  * Access to AWS Cloud resources under the account root user via web interface
</details>

---
### Exercise 3
Create first IAM admin user
  | [text](https://catalog.us-east-1.prod.workshops.aws/workshops/13304db2-f715-48bf-ada0-92e5c4eea945/en-US/020-landingzone/prepare/aws-side/30-create-user)
  | [video](https://www.youtube.com/watch?v=wRzzBb18qUw)
<details><summary>Show details</summary>
  
* **Details**
  * Use AWS Console
* **What we have as a result (to check/validate)**
  * (First) IAM admin user credentials: username, password, access key ID, secret access key 
</details>

---
### Exercise 4
Install AWS CLI (***Command Line Interface***) for local Linux/MacOS
  | [text](https://docs.aws.amazon.com/cli/latest/userguide/install-cliv2.html)
  | [text](https://catalog.us-east-1.prod.workshops.aws/workshops/13304db2-f715-48bf-ada0-92e5c4eea945/en-US/020-landingzone/prepare/local-side/10-aws-cli)
<details><summary>Show details</summary>
  
* **What we have as a result (to check/validate)**
  * AWS CLI (`aws` command) is available in local environment  
</details>

Setup AWS credentials for local Linux/MacOS shells
  | [text](https://catalog.us-east-1.prod.workshops.aws/workshops/13304db2-f715-48bf-ada0-92e5c4eea945/en-US/020-landingzone/prepare/local-side/11-aws-profile)
<details><summary>Show details</summary>
  
* **What we have as a result (to check/validate)**
  * AWS CLI in local environment is configured with access to the created AWS account resources under the IAM admin user	 
</details>

---
### Exercise 5
Sign in to AWS Console as an IAM admin user
  | [text](https://catalog.us-east-1.prod.workshops.aws/workshops/13304db2-f715-48bf-ada0-92e5c4eea945/en-US/020-landingzone/prepare/aws-side/40-sign-in-iam)
  | [text](https://docs.aws.amazon.com/IAM/latest/UserGuide/console.html#user-sign-in-page)
<details><summary>Show details</summary>
  
* **What we have as a result (to check/validate)**
  * Access to AWS Cloud resources under the IAM admin user via web interface
</details>

---
### Exercise 6
Create AWS Cloud9 IDE environment
  | [text](https://docs.aws.amazon.com/cloud9/latest/user-guide/create-environment-main.html#create-environment-console)
<details><summary>Show details</summary>
  
* **Details**
  * Use AWS Console
  * Set all the following Cloud9 IDE environment settings as default
	  * Environment type, Instance type, Platform, Cost-saving setting, Network settings
* **What we have as a result (to check/validate)**
  * Cloud9 IDE environment is created and configured with access to the created AWS account resources under the IAM admin user	
</details>

---
### Exercise 7
Create (first) IAM admin group; place the current (first) IAM admin user into the created IAM admin group; remove `AdministratorAccess` policy from the current IAM admin user	
  | [text (Console)](https://docs.aws.amazon.com/IAM/latest/UserGuide/getting-started_create-admin-group.html)
<details><summary>Show details</summary>
  
* **Details**
  * Use AWS Console
* **What we have as a result (to check/validate)**
  * No `AdministratorAccess` policy is directly assigned to the current (first) IAM admin user permissions, but the user has administrative access to the created AWS account resources
</details>

---
### Exercise 8
Repeat the above exercise but by using AWS CLI and for another user and group — create (second) IAM admin group and (second) IAM admin user by placing it into the (second) IAM admin group
  | [text (AWS CLI)](https://docs.aws.amazon.com/IAM/latest/UserGuide/getting-started_create-admin-group.html)
<details><summary>Show details</summary>
  
* **Details**
  * Use AWS CLI
* **What we have as a result (to check/validate)**
  * (Second) IAM admin user credentials: username, password, access key ID, secret access key
</details>






...

---
### Exercise X
ExerciseDescription
  | [text](url)
  | [text](url)
<details><summary>Show details</summary>
  
* **Details**
  * DetailsDescription
* **What we have as a result (to check/validate)**
  * ResultDescription
</details>
