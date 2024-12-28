# Important
This is not a tutorial on how to do the project Born2beRoot, but a mere explanation of the commands and concepts to be known during evaluation.

## 1. Clone your VM
Open the VM VirtualBox Manager,  right-click on your VM, and choose "Clone".

Select your cloned VM and start it.

This is where you will perform the evaluation. Never start your original VM after you have submitted your project.

If you do, your ```signature.txt``` will no longer match the one on your original VM.

## 2. Compare the signatures
In your physical machine's terminal type:

``` shasum vmname.vdi ```

This will generate your machine's signature in the terminal.
Then, clone your repository and open the ```.txt``` file.

The easiest approach is to copy the signature from the terminal, press ```Ctrl+F``` in the ```.txt``` file, and paste the signature.

This will check if it matches the original signature inside the ```.txt``` file.


## 3. What is a VM and why is it usefull?
A Virtual Machine (VM) is software that simulates an operating system (OS) and executes programs like a real machine.

It allows the creation of several different OS environments on a single physical hardware system, providing an independent environment from the OS of the physical machine.

This is great for performing tests safely. It also provides financial benefits for companies.


## 4. Why did you choose Debian? Or Why did you choose Rocky?
Debian is easier for learners as it requires minimal administration. It is also more stable and has a larger support community.

Rocky is more enterprise-oriented and is updated more regularly, allowing access to more recent software.

Rocky uses SELinux, which is more flexible and robust than AppArmor.

Rocky also uses ```dnf```, which is more flexible and efficient than ```apt```.

## 5. Apt Vs Aptitude
Apt is a package management tool that comes by default in Linux. It does not have a graphical interface.

Aptitude is an improved version of Apt, with a graphical interface. It also allows the resolution of package conflicts and offers more functionality.

## 6. AppArmor
AppArmor is a Linux Security Module (LSM) in the kernel that allows the admin to restrict the permissions and capabilities of programs.

This is done through the creation of profiles in either enforcement or complain mode.

Complain mode: only registers violation attempts.

Enforcement mode: registers and enforces the rules set in the profile.

Note: The kernel is a central component of the OS in most machines.

## 7 LVM
LVM (Logical Volume Manager) is a tool that provides virtual block devices from physical devices.

It is more flexible than traditional partition schemes for volume storage and works as a memory manager.

## 8. UFW
UFW (Uncomplicated Firewall) is a firewall management tool that allows you to control and monitor incoming and outgoing network traffic.

It decides whether to allow or block specific traffic based on the security rules applied.

## 9. SUDO
SUDO (Substitute User Do) is a command that allows you to execute commands with the privileges of another user, usually the root user, by entering a password.

The key difference between SUDO and ```su``` is that with SUDO, after 5 minutes of inactivity, it will prompt you for the password again.

With ```su```, the account stays active until the user switches or logs out, which can pose a security risk.

## 10. SSH
SSH (Secure Shell) is a network cryptography protocol that encrypts all communications between a client and a server.

This enables secure access and remote management of computers over a network.

## 11. Crontab
Crontab (from the Greek god of time, Chronos) is a manager for background processes.

It allows you to schedule tasks to automate the execution of commands or scripts at specific time intervals.

