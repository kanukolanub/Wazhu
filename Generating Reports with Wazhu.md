Wazuh features a reporting module that allows you to view a summarised breakdown of events that have occurred on an agent. 

First, we will need to select a view to generate reports from. In this example, I want to generate a report of the security events in the last 24 hours. To do so, I will need to open the view: 1. Modules -> 2. Security Events
![image](https://github.com/user-attachments/assets/a4fa96f0-fcb7-472b-8562-97091b53191a)

Now, if there have been alerts within the last 24 hours, I can generate a report like so: 

![image](https://github.com/user-attachments/assets/8213bc13-371f-4265-8a78-8a69b10ae152)

Note: If this button is greyed out, there is no report data, so you will either need to change your query or extend the date range.
The report may take between a couple of seconds to a few minutes to generate (depending on the amount of data needed to be processed). After allowing some time, we will navigate to the report overview dashboard within Wazuh.
First, press on the "Wazuh" heading at the top of the screen and select "Management", and then click on the "Reporting" text located under the "Status and Reports" sub-heading:
![image](https://github.com/user-attachments/assets/868072c7-86a8-4ccb-9ecc-cad3d498dcad)

The report overview dashboard lists all generated reports. To download a report, press the save icon on the right of the report located under the "Actions" heading. 
Which will download the report as a PDF to your machine. A generated security events report looks like so:
![image](https://github.com/user-attachments/assets/17c48bc1-b830-4603-860a-742ceaeb8e3e)
