Devices that record the events and processes of a system are called agents. Agents monitor the processes and events that take place on the device, such as authentication and user management. Agents will offload these logs to a designated collector for processing, such as Wazuh.

![image](https://github.com/user-attachments/assets/6e7869db-0708-49eb-b015-a73c33123ecc)

In order for Wazuh to be populated, agents need to be installed onto devices to log such events. Wazuh can guide you through the agent deployment process provided you fill out some pre-requisites such as::

1. Operating System
2. The address of the Wazuh server that the agent should send logs to (this can be a DNS entry or an IP address)
3. What group the agent will be under - you can sort agents into groups within Wazuh if you wish

This wizard can be launched by navigating to the following location on the Wazuh server: Wazuh -> Agents -> Deploy New Agent as illustrated in this screenshot below:
