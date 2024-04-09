**AWS S3 Bucket Policy Exploration.**<br>
STEP 1 : Login to AWS management console navigate to S3 or search S3 on the search bar and create a s3 bucket.<br>
STEP 2 : Create a JASON- formatted bucket policy on the management console by clicking on the bucket you created, click on permission then click on Edit block public access and allow.<br>
Scroll down you will see bucket policy click on edit. At the right hand side click on generate policy select the policy type(s3 bucket) add principal copy and paste the resource then click generate policy.<br>
STEP 3 : **Testing**<br>
Copy and paste the generated policy on your s3 bucket and click save changes.<br>
Create a photo/image folder and upload a photo, and copy the URL link on a new web browser click Enter . it will display your image.<br>
If you've assigned S3 to an IAM User, login the user to access S3 bucket to check if your changes has been made.<br>

**S3 Static Website Hosting**<br>
1. Create S3 bucket<br>
2. Upload static website content such as; HTML,CSS and other static content files for your website.<br>
3. Configure the bucket for static website hosting; in the s3 bucket, navigate to the **static website hosting** selection.<br>
4. Choose "use this bucket to host a webite" and configure the index document.<br>
5. Access the static website using the provide URL endpoint and verify that it displays correctly.<br>

**S3 Versioning and Replication**<br>
1. In the S3 properties navigate to versioning section and enable.<br>
2. Configure cross-region replication by navigating to management tab click on "Replication". Configure source region(your bucket region) then destination region(which is another region of your choice) then create or select IAM role for replication.<br>
3. Upload an object to test versioning,modify the object and check versioning behaviour,check the verison history of the object.<br>
4.  Verify that the object is replicated to the designated region.<br>

**S3 Bucket Policy For CloudFront Website**<br>
1. Create a S3 bucket, add a file or image.<br>
2. Configure static website hosting by navigating to properties on your bucket then click on **static website hosting** enable it and configure the index document.<br>
3. Create a cloudfront distribution . Navigate to CloudFront service on your AWS management console. Create distribution, choose **web** distribution type,configure the setting,specifing your S3 bucket as the origin.<br>
4. Click create and copy the policy that pop up.<br>
5. Configure S3b bucket policy by navigation to **permission** on your S3, click on bucket policy paste the policy from cloudfront and click make changes.<br>
6. Then copy the CloudFront distribution URL and paste on your new web browser /the image name on S3 bucket and press ENTER.<br>

**Understanding Virtual Private Cloud**<br>
Introduction to Networking: Networking is a system that allows multiple devices to communicate with one another.<br>
How to create virtual private cloud(vcp) on AWS using Aws management console: Login to your Aws management console then navigate to VCP service. Click create VPC enter vpc name and select IP range (10.0.0.0/16). Click create.<br>

**How to setup VPC,Public,Private Subnet,NAT,Internet Gateway and Route Table**.<br>
*Internet Gateway*: Go to VPC on the right hand side navigate to Internet Gateway click create internet gateway then input a name tag and click create. Click on the internet gateway you create then go to Actions then you will see Attached to VPC option,click it then select the VPC you created and click attached.<br>
*Public and Private Subnet*: Navigate to vcp dashboard then click on Subnet then click on create subnet, select vpc you created then create a subnet name (test-public-1a),select the available Zone/region then specify the IP range based between the range you use for your VPC 10.0.0.0/24 then click create subnet. Repeate same process to create public subnet But select a different Ip 10.0.1.0/24.<br>
*Route Table*: On your vpc dashboard on the left hand side click on click route table, click create route table. Select a name for public then put a VPC(must be the one you created) then click on create route table . Repeate same process to create private route table as well. But to  create a route table is not enough you have to enable the route to access the internet by associating it with internet gateway.<br>
*To Do That*: Click on edit route then click on Add route and select Ip (0.0.0.0/0) to enable access to the internet publicly then select TARGET(Internet Gateway) the igway you created. Click save changes.<br>
For private route table you just gonna assiocate it with subnet association. Click on subnet assiociation then select private and save changes.<br>
**Creating An EC2 instance into the Pubic Route**<br>
1. Go to AWS management console, click on EC2 instance and Launch an instance . Create a name for your instance(test-ec2-public-sub-instance) choose ubuntu and create a key pair if you dont have one then **Edit** Networking setting . Choose the VPC you created and choose te public subnet your created as well.Then **Enable** Auto Assign Public IP then you name a security group(test-ec2-SG).<br>
2. Then click on Launch instances.<br>
3. Then you SSH into the running instance: open the "key.pem" you generate from your instance then copy the SSH connect link from your instance then in your terminal then press ENTER.<br>
   **Deploying ALB(Application Load Balancer) On Two EC2 Instances**<br>
   STEP 1. Create a **VPC**<br>
   On your AWS navigate to VPC click create vpc select IP range 12.0.0.0/16.Then click create vpc.<br>
   Create **Internet Gateway And Attach To Vpc**<br>
   Click on vpc dashboard navigate to Internet Gateway, click create internet gatwway specify a *Name tag* and click on create internet gateway.<br>
   On the internet gateway click on *Action* go to *Attach VPC* then select the vpc you created then click Attached to internet gateway.<br>
   Create **Public Subnet**<br>
   On Vpc dashboard navigate to *Subnet* click create subnet, select the vpc created then select the 1a public subnet name ,select a zone and specify the IP range 12.0.1.0/24. Create the second 1b public subnet specifing the IP range 12.0.3.0/24 following same step and click create subnet. so that **Two** EC2  instacnce can be created so we can load balamce traffic into the two EC2 instance.<br>
   Create **Route Table**<br>
   Navigate  to route table click create and specify a route name, select th vpc you create then click create route table. On the route table click subnet association then click *Edit subnet association* then select the two public subnet created and click *Save association*. Inside the route table click on **Route** then click *edit route* specify the IP range 0.0.0.0/0 (which means it will have an internet access and anyone can have access to those public subnet) then select internet gateway you created then click save changes.<br>
