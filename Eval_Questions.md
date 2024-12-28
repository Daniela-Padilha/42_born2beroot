## 1. Clone your VM
Open the VM VirtualBox Manager, click on your VM with a rigth mouse click and choose Clone.
Select your Clone and start it.
This is were you are going to do the evaluation, never start your original VM after you have submitted your project.
If you do your signature.txt will no longer coincide with the one on your original VM.

## 2. Compare the signatures
In your pshisycal machine's terminal write:
``` shasum vmname.vdi ```

It will generate your machine's signature in the terminal.
Then clone your repository, and open the .txt file.
The easiest approach is to copy the signature from the terminal, do a ctrl+f in the .txt file and paste the signature.
It will check if it is a correct match with the original one inside the .txt file.

## 3. What is a VM and why is it usefull?
A Virtual Machine (VM) is a software that simulates an operative system (OS) and executes programs like a real machine. 
It allows the creation of severall different OS from one single phisycal hardware system, having an independent environment from the OS of the physical machine.
This is great to perform tests in a safe way. And it also brings finnancial benefits for companies.

## 4. Why did you choose Debian? Or Why did you choose Rocky?
Debian is easier for learners as it requires very little administration. It is also more stable and it offers a bigger support community.
Rocky is more enterprise oriented, it ir more regularly updated, which allows access to more recent software. 
Rocky uses SELinux which is more flexible and robust then AppArmor.
Rocky also uses dnf which is also more flexible and efficient then apt.

## 5. Apt Vs Aptitude
Apt is a package management tool, it comeas as default in Linux, and it doens't have graphycal interface.
Aptitude is an improved version of apt, it has graphycal interface and it allows resolution of package conflicts, is richer in functionalities.

## 6. AppArmor
Its a linux security model (LSM) from kernel that allows the admin to restrict the permissions and capabilities of programs.
Trought the creation of profiles of enforcement or complain.
Complain mode: only registers the violation attempts.
Enforcement mode: registers and imposes the rules set to the profile.

Ps: Kernel it's a central component of the OS of most machines.

## 7 LVM
Its a logical volume manager. It provides tools to create virtual block devices from physical devices.
It's more flexible than the conventional partition schemes for volume storage. Memory manager.

## 8. UFW
Firewall management tool. Uncomplicated firewall (UFW) allows you to control and monitor incoming and outgoing network traffic.
It decides if it allows or blocks specific traffic based on the safety rules applied.

## 9. SUDO
Substitute user do (SUDO).
SUDO basically does the same that the su (select user) command does, it allows you to change user into root, using a password.
The big difference is that with SUDO after 5 min of inactivity it will prompt you again for a password.
With su the account stays active until the user changes it again, which can be risky in terms of security.

## 10. SSH
Secure shell (SSH).
It's a network cryptography protocol, that encrypts every communication between a client and a server.
This allows safe access and remote management of computers trought a network.

## 11. Crontab
Chronos (the greek god of time) table.
It's a manager of background processes. 
It allows you to schedule a task that automates the execution of commands or scripts in a time interval.

