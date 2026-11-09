<h1 align="center"> Penetration Testing Report: Footprinting and Network Scanning Phase </h1>

<div align="center"> 
  
|  |  |
| :---: | :---: |
|**Name**| Ashley-Megan Ikhialose Ehiede |
|**Batch Number**| 084|
|**Modules Completed**| PM1:Footprinting with Multiple Tools,  |
|**Target**| networkwalks.com  |
|**Permission obtained from target?**| Yes |
|**Phases Covered**| Phase 1: Reconnaissance  | 

</div>



## Introduction
talk about what my goal was briefly and give a short over view 

|**Tools and Commands Used**| 
| :---:| 
|Kali Linux|
|`whois` |  
|`whatweb`|  |
|`nslookup`|  |
|`curl`| |
|`wafw00f`|  |
|`dnrecon`|

### Activities Executed
#### Reconnaissance
I performed recon against networkwalks.com, putting myself in the shoes of an attacker to see what they would see. Using the `whois` command on Kali, I was able to get basic information about the registration, like expiry dates and registrar abuse contact email and phone number. Next, I used `whatweb` to get the exact technologies running on this website. This exposed the exact software version (Wordpress 7.1.4), an email address and the server's IP address. I used `nslookup` afterwards to confirm the server's IP as 192.232.216.135.

After I used `curl` with `-i` flag to fetch the http header. This gives me the REST API endpoint. `wafw00f` featured next, used to see whether the website is behind a web application firewall and which one exactly. Finally, I used `dnsrecon` to list out the DNS records of our target. This gives me a key insight into the target website's infrastructure.  


