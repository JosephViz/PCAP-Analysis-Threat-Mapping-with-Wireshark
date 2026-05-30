<h1>PCAP Analysis & Threat Mapping with Wireshark</h1>

 ### 

<h2>Description</h2>
Network forecnsics using Wireshark to analyze protocols, hosts, and SMB lateral movement attempts


<h2>Utilities Used</h2>

- <b>Wireshark</b> 


<h2>Environments Used </h2>

- <b>Windows 11</b> 

<h2>Program walk-through:</h2>

<p align="center">
Opening "Protocol Hierarchy Statistics" panel to reveal overall structure of Pcap:<br/>
<img src="https://i.imgur.com/SKNIBaz.png" height="40%" width="80%" alt="Wirshark process"/>
<br />
<br />
Deeper inpection reveals IPV4, TCP, & SMB2 Usage:  <br/>
<img src="https://i.imgur.com/kgIxqco.png" height=80%" width="80%" alt="Wireshark process"/>
<br />
<br />
Reviewing the conversations-level traffic statistics to identify top talkers(.130,.131,.133) <br/>
<img src="https://i.imgur.com/n64UHGi.png" height="80%" width="80%" alt="Wireshark process"/>
<br />
<br />
Traffic analysis for 10.0.0.130; TCP connection was successful over port 445:  <br/>
<img src="https://i.imgur.com/V5KCs84.png" height="80%" width="80%" alt="Wireshark process"/>
<br />
<br />
TCP Stream for packet; Identified hostname, NTLMSSP :  <br/>
<img src="https://i.imgur.com/PPwMlnN.png" height="80%" width="80%" alt="Wireshark process"/>
<br />
<br />
Network Query request capture, IPC$ & $ADMIN Request Successful  <br/>
<img src="https://i.imgur.com/zAzFApu.png" height="80%" width="80%" alt="Wireshark process"/>
<br />
<br />
Traffic Analysis for 10.0.0.131(MARKTING-PC):  <br/>
<img src="https://i.imgur.com/f3bAUbT.png" height="80%" width="80%" alt="Wireshark process"/>
<br />
<br />
Lateral movement attempt from 10.0.0.130 to 10.0.0.131: <br/>
<img src="https://i.imgur.com/nmLURjx.png" height="40%" width="80%" alt="Wireshark process"/>
<br />
<br />
Analysis of SMB2 traffic showing remote file access:  <br/>
<img src="https://i.imgur.com/Kniiluh.png" height=80%" width="80%" alt="Wireshark process"/>
</p>

<h2>Summary</h2>
The process began by examining "Protocol Hierarchy Statistics" to identify active protocols and overall traffic composition, follwed by 'Conversations analysis" to determin top talkers anc communication patterns. Subsequent filtering revealed hostnames, authentication exchanges, and SMB2 activity associated with PsExec, including a failed lateral movement attempt from 10.0.0.130 to 10.0.0.131. The findings demonstrate how systematic packet inspection can reconstuct attacker behavior and validate host interactions within a compromised network.
<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