STEP 2 . Create **TWO EC2 INSTANCE**<br>
On AWS management navigate to EC2 click launch instance then specify your instance name then choose Ubuntu operating system, choose or create a key pair then *Edit Network settings* select the vpc you've created, select subnet then *Enable* Auto Assign Public IP then click on *Add security group* select HTTP and ANYWHERE then scroll down to user date and add the script/package you want to get installed into your EC2 machine. Then click on launch instance.<br>
Copy your EC2 instance ID to verify if your package is running. Follow same step to create the second EC2 instance.<br>
STEP 3. Create **TARGET GROUP**<br>
On Ec2 Dashboard navigate to Target Group click on create group input the name click on Next then select the two instances you created then click on *Incude as pending below*.Then click on create target group.<br>
Create **ALB**<br>
On EC2 dashboard navigate to *Load Balancer* click on create load balancer and select Application Load Balancer, specify a name then select the VPC you created ,then select both subnet created. Click on create security group, select a group name put a *Description* that says Allow Access From Internet, choose the VPC. Then inbound rule use (HTTP then source "Anywhere 0.0.0.0/0") then click create security group.Then go back to your Load Balancer and select the security group you created .<br>
Under Listener and Routing select a Target group you created. Click on create Load Balancer. <br>
After the Load Balancer has been created copy the DNS which wil be used to access the internet ad confirm the traffic you've created paste it on a new web browser and reload .<br>
**Configuring Auto scaling with ALB Using Launch Template**<br>
After creating your ALB, on your EC2 dashboard navigate to *Auto Scaling* click create Auto scaling group specify your group name ,click on create a lanuch template then you create an *Image of your server*. Navigate to your instance click on the instance you want then click on ACTIONS then click on image and template then cclick on create image,specify your image name then add describtion(Image for Auto Scaling Group) and click on create image. Then you go back to *Launch template* specify your template name then add description and select an **AMI** which is the image you created,select the instance type,select the key pair,select a security group(the security group you created) then click on create launch template.<br>
Then you go back to the Auto scaling page then select the template you created click on next, select the VPC you created, select the subnets you created and click next.<br>
Attached an existing load balancer, select health check then click next then select the EC2 capacity and minimum you want to be created, select *Target tracking policy* click next then click create Auto Scaling group.<br>
**Configuring Route53 With Ec2 Instance**<br>
On AWS console navigate to Route53, create a Domain name if you dont have then click on *Create Hoated Zone* inout your domain name and click create.Now to define record, click on create record choose simple routing then click next, click on define simple record then choose (IP address then copy the Elastic IP address from your ec2 and paste it there then select **A** record type then clik Define record. Create one more record which is type **c** , record name (www) then choose the IP address then paste your *domain name* then click on define record then click on create record.<br>
If you're using another domain name provider copy the NS(namespace) one by one then go to your domain provider and edit changes and paste the namespace then click save changes.<br>
TO VERIFY: Copy your domain name and paste it on a new web browser it will revolve the domain to the IP address o your EC2.<br>
**Setting Up Amazon RDS with MYSQL Engine**<br>
On your Aws management console navigate to RDS click on database, click create database and select MYSQL Engine. Configure the RDS settings, including master username and password. On the RDS instance click on connectivity, click on the security group and set the inbound rules to allow **MYSQL Traffic**.<br>
Use MYSQL client (Workbench) to connect to the RDS instance provided the Endpoint,master username and password.
