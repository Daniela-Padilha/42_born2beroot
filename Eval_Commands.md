## 1. Does your VM have a graphical interface (GUI)?
```ls /usr/bin/*session```

Answer: if the output only shows: ```/usr/bin/dbus-run-session```, it means you don't have a GUI.

## 2. Is UFW active?
```sudo service ufw status```

Answer: you should see "status: active" written in green in the output.

## 3. Is SSH active?
```sudo service ssh status```

Answer: you should see "status: active" written in green in the output.

## 4. Which OS are you using?
```uname -v```

uname -v --> unix name version

Answer: it should display either Debian or Rocky.

## 5. Is the user in the right groups?
```getent group sudo```

```getent group user42```

getent --> get entries

Answer: username.

## 6. Create a new user and pass
```sudo adduser newuser```

Answer: password updated successfully.

## 7. Create a new group named "evaluating".
```sudo addgroup evaluating```

Answer: done.

## 8. Add newuser to evaluating group
```sudo adduser newuser evaluating```

to verify: ```getent group evaluating```

Answer: newuser.

## 9. Check the hostname.
```hostname```

Answer: username42.

## 10. Change hostname.
```sudo vim /etc/hostname``` and replace

``` sudo vim /etc/hosts``` and replace

```sudo reboot```

```hostname```

Answer: new hostname.

## 11. Partitions.
```lsblk```

lsblk --> list block devices

Answer: matches the subject.

## 12. Is SUDO active?
```which sudo```

## 13. New user in SUDO group
```sudo adduser newuser sudo```

```getent group sudo```

Answer: newuser.

## 14. See rules for password implementation
```vim /etc/sudoers.d/sudo_config```

```vim /etc/login.defs```

```vim /etc/pam.d/common-password```

## 15. SUDO command log
``` su```

```cd /var/log/sudo```

```ls```

```cat sudo_config```

Answer: it should have at least one file and the command log using sudo.

## 16. Is UFW active?
```sudo service ufw status```

Answer: active.

## 17. See UFW rules
```sudo ufw status numbered```

Answer: 4242.

## 18. Create new UFW rule and delete it
```sudo ufw allow 8080```

```sudo ufw status numbered```

```sudo ufw delete rule_number```

```sudo ufw status numbered```

```sudo ufw delete rule_numbered```

## 19. Is SSH active, and only open to 4242 port?
```sudo service ssh status```

Answer: active and server listening on port 4242.

## 20. Connect to SSH with the newuser
```hostname -I```

Change to terminal of the physical machine.

```ssh newuser@IP -p 4242```

```sudo service ssh status```

Do the same with the root@IP.

Answer: With the root, it should not have permissions. With newuser, it should connect.

## 21. Change Crontab script from 10 min to 1 min
```sudo crontab -u root -e```

And change the interval from 10 to 1.

## 22. Stop the script
```sudo /etc/init.d/cron stop```

Answer: stopping cron.

## 23. Restarting the script
```sudo /etc/init.d/cron start```

Answer: starting cron.
