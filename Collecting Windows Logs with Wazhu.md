All sorts of actions and events are captured and recorded on a Windows operating system. This includes authentication attempts, networking connections, files that were accessed, and the behaviours of applications and services. This information is stored in the Windows event log using a tool called Sysmon.

We can use the Wazuh agent to aggregate these events recorded by Sysmon for processing to the Wazuh manager. Now, we will need to configure both the Wazuh agent and the Sysmon application.  Sysmon uses rules that are made in XML formatting to be triggered. For example, in the XML snippet below, we are telling Sysmon to monitor for the event of the powershell.exe process starting.

![image](https://github.com/user-attachments/assets/fc3d8261-d2dd-4474-b531-acaef09fc268)

To instruct Sysmon to do, we need to execute the Sysmon application and provide the aforementioned configuration file like so: Sysmon64.exe -accepteula -i detect_powershell.xml

![image](https://github.com/user-attachments/assets/0f8b1906-80b2-41b9-8236-111329fc082c)

![image](https://github.com/user-attachments/assets/43901a43-1f69-4a40-a5e4-1eef48de16ac)

![image](https://github.com/user-attachments/assets/f551e007-2a53-49a0-84f0-29431c1ea1ed)

We can verify that Sysmon has accepted our configuration file by navigating to the Event Viewer and searching for the “Sysmon” module like so:

![image](https://github.com/user-attachments/assets/841eabe0-a7d2-48fa-a744-2de9c672335a)

![image](https://github.com/user-attachments/assets/dcdd91e1-2c9e-4bb2-b1ca-4cf82cd95ea4)

Let’s launch a powershell prompt on the Windows Server and return to our Event Viewer. We can now see a record of this powershell prompt being opened, kept within the Event Viewer.

![image](https://github.com/user-attachments/assets/73b26534-a27d-4521-8f81-5483668cd47e)

Now we will need to configure the Wazuh agent on this Window Server to instruct it to send these events to the Wazuh management server. To do so, we need to open the Wazuh agent file located at: C:\Program Files (x86)\ossec-agent\ossec.conf

![image](https://github.com/user-attachments/assets/28bc6109-ee6b-43cb-894e-55b29e3371c5)

To include the following snippet:

![image](https://github.com/user-attachments/assets/ecc47cbc-51b0-4311-85ab-87b47a170b81)

Looking like so:

![image](https://github.com/user-attachments/assets/6e9ffe8a-144f-484f-800e-c9028457d6a4)

![image](https://github.com/user-attachments/assets/c6504b75-8b98-409d-8496-d36f978c4a84)

Once this is done, we need to tell the Wazuh Management server to add Sysmon as a rule to visualize these events. This can be done by adding  an XML file to the local rules located in /var/ossec/etc/rules/local_rules.xml

![image](https://github.com/user-attachments/assets/5883b10d-7d75-473a-92c7-31f15d31ab16)








