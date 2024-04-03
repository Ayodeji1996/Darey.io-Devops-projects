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
3. Then you SSH into the running instance: open the "key.pem" you generate from your instance then copy the SSH connect link from your instance then in your terminal then press ENTER. 

