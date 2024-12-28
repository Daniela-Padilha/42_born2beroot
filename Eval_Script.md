# Important
This is not a tutorial on how to do the project Born2beRoot, but a mere explanation of the commands and concepts to be known during evaluation.

## What is a Script?
It's a sequence of commands stored in a file.

## Arch
Is the architecture of the OS.

```uname -a```


```Uname``` --> unix name, and -a means all, so we are going to see all the information of the OS.

## CPUF
It will show the number of physical nuclei of the CPU.

```grep "physical id" /proc/cpuinfo | wc -l```


```Grep``` --> means globally search for a regular expression and print it, so we are going to look into the file 
/proc/cpuinfo which will tell us information about the processor, and search for "physical id".

```wc -l``` --> means word count, with the -l flag to count how many lines inside that file have the words
"physical id" .

## CPUV
It will show the number of virtual nuclei of the CPU.

```grep "processor" /proc/cpuinfo | wc -l```


Same thing as before, but here we want to know how many lines have the word "processor" in them.

## RAM
It will show how much RAM we have in total, how much of it is being used in megabytes and in percentage.

ram_total = ```free --mega | awk '$1 == "Mem:" {print $2}'```

ram_use = ```free --mega | awk '$1 == "Mem:" {print $3}'```

ram_percent = ```free --mega | awk '$1 == "Mem:" {printf("%.2f"), $3/$2*100}'```



```Free --mega``` --> will show the memory usage in megabytes, as the subject asks.

```Awk``` --> is a script language that processes data based on ```.txt``` files.

```$1 == "Mem:"``` --> check if the first word of a line is equal to "Mem:".

```{print $2}``` --> print the second word ($3 or the third word) of that line.

```{printf("%.2f"), $3/$2*100}``` ---> print the result of memory used/total memory * 100, as a float with two decimal cases.

## DISK
It will show how much disk memory we have in total, how much of it is being used in megabytes and in percentage.

disk_total = ```df -m | grep "/dev/" | grep -v "/boot" | awk '{disk_t += $2} END {printf ("%.1fGb\n"), disk_t/1024}'```

disk_use = ```df -m | grep "/dev/" | grep -v "/boot" | awk '{disk_u += $3} END {print disk_u}'```

disk_percent = ```df -m | grep "/dev/" | grep -v "/boot" | awk '{disk_u += $3} {disk_t+= $2} END {printf("%d"), disk_u/disk_t*100}'```


 ```df -m``` --> show info about the usage of disk memory in megabytes.

```grep "/dev/" | grep -v "/boot"``` --> looks for all the lines that have "/dev/" and all the lines that don't have "/boot".

```awk '{disk_t += $2} END {printf ("%.1fGb\n"), disk_t/1024}'``` --> we will add the value of the second word of each line and save it in ```disk_t```
We divide that variable by 1024 (the number of bits in one byte) to trasform the result into Gb. The code after the ```END``` is executed only one time 
after all the input is read.

## CPU LOAD
Shows the number of tasks waiting for CPU time.

cpul = ```vmstat 1 2 | tail -1 | awk '{printf $15}'```

cpu_op = ```expr 100 - $cpul```

cpu_fin = ```printf "%.1f" $cpu_op```


```vmstat 1 2``` --> virtual memory statistic reporter, it will set the interval between two updates to one second, and it will print only two updates.

```tail -1``` --> prints the last line of the input.

```awk '{printf $15}'``` --> prints only the 15th word of the last line, which will be the percentage of CPU usage.

```expr 100 - $cpul``` --> handles both integer and string values, it will calculate the remaining percentage of unused CPU, by subtracting the cpul from the total (100).

```printf "%.1f" $cpu_op``` --> it prints the result with one decimal case.


## LAST BOOT
Shows the last time the system was rebooted.

lb = ```who -b | awk '$1 == "system" {print $3 " " $4}'```


```who -b``` --> shows the date, time and extra info about the last boot.

```awk '$1 == "system" {print $3 " " $4}'``` --> if the first word of the line is ```"system"```, it will print the third word, a space and the fourth word.

## LVM USE
Checks if the LVM is active.

lvmu = ```if [ $(lsblk | grep "lvm" | wc -l) -gt 0 ]; then echo yes; else echo no; fi```


```lsblk``` --> checks all the info about memory blocks.

```grep "lvm" | wc -l``` --> counts the number of lines where "lvm" appears.

```if...then...fi``` --> if the number of lines is greater than zero print yes, if not print no, and end the condition.


## TCP CONNEXIONS
Check how many transmission control protocol connexions are established.

tcpc = ```ss -ta | grep ESTAB | wc -l```


```ss -ta``` --> socket statistics, check all the tcp sockets.

```grep ESTAB | wc -l``` --> Count how many are established.

## USER LOG
Show how many users exist.

ulog = ```users | wc -w```


```users``` --> shows the usernames.

```wc -w``` --> counts how many users there are.

## NETWORK
SHows the IP and MAC addresses.

ip = ```hostname -I```

mac = ```ip link | grep "link/ether" | awk '{print $2}'```


```hostname -I``` --> shows the IP address.

```ip link``` --> shows the network interfaces.

```grep "link/ether" | awk '{print $2}'``` --> finds the line with the MAC address and prints it.

## SUDO
SHows the number of commands executed using SUDO.

cmnd = ```journalctl _COMM=sudo | grep COMMAND | wc -l```

```journalctl _COMM=sudo``` --> access the log information of several sources, and filter the entries specifying the path to sudo. _COMM is to look for executable scripts.

```grep COMMAND | wc -l``` --> count how many lines have the word COMMAND on them.

## Wall
Write to all, displays the contents of the script to all logged-in users.

```wall "	Architecture: $arch
	CPU physical: $cpuf
	vCPU: $cpuv
	Memory Usage: $ram_use/${ram_total}MB ($ram_percent%)
	Disk Usage: $disk_use/${disk_total} ($disk_percent%)
	CPU load: $cpu_fin%
	Last boot: $lb
	LVM use: $lvmu
	Connections TCP: $tcpc ESTABLISHED
	User log: $ulog
	Network: IP $ip ($mac)
	Sudo: $cmnd cmd"```
