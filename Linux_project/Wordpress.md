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


