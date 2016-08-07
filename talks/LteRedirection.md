# Forcing Targeted LTE Cellphone into Unsafe Network

[Abstract](https://www.defcon.org/html/defcon-24/dc-24-speakers.html#Shan)

## Summary
LTE trades away some of your security to connecting to a secure network, in favor of being able to get clients connected in the face of a very overloaded network.  Specifically, the network/tower redirection message (RRC) isn't encrypted because it would add extra load to overloaded towers trying to load balance to lighter-loaded towers in a disaster scenario.

Side note: Team Unicorn 360 do fascinating security research, but I haven't had good luck with using their code in the past, and due to relatively low english proficiency, I find them very difficult to understand.  :)

## Notes
LTE isn't perfectly secure, already some papers and presentations (blackhat EU last year) demonstrating vulnerabilites.  LTE and IMSI catcher and Dos Attack.

### IMSI Catcher

### DOS Attack
Can tell phone you're an illegal clellphone, or there is no network available, could shut down your 4g/3g/2g modem for a long time.  Some can only be recovered by rebooting.

### Redirection Attack
Malicious LTE network can redirect the phone to a malicious GSM network.  Demo video using "OpenBTS>".

### Risk
* DoS cellphone
* Fake GSM network can make malicious call and SMS
* Eavesdrop and MITM all network traffic, voice and data, from the phone

### LTE Basic Procedure
1. Phone boots
1. Phone chooses network with strongest signal
1. Phone sends attach request
1. Malicious base station sends a Tracking Area Update Reject response, causing the phone to send it's IMSI number
1. Having the IMSI allows you send an Attach Reject with codes 3,7,8,14, all of which convince the modem that it should shut down for a long time (eg. "you're stolen", and "you're not allowed to be here").  Can also send redirectedCarrierInfo, to redirect you into the 2G or 3G malicious network.

### Why not just Jam 4G?
Why is this better than jamming?  Jamming influences all cell phones.  The redirection attack allows you to target only specific phones.  You can redirect all other users who connect to a nearby regular 4G network, and only capture the target device and redirect it to your target network.

### How to build a fake LTE newtork
You need a computer and a USRP Software Defined Radio

#### Available Software Stacks
##### Open Air Interface by Eurecom
* www.openairinterfae.org
* most complete and open source LTE software
* support connecting cellphone to Internet
* complicated architecture

##### OpenLTE by Ben Wojtowicz
* openlte.sourceforge.net
* not stable LTE data, but functional enough for fake LTE network
* much cleaner architecture, more popular for security researchers

#### DOS
The current release doesn't support TAU request, but TAU reject is available!  Reasonably easy to implement.

#### Redirection
A bit more complicated, have to read protocol and implement message.  She showed a brief overview, no code.

### Why is this possible?
Why is the RRC redirection message not encrypted?

Is this a new problem?  Apparently it was documented in January 2006, over 10 years ago.  In Nov 2006, RRC integrity and ciphering algorithm can only be changed in the case of the eNodeB handover.

In the case of an earthquake, it's important to allow the network side to control redirection to do load balancing efficiently, rather than the client doing so very inefficiently with no knowledge of the tower loading.  It was a conscious decision not to encrypt the RRC message.

### Countermeasures
#### Cellphone Manufacturers
1. Don't follow the redirection command, auto-search the avilable base stations.
2. Follow but raise an alert to cellphone user, "Warning, you are downgraded to a lower security network!"

#### Fix weak GSM
Possible, but a hard battle in standardization committees, such as:
1. Refuse one-way authenticatino
1. Disabling compromised encryption in mobile
