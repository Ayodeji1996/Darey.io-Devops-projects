cat /etc/shells:To view the numbers of shell command your ubuntu operating system support.<br>
cd /: To change directory e.g cd desktop/.<br>
touch: To create a file.<br>
ls -al: To check the file created and the permission it has.<br>
chmod +x: To change permission of a script to execute.<br>
echo: To print a command.<br>
#: Signifies a comment in a script e.g #this is a multiplication table.<br>
**Using Variables**
echo $BASH is an example of system variable: It print system information e.g $BASH_VERSION, $HOME.<br>
name=Mark: Is an example of user define variabe e.g echo $name or echo my name is $name.<br>
read -p: Allows you to enter input on same line.<br>
read -sp: Allows you to enter silent password.<br>
read -a: Allows you to extrat input in arrays.<br>
**Passing Arguement To Bash Script**<br>
echo $1 $2 $3 ' < echo $1 $2  $3 ' . IF you add $0 it will also show the name of shell script.<br>
**IF Statement Integers**<br>
-eq: is equal to [$a -eq $b]
