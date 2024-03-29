**Ecommerce platform deployment with Git, Linux and Aws.**<br>
Open my git terminal to create a project name  **"mkdir Marketpeak_Ecommerce"** then cd *"Marketpeak_Ecommerce"* then "git init"<br>
Download Ecommerce website template @Tooplate then i Extract the downloaded Template into Marketpeak_Ecommerce directory(right click on the downloaded file click extract all then select Marketpeak_Ecommerce)<br>
Use (**"git add"**) (git config --global user.name Ayodeji1996) and email respectively.<br>
Then "git commit -m "initial commit with basic e-commerce site structure".<br>
**PUSH THE CODE TO GITHUB REPOSITORY**<br>
Create a git repository name "Marketpeak_Ecommerce" on GITHUB.<br>
Copy the remote repository URL on github by navigating to CODE, click on it to select the http URL then copy.<br>
On your terminalt "git remote add origin" then paste the remote repository URL and push code "git push -u origin main"<br>
STEP 2 : **Aws Deployment**<br>
login to Aws Management console<br> 
launch an EC2 instance using Amazon Linux AMI<br>
Then navigate to the connect button click on EC2 then click connect.<br>
Clone the repository from GITHUB on Linux server using the HTTPS. <br> 
Navigating to CODE on GITHUB and copy the https option<br>
Then on my git terminal i run "git clone then paste the https address then press Enter"<br>
STEP 3 : **Install Web Server on EC2.**<br>
On EC2 instance install APACHE webserver (httpd) for HTML files run "sudo su -" then "yum update -y" then "sudo install httpd" then "systemctl status httpd" then "systemctl enable httpd.
STEP 4 :
CONFIGURE HTTPD FOR WEBSITE:
To do that i run "mkdir Marketpeak_Ecommerce" then  "cd Marketpeak_Ecommerce" 
then "wget https://github.com/Ayodeji1996/MarketPeak_Ecommerce.git" then i run "ls -lrt" to see if the files are there.
Then i run "wget ( my remote repository ZIP)" iF you navigate to CODE on your GITHUB click on the code then you will see DOWNLOAD ZIP.
After that i run "ls -lrt command again"' there it shows that my website template have been added and saved as "Main" 
then i run the command "unzip main" to add all the files in "Main" to Marketpeak_Ecommerce. 
then i run "ls -lrt" and i see "Marketpek_Ecommerce-main" then i run "cd Marketpeak_Ecommerce-main"
Then i run ls -lrt command and it shows list of  in HTML.
then i run mv * /var/www/html/ because it is a directory structure on Linux system that host web content particularly for APCHE HTTP SERVER.
then run cd /var/www/html, then i run 'ststemctl reload httpd".
Then i opened a web browser to access my copied Ec2 instance ip address and the website was deployed.
TO ENSURE CONTINUOUS INTEGRATION AND DEPLOYMENT WORKFLOW :
On git terminal i changed directory "cd Marketpeak_Ecommerce"
then create a new development branch and checkout with command "git checkout -b development" .This command created a new branch and change directory to the new branch
Then i run "cd Marketpeak_Ecommerce" then i run "ls -l" to see whats in there . 
Then i created a file with the command "touch file1.txt. 
Then "echo 'my new changes to my repo' > file1.txt. 
Then cd.. which takes me back the development branch i created.
Then i go back to my GITHUB account to pull, commit and merge the request/changes.
To test my changes i open my EC2 instance terminal and run "systemctl reload httpd" 
then open a new web browser and refresh my EC2 ip address again.












