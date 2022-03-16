# AWS

Used Cloudformation to create following resources in North Virginia region:

1. VPC
- Internet Gateway
- Internet Gateway Association
- Private subnet
- Public subnet
- Public route table
- Gateway route
- Public Route table subnet association
- AWSTemplateFormatVersion: "2010-09-09"

2. Created NAT instance
- Created EC2 in Public subnet
- Created EC2 in private subnet
- Security group for NAT instance

3. Allowed all inbound traffic from private subnet
- Security group for JumpBox instance
- Allowed inbound traffic to port 22 from your public IP
- Security group for Public EC2 instance (apache web server)
- Allowed inbound traffic to port 80 from everywhere
- Allowed inbound traffic to port 22 from jumpbox
- Security group for Private EC2 instance (Mariadb server)
- Allowed inbound traffic to port 3306 from Public EC2
- Allowed inbound traffic to port 22 from jumpbox
- Jumpbox EC2 instance
- Install Apache WEB server on public EC2
- Install MariaDB on private EC2
- Modified EC2 instances with their corresponding security groups.

4. Created IAM Role for the public EC2 instance that will grant S3 Full Access
- Created Instance profile with reference to the created IAM Role
- In the public EC2, create reference to the created Instance profile
- In the public EC2 add User Data with a script that will install httpd and copy index.html from S3.

5. Configure AWS CLI
- Create S3 Bucket
- Enable Static WEB site hosting
- Prepared index.html and error.html
- Upload html files using AWS CLI
- Disable "Block public access"
- Write Resource based policy that will enable public access

6. Create a Lambda function using AWS console
- Lambda properties: Set memory to 256 MB, Set timeout to 5 sec.
- Examine the role taht is assigned to the lambda function
- Create a test event as it comes from S3
- Execute the lambda with created test event
- Examine the cloudwatch log
- Took the lambda code in a local file and open it in VS Code
- Updated the code to output the event object in the response body
- Zip the code and upload it to the lambda function to update it.
