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
6. Then copy the CloudFront distribution URL and paste on your new web browser /the image name on S3 bucket and press ENTER.

