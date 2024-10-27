Using Our Own Client

The Wazuh management server features a rich and extensive API to allow the Wazuh management server to be interacted with using the command line. Because the Wazuh management server requires authentication, we must first authenticate our client.

In this task, we will be using a Linux machine with the curl tool installed to interact with the Wazuh management server API. First, we will need to authenticate ourselves by providing a valid set of credentials to the authentication endpoint.

Once we are authenticated, the Wazuh management server will give us a token (similar to a session) that we will need to provide for any further interaction. We can store this token as an environment variable on our Linux machine like the snippet below:

(replacing WAZUH_MANAGEMENT_SERVER_IP with the IP address of the Wazuh management server (i.e. MACHINE_IP):

TOKEN=$(curl -u : -k -X GET "https://WAZUH_MANAGEMENT_SERVER_IP:55000/security/user/authenticate?raw=true")

Let’s confirm that we have authenticated okay and have been given a token by the Wazuh management server:

curl -k -X GET "https://MACHINE_IP:55000/" -H "Authorization: Bearer $TOKEN"

![image](https://github.com/user-attachments/assets/a1286ebc-8e79-42e8-99e4-37ef03cc6553)

We can use the standard HTTP request methods such as GET/POST/PUT/DELETE by providing the relevant option after a -X i.e. -X GET
curl -k -X GET "https://MACHINE_IP:55000/manager/status?pretty=true" -H "Authorization: Bearer $TOKEN"

For example, let’s use the Wazuh API to list some statistics and important information about the Wazuh management server, including what services are being monitored and some general settings about the Wazuh management server:

curl -k -X GET "https://MACHINE_IP:55000/manager/configuration?pretty=true§ion=global" -H "Authorization: Bearer $TOKEN"

![image](https://github.com/user-attachments/assets/ed31ad49-554e-4633-9239-a87c0341fcc4)

Or perhaps, we can use the Wazuh management server’s API to interact with an agent:
curl -k -X GET "https://MACHINE_IP:55000/agents?pretty=true&offset=1&limit=2&select=status%2Cid%2Cmanager%2Cname%2Cnode_name%2Cversion&status=active" -H "Authorization: Bearer $TOKEN"

![image](https://github.com/user-attachments/assets/baf57e04-dfa2-4530-a98b-deae9a2455d0)

Using Wazuh's API Console
Wazuh has a powerful, integrated API console within the Wazuh website to query management servers and agents. Whilst it is not as extensive as using your own environment (where you can create and run scripts using python, for example), it is convenient.

To find this API console, we need to open the "Tools" category within the Wazuh heading at the top:

![image](https://github.com/user-attachments/assets/a5b7458f-eb3b-47d7-804c-cb9f15b5aa35)

You will be greeted with a few sample queries that you can run. Simply select the line and press the green run arrow to run the query as demonstrated below:

![image](https://github.com/user-attachments/assets/8d71a911-30cd-4f11-ae26-bbad52530012)

Reminder, the syntax for running queries uses the same web methods (i.e. GET/PUT/POST) and endpoints (i.e. /manager/info) as you would use with curl. You can view some more options about API endpoints by following Wazuh's detailed API documentation here






