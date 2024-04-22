**Wordpress Site On Aws with Loadbalancing And Autoscaling Using EFS and MYSQL**<br>
VPC SETUP:<br>
1) create VPC using ip range 10.0.0.0/20<br>
2) create public subnet using ip range 10.0.0.0/24 and private subnet ip 10.0.1.0/24<br>
3) configure both public andd private route table and associate public RT with public subnet and configure a NAT gateway for private access<br>
4) create internet gateway and attach with VPC<br>
5) Edit public Route to target internet gateway Ip 0.0.0.0/0 and private route to target instance.<br>
LAUNCH 2 EC2 INSTANCE<br>
1) On the instance configure the Network Vpc and subnet to the one you created<br>
2) onfigure security All Traffic Everywhere ip 0.0.0.0.0/0 and launch the first instance<br>
CREATE EFS(Elastic Ip)<br>
1) Navigate to Efs on your dashboard click alloacte Ip address then click Allocate and associate it to Ec2 instance launched<br>
CREATE SECURITY GROUPS<br>
On your dashboard navigate to security group create new inbound rules for the following ;<br>
a) Web-public sg and web private sg; Type: HTTP and HTTPS and SSH, Protocol: TCP, Port Range: 80/443/22, Source: Anywhere<br>
b) Loadbalancer sg; Type: HTTP and HTTPS , Protocol: TCP, Port Range: 80/443, Source: Anywhere<br>
c) EFS sg; Type: NFS , port Range: 2049, source: web-public sg and web-private sg<br>
d) RDS sg; Type: MYSQL, port Range: 3306, source: web-public sg and web-private sg<br>
CREATE RDS<br>
Navigate to RDS on your Aws dashboard create Amazon RDS instance with MYSQL Engine. Select the RDS security group created .<br>
Navigate to EFS and configure security group to the EFS-Sg created and click create file system.<br>
CREATE *Master Ec2 instance for installation of Web Server*<br>
1) On the instance configure the Network Vpc and subnet to the one you created and select the *Web-public-Sg* from existing security group after the instance has been launched navigavte to *Elastic IP* and allocate Ip address and associate it with the instance.<br>
WORDPRESS SETUP ON MASTER SERVER<br>
a) SSH into the master instance and run the following command;<br>
sudo -i (To change to root)<br>
apt -get update (To update applicaions)<br>
mkdir -p /var/www/html(To make a directory)<br>
sudo mount -t nfs4 -o nfsvers=4.1,rsize=1048576,wsize=1048576,hard,timeo=600,retrans=2,noresvport fs-46fb70c4.efs.us-east-1.amazonaws.com:/ /var/www/html(To mount EFS to EC2 instance)<br>
df -h(To check if it has been mount)<br>
vim /etc/fstab (fs-46fb70c4.efs.us-east-1.amazonaws.com:/ /var/www/html nfs4 -o nfsvers=4.1,rsize=1048576,wsize=1048576,hard,timeo=600,retrans=2 0 0). To permanently mount files.<br>
b) yum install -y httpd24 php73 mysql57 php73-mysqlnd php73-opcache<br>
service httpd start<br>
chkconfig httpd on<br>
usermod -a -G apache ec2-user<br>
sudo chown -R ec2-user:apache /var/www<br>
sudo chmod 2775 /var/www<br>
c) Download Wordpress, Unzip And Move It to HTML Directory<br>
wget https://wordpress.org/latest.tar.gz<br>
tar -xzf latest.tar.gz<br>
cp -r wordpress/* /var/www/html/<br>
d) cp /var/www/html/wp-config-sample.php /var/www/html/wp-config.php(Create wp-config.php file)
e) vim /var/www/html/wp-config.php(Open it in vim editor or Nano); Edit the *database name*, *Username*, *Password* and *hostname/RDS Endpoint* information to the RDS instance to connect wordpress with RDS .Then save<br>
f) Go to your EC2 instance copy the public IP and paste it on your browser to access wordpress site and fill in your information then click *Install wordpress*. After installation enter yout username and password to login.<br>
CREATE ALB AND AUTOSCALING <br>
On EC2 dashboard navigate to Load Balancer click on create load balancer and select Application Load Balancer, specify a name then select the VPC you created ,then select both subnet created. Click on create security group, select a group name put a Description that says Allow Access From Internet, choose the VPC, choose security group and create a new target group using MASTERSERVER INSTANCE for wordpress and click create ALB. After the Load Balancer has been created copy the DNS paste it on a new web browser and reload you will be able to access your wordpress site.<br>





