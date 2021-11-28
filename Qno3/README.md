# Create a file in your system. Whenever someone performs some action(read, write, execute) on that file, the event should be logged somewhere.

The Linux Auditing System helps system administrators create an audit trail, a log for every action on the server. We can track security-relevant events, record the events in a log file, and detect misuse or unauthorized activities by inspecting the audit log files. We can choose which actions on the server to monitor and to what extent. Audit does not provide additional security to your system, rather, it helps track any violations of system policies and enables you to take additional security measures to prevent them.

Firstly let’s install Aduit using the following command:
- sudo apt install auditd<br/>
  ![installing auditd](https://github.com/LF-DevOps-Intern/5_3_logging_reporting-vikram-rikeshkarma/blob/main/Qno3/snapshots/installing%20auditd.png)
- Now let’s start, enable and check the status of auditd, we just installed using the following commands:
  - `sudo service auditd start`
  - `sudo systemctl enable auditd`
  - `systemctl status auditd`<br/>
  ![enable auditd](https://github.com/LF-DevOps-Intern/5_3_logging_reporting-vikram-rikeshkarma/blob/main/Qno3/snapshots/enable%20auditd.png)
Now let’s view the audit rules:
- We can view the current set of rules using the command
  - `sudo auditctl -l`
  - It will show no rules, as we have not configured anything and its the default.
- And the current status of the audit system can be viewed using:
  - `sudo auditctl -s`<br/>
  ![audit rules](https://github.com/LF-DevOps-Intern/5_3_logging_reporting-vikram-rikeshkarma/blob/main/Qno3/snapshots/auditd%20rules.png)
There are 3 kinds of audit rules:
- Control rules: These rules are used for changing the configuration and settings of the audit system itself.
- Filesystem rules: These are file or directory watches. Using these rules, we can audit any kind of access to specific files or directories.
- System call rules: These rules are used for monitoring system calls made by any process or a particular user.
For this task we will be configuring FILE SYSTEM RULES:
- Filesystem watches can be set on files and directories. We can specify the type of access to watch. The syntax for a filesystem rule is:
  - `sudo auditctl -w <path-to-file> -p <permissions> -k <key-name>`
  - Where,
    - Path-to-file:   is the file or directory that is audited.
    - Permissions:  the permissions that are logged, This value can be one or a combination of r(read), w(write), x(execute), and a(attribute change).
    - Key-name:  this is an optional string that helps you identify which rule(s) generated a particular log entry.
  - In our case let’s make a test file in our Desktop and name it ‘test’ and let’s log the events in this file using following command on Desktop:
    - `touch test-file`
  - And let’s create a file named ‘hosts-file-changes’ again on the Desktop and here we will record the logs. LEt’s use the following commands for this:
    - `touch logged-events`
  - Now let’s use this command to set a rule which will ask the audit system to watch for read access, write access, and attribute access changes to the file on  ‘_/home/gandalf/Desktop/test_’.
    - `sudo auditctl -w /home/gandalf/Desktop/test-file -p rwx -k /home/gandalf/Desktop/logged-events`
  - We can use the following command to view the rules we just added and we can then verify:
    - `sudo auditctl -l`<br/>
  ![create files, add and view rules](https://github.com/LF-DevOps-Intern/5_3_logging_reporting-vikram-rikeshkarma/blob/main/Qno3/snapshots/create%20files%2C%20add%20and%20view%20rules.png)
    - I have more than one rule set because the others were set when I was practising for this task.
- Now let’s make some manual changes to the test file so as to check if we have done everything right and everything is up and running.
- After all this let’s search the audit logs for the events, for this we can use the command ausearch i.e:
  - `sudo ausearch -k <-key-name>`
  - For our case the command will be:
    - `sudo ausearch -k /home/gandalf/Desktop/logged-events`<br/>
  ![ausearch events logged](https://github.com/LF-DevOps-Intern/5_3_logging_reporting-vikram-rikeshkarma/blob/main/Qno3/snapshots/ausearch%20events%20logged.png)

We can observe that the events have been recorded and we have successfully set up a file in our system in which all the events of the action of read, write and execute will be logged.