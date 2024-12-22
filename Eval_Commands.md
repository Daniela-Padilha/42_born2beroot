## 1. Does your VM have a graphical interface (GUI)?
```ls /usr/bin/*session```
Answer: if the output only shows: ```/usr/bin/dbus-run-session``` it means you don't have a GUI.

## 2. Is UFW active?
```sudo service ufw status```
Answer: you should see "status: active" written in green in the output.

## 3. Is SSH active?
```sudo service ssh status```
Answer: you should see "status: active" written in green in the output.

## 4. Which OS are you using?
```uname -v```
Answer: it should display Debian or Rocky.
