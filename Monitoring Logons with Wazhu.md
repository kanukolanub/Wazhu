Wazuh's security event monitor is capable to actively record both successful and unsuccessful authentication attempts. The rule with an id of 5710 detects attempted connections that are unsuccessful for the SSH protocol. Let's look at this animated picture below as an example.

![image](https://github.com/user-attachments/assets/0695b895-be7d-4d73-975c-be8fb558a001)

The alert was created because someone tried to log onto the agent "ip-10-10-73- 118" with the user "cmnatic" which does not exist. I have summarized this alert into the table below:

![image](https://github.com/user-attachments/assets/61f22b50-0d11-4fd9-90e4-2d4a0b098144)

For reference, this alert is stored in a specific file on the Wazuh management server: /var/ossec/logs/alerts/alerts.log. We can use a command such as grep or nano to search through this file on the management server manually.

![image](https://github.com/user-attachments/assets/eb42bbb8-b63d-4a8c-8c08-d4b1cbf3cb06)

Looking at the animated gif below, we can see how Wazuh has created an alert for successful login to a Window's server running the Wazuh agent. Because this attempt was successful, the severity of the alert is considered less than that of an unsuccessful login. This can, of course, be tailored to your environment. For example, if a user infrequently used is logged on, you can configure Wazuh to list this alert with higher severity.

![image](https://github.com/user-attachments/assets/75b19709-9522-428d-a07b-f7f7b79e633f)

The animated gif below shows the number of Windows agent events/alerts triggered to show how many times a user has logged on. . In this case, it narrows down the total logon events of 285 to 79.

![image](https://github.com/user-attachments/assets/012ff2b5-743f-4676-8e2e-eeca91414219)

Navigate to the "Management" tab by pressing Wazuh -> Management and open the "Rules" module like so:

![image](https://github.com/user-attachments/assets/10f2bc80-8f83-45ed-9151-263b514abd56)






