**AWS S3 Bucket Policy Exploration.**<br>
STEP 1 : Login to AWS management console navigate to S3 or search S3 on the search bar and create a s3 bucket.<br>
STEP 2 : Create a JASON- formatted bucket policy on the management console by clicking on the bucket you created, click on permission then click on Edit block public access and allow.<br>
-Scroll down you will see bucket policy click on edit. At the right hand side click on generate policy select the policy type(s3 bucket) add principal copy and paste the resource then click generate policy.
STEP 3 : **Testing**<br>
-Copy and paste the generated policy on your s3 bucket and click save changes.<br>
-Create a photo/image folder and upload a photo, and copy the URL link on a new web browser click Enter . it will display your image.<br>
-If you've assigned S3 to an IAM User, login the user to access S3 bucket to check if your changes has been made.
