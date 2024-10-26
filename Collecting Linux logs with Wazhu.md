Capturing logs from a Linux agent is a simple process similar to capturing events from a Windows agent. We will be using Wazuh’s log collector service to create an entry on the agent to instruct what logs should be sent to the Wazuh management server.

For example, in this task, we will be monitoring the logs of an Apache2 web server. To begin, let’s configure the log collector service on a Linux server running the Wazuh agent.

Wazuh comes with many rules that enable Wazuh to analyze log files and can be found in /var/ossec/ruleset/rules. Some common applications include:

Docker
FTP
WordPress
SQL Server
MongoDB
Firewalld
And many, many more (approximately 900).
However, you can always make your own rules. In this task, Wazuh will digest Apache2 logs using the 0250-apache_rules.xml ruleset.

This ruleset can analyze apache2 logs for warnings and error messages like so: We will need to insert this into the Wazuh’s agent that is sending logs to the Wazuh management servers configuration file located in /var/ossec/etc/ossec.conf:

![image](https://github.com/user-attachments/assets/c4aeea0c-1a12-4b0f-803c-f88698258a7d)
