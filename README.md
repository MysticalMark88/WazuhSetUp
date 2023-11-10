<h1>Set Up a SIEM with Wazuh.</h1>


<h2>Description</h2>
In this project we will install and set up a Wazuh SIEM dashboard on a cloud server and add two ubuntu server endpoints as agents to be monitored. Both agents have suricata installed. We will make sure that suricata's logs are readable by Wuzuh and the alerts are present in the dashboard alongside the logs and files Wazuh is already monitoring on those systems.   
<br />


<h2>Environments Used: </h2>

- <b>Ubuntu 22.04 LTS, running on Linode connected over SSH from a local Manjaro system</b>
- <b>Ubuntu 20.04 LTS on server endpoints, running on DigitalOcean connected over SSH from the same local system</b>

<h2>Installation & Set Up walk-through:</h2>

<p align="center">
We will be using the installer provided by the Wazuh quick start documentation to set up our Wazuh server and run it as follows: <br/>
<img src="https://i.imgur.com/w0g6Kph.png" height="80%" width="80%" alt="Install Wazuh"/>
<br />
<br />
Once install is complete we are provided with credentials, we will note these then proceed to access Wazuh from our browser:  <br/>
<img src="https://i.imgur.com/5D2aJAm.png" height="80%" width="80%" alt="Finish Install"/>
<br />
<br />
On our local machine we will enter the ip of the server in our browser to reach the login page for our fresh install of Wazuh: <br/>
<img src="https://i.imgur.com/QBPTyn4.png" height="80%" width="80%" alt="Connect to Log In screen"/>
<br />
<br />
Once successfully logged in we can see the main page of Wazuh and we can also see that we need to add our agents:  <br/>
<img src="https://i.imgur.com/NlEKozR.png" height="80%" width="80%" alt="Wazuh home page"/>
<br />
<br />
We will then navigate to the page to add an agent and start entering the information for our first ubuntu server:  <br/>
<img src="https://i.imgur.com/Im2ohLo.png" height="80%" width="80%" alt="Set up first agent"/>
<br />
<br />
Next, we are given commands we can use on our server endpoint to set up and install the Wazuh Agent:  <br/>
<img src="https://i.imgur.com/HpSzCiu.png" height="80%" width="80%" alt="Set up first agent server command"/>
<br />
<br />
We will then SSH into our first server endpoint and run the command to deploy the Wazuh agent:  <br/>
<img src="https://i.imgur.com/O6Sujnr.png" height="80%" width="80%" alt="Deploy first agent"/>
<br />
<br />
After the install completes we then need to enable and start the Wazuh agent service using systemctl:  <br/>
<img src="https://i.imgur.com/CdmLcZq.png" height="80%" width="80%" alt="Enable and Start First Agent"/>
<br />
<br />
We can now see in our browser that Wazuh is showing one connected agent:  <br/>
<img src="https://i.imgur.com/ZpBNt3v.png" height="80%" width="80%" alt="Agent Connected"/>
<br />
<br />
Next, we can navigate to the security events and see that the agent is already reporting alerts from system logs:  <br/>
<img src="https://i.imgur.com/g1ChHy7.png" height="80%" width="80%" alt="View alerts on first agent"/>
<br />
<br />
Now, we will need to open the configuration file for the Wazuh agent on this endpoint so we can set up suricata:  <br/>
<img src="https://i.imgur.com/4Us9fbT.png" height="80%" width="80%" alt="Edit config on first agent"/>
<br />
<br />
We will edit the configuration file adding the following block so Wazuh can access suricata's logs:  <br/>
<img src="https://i.imgur.com/uVtj1hp.png" height="80%" width="80%" alt="Edit Config"/>
</p>

<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
