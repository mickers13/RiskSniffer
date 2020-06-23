# RiskSniffer ( work in progress )
 A http(s) Sniffer in python that tries to determine risks by textmining/analysis algorithms 
 All my code is written in Src. Almost all comments are in Dutch, because the company that gave me this assignment is dutch.
 
 This project uses MITM proxy as a framework get it here: https://github.com/mitmproxy/mitmproxy 
 
 This is NOT an attack framework, because you will need root and admin access to all computers on the network, meaning that this can only be used and should only be used if you are fully authorised to see ALL internet traffic on these computers. Please keep the European General Data Protection Regulation (AVG) in mind when using this software.
 
 ##### A warning in advance:
 This program decrypts all traffic, by creating an SSL certificate, and manually adding it to the trusted certificates list.
 Because of this, I would recommend to NOT share the certificate with other people that have or might have access to your network. This will mean that they will be able to see all traffic including passwords, usernames and other sensitive information.
 This program could also be modified to edit the webpages users see, what can give an attacker in your network a whole new framework for phishing/ credential-stealing. Please, notify your users to not enter ANY personal information on the computers that you installed this proxy sniffer, because these could be stolen. 
 
 
## How to install


* install the certs in the browsers, and windows of the hosts you want to sniff/analyse. ( from C:\Users\"your host/user here"\.mitmproxy by default) (Will showup after running the mitmdump command once.) 

_There is a windows installer in commandline(certutil), but for example Firefox I could not figure out how to auto install the selfmade cert._

* Download Mitmdump and replace the Venv with mine. ( not added on github because of file size! ) ( or look up the libraries used and install with pip)

* To be able to run this project, you need to add the DEV version of MITM-proxy to this folder with the standard name: mitmproxy

### Choose from the 2 following modes: 

#### 1. Local use, with external path setup
Install this full program on a desktop that you want to monitor, and make the path to save the log's on a shared folder on the network. ( no central server needed, and faster analysis since everycomputer analyses their own traffic.) ( fast but less secure.)

#### 2. External proxy, with 1 central proxy server
Install this full program on a desktop/server computer with alot/decent amount of proccessing power. 
Install a proxy redirect on all desktops towards this pc's IP-Adress + port 8080. 
( program will not be edittable from the other pc's + chance of this program being detected(and abused) by the user is a-lot lower, But the internet traffic might be a bit slower, since all traffic is re routed to one pc and then being analysed on the same desktop. )( Secure but slower internet speeds(if the central server does not have enough ram.) )

#### 2.1 External proxy, with a few central proxy servers.
Same as 2, but use multiple midrange, to lowend pc's to devide the workload. (Dont forget to divide the proxy setting ip aswell)
If problems occur, you can use -p (porthere) to also seperate the external proxies completely.


## How to run:
* To run this program enter following commands:

		cd "yourpathhere"\mitmproxy
		
		venv\Scripts\activate
		
		mitmdump -s "your path here"\Src\Start.py -q (for local server on port 8080)
		
		mitmdump -s "your path here"\Src\Start.py -q --listen-host "host ip here" (to manually determine ip)
		
		dont forget to configure the proxy settings on the pc's.
		
		You could configure your router so that only these proxyservers can connect to the internet, this way the computers have to connect to these proxy servers in order to access the internet.
		
Check mitmdump --help for more intresting options! ( some might break the program, be warned!)

