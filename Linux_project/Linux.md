**Bash Script For Generating A Multiplication Table**<br>
#!/bin/bash<br>
echo"Enter a number<br>"
read n<br>
**Validation**
if [ $n -gt 10] || [ $n -lt 0 ];then<br>
echo"Number out of range"<br>
exist 1<br>
fi<br>
**Part 1**: **Using List Form For Loop**<br>
echo"select **F** for full multiplication table or select **P** for partial table:"<br>
read choice<br>
if [ "$choice == "f" ];then<br>
echo"Full multiplication Table for $n"<br>
for ((i=i; i<=1o ;i++));<br>
do<br>
b=$((n*i))<br>
echo"$n*$i=$b"
done<br>
**Part 2**: **Using The C-Style Loop**<br>
elif ["$choice" == "p" ];then<br>
echo"Enter the starting number between 1 and 10:"<br>
read start<br>
echo"Enter the ending number between 1 and 10:"<br>
read end<br>
echo"The partial multiplication table for $n from $start to $end:"<br>
for ((i=start; i<=end ;i++))<br>
do<br>
b=$((n*i))<br>
echo"$n*$i=$b"<br>
done<br>
else <br>
echo "invalid range. Showing full multiplication table of $n instead"<br>
fi






