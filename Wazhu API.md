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
