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
We will need to run apt-update and then install suricata:  <br/>
<img src="https://i.imgur.com/FN4hiJQ.png" height="80%" width="80%" alt="Update and Install"/>
<br />
<br />
Once the install is complete we will enable Suricata using systemctl then stop the service temporarily so we can configure it: <br/>
<img src="https://i.imgur.com/uynGLFe.png" height="80%" width="80%" alt="Enable Suricata"/>
<br />
<br />
Next, we will check the default interface we want to monitor on to update the config file. Note the interface is eth0:  <br/>
<img src="https://i.imgur.com/FfyYKfA.png" height="80%" width="80%" alt="Check Default Interface"/>
<br />
<br />
We will then open the configuration file with nano to edit the configuration:  <br/>
<img src="https://i.imgur.com/0gW5qQ5.png" height="80%" width="80%" alt="Open Config File"/>
<br />
<br />
Next, we will edit the interface to match our system, in this case it is eth0:  <br/>
<img src="https://i.imgur.com/Dh86zWI.png" height="80%" width="80%" alt="Edit interface in config file"/>
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
