<h1 align="center"> Penetration Testing Report: Footprinting and Network Scanning Phase </h1>

<div align="center"> 
  
|  |  |
| :---: | :---: |
|**Name**| Ashley-Megan Ikhialose Ehiede |
|**Batch Number**| 084|
|**Modules Completed**| PM1: Footprinting with Multiple Tools and Footprint with GHDB  |
|**Target**| networkwalks.com  |
|**Permission obtained from target?**| Yes |
|**Phases Covered**| Phase 1: Reconnaissance  | 

</div>



## Introduction
In this mission, I set out to perform passive recon on my target network, networkwalks.com. The goal was to find any all information that could be useful to an attacker in a future attack. For the second module, I tried to fine 10 unsecured web cameras live streaming on the internet, and 10 

<div align="center">

|**Tools and Commands Used**| 
| :---:| 
|Kali Linux|
|`whois` |  
|`whatweb`|  |
|`nslookup`|  |
|`curl`| |
|`wafw00f`|  |
|`dnrecon`|
| Google Hacking Database (GHDB)|

</div>

### Activities Executed
#### Reconnaissance on Kali
I performed recon against networkwalks.com, putting myself in the shoes of an attacker to see what they would see. Using the `whois` command on Kali, I was able to get basic information about the registration, like expiry dates and registrar abuse contact email and phone number. Next, I used `whatweb` to get the exact technologies running on this website. This exposed the exact software version (Wordpress 7.1.4), an email address and the server's IP address. I used `nslookup` afterwards to confirm the server's IP as 192.232.216.135.

After I used `curl` with `-i` flag to fetch the http header. This gives me the REST API endpoint. `wafw00f` featured next, used to see whether the website is behind a web application firewall and which one exactly. Finally, I used `dnsrecon` to list out the DNS records of our target. This gives me a key insight into the target website's infrastructure.  

#### Reconnaissance with Google Hacking Database
Using Google Hacking Database (GHDB) I was able to find 10 live vulnerable security cameras and 10 downloadable mathematics textbooks. They are listed as follows: 

|No. |Link | Relevant Dork | Username/Password (if any) |
|:--- |:---|:---|:---|
|1.|https://www.lmc.edu/webcam.htm  |intitle:"Webcam" inurl:WebCam.htm | -- |
|2.|https://www.skylinewebcams.com/webcam/italia/lazio/roma/piazza-di-spagna.html |inurl:webcam site:skylinewebcams.com inurl:roma | -- |
|3. |https://www.skylinewebcams.com/en/webcam/italia/lazio/roma/roma-skyline.html | inurl:webcam site:skylinewebcams.com inurl:roma | -- |
|4.|http://www.insecam.org/en/view/812476/ |intitle:"webcamXP" inurl:8080 | -- |
|5.|http://www.insecam.org/en/view/986159/ |intitle:"webcamXP" inurl:8080  | -- |
|6.|http://109.233.191.130:8080/multi.html |intitle:"webcamXP 5" inurl:admin.html | -- |
|7.|http://184.57.102.6:5800/ | intitle:"webcamXP 5" inurl:admin.html| -- |
|8.|https://www.cameraftp.com/cameraftp/publish/camera.aspx/parentID117642754/shareID12467551/modelive/nameVIH%20Gold%20River/camTypeCamera |inurl:"view.shtml" "camera"  | --|
|9.|http://109.164.203.165/cgi-bin/guestimage.html | "Camera Live Image" inurl:"guestimage.html"| -- |
|10.|http://185.186.69.63:10082/cgi-bin/guestimage.html |"Camera Live Image" inurl:"guestimage.html" | -- |

Each dork led to a website that allowed me to view various webcams all over the world. This was only possible because many of these webcams use old, deprecated software and hardware, making them easy to find with modern technology.

