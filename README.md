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
The rule set will then need to be updated so we have updated rules for Suricata to use to monitor the network:  <br/>
<img src="https://i.imgur.com/YMIuuYE.png" height="80%" width="80%" alt="Update Suricata Rules"/>
<br />
<br />
Since updating the config and rules we will test the configuration and once successfull will then start the Suricata service:  <br/>
<img src="https://i.imgur.com/XDrkJK6.png" height="80%" width="80%" alt="Test and start Suricata"/>
<br />
<br />
We will then check the status of the service to make sure it has started and running successfully:  <br/>
<img src="https://i.imgur.com/97rtZ9A.png" height="80%" width="80%" alt="Check status of Suricata"/>
<br />
<br />
We will also check the Suricata log file to confirm that it has successfully started:  <br/>
<img src="https://i.imgur.com/iWLsXPT.png" height="80%" width="80%" alt="Check status of Suricata"/>
<br />
<br />
Next, we will want to test Suricata to make sure it is detecting malicious traffic:  <br/>
<img src="https://i.imgur.com/zf1B8tF.png" height="80%" width="80%" alt="Test Suricata"/>
<br />
<br />
We will now check Suricata's fast.log file to see if it detected the malicious test, we can see that it was successfull. Suricata is installed and running successfully!  <br/>
<img src="https://i.imgur.com/mXPec1E.png" height="80%" width="80%" alt="Test Suricata"/>
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
