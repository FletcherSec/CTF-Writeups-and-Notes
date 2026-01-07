Identity and Access Management

Global Service

Root Account created by default, shouldnt be used or shared

Users are people within your organization and can be grouped

Users dont have to belong to a group, and users can belong to multiple groups

##### IAM Permissions
- Users or Groups can be assigned JSON documents called policies
- Policies define th e permissions of the users
- Apply [[Least Privilege Principle]] 

#### Permissions
- Not best practice to use root user; better to make admin accounts to manage from

##### Multi-session Support
- Allows you to sign into multiple user sessions within the same browser

##### Inline Policies
- Applied to users instead of groups
![[Pasted image 20251124104927.png]]

##### Attaching Policies Directly
- Going to the user and adding permissions via "Attach Policies Directly" you can specify a permission like "IAMReadOnlyAccess" to list Users in the AWS Console (And read anything in IAM)

[[IAM Roles for Services]]