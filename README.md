<h1 align="center"> Penetration Testing Report</h1>

<div align="center"> 
  
|  |  |
| :---: | :---: |
|**Name**| Ashley-Megan Ikhialose Ehiede |
|**Batch Number**| 084|
|**Modules Completed**| PM1: Multiple Kali Tools <br> PM2: Footprint with GHDB  |
|**Target**| networkwalks.com  |
|**Permission obtained from target?**| Yes |
|**Phases Covered**| Phase 1: Reconnaissance| 

</div>

## Liability Disclaimer
*I have performed these activities only on the systems & devices where I had secured written permission or the devices/systems that I own myself. All these materials are for education and research purpose only. Do not use anything from here to break the law. The instructor, the authors and Networkwalks are not responsible for what you do with this knowledge. Every action you take is your own responsibility. Misuse can lead to criminal charges, heavy fines, loss of your job and a permanent record. In most countries unauthorized access is a crime even when nothing is damaged.*



## Introduction
In this project, I completed modules one and two of the available five for week two of my internship with Networkwalks. For the first task, I set out to perform passive recon on the target network, networkwalks.com. Prior to this exercise, I obtained  explicit, written permission. The goal was to find any information that could be useful in the planning stages of an attack. For the second module, I found 10 unsecured web cameras live streaming on the internet, and 10 publicly available downloadable math textbooks.

<div align="center">

|**Tools and Commands Used**| 
| :---:| 
|Kali Linux|
|`whois` |  
|`whatweb`|  |
|`nslookup`|  |
|`curl`| |
|`wafw00f`|  |
|`dnsrecon`|
| Google Hacking Database (GHDB)|

</div>

### Activities Executed
#### Reconnaissance on Kali
I performed recon against networkwalks.com, putting myself in the shoes of an attacker to see what they would see. Using the `whois` command on Kali, I was able to get basic information about the registration, like expiry dates and registrar abuse contact email and phone number. Next, I used `whatweb` to get the exact technologies running on this website. This exposed the exact software version (Wordpress 7.1.4), an email address and the server's IP address. I used `nslookup` afterwards to confirm the server's IP.

After I used `curl` with `-i` flag to fetch the http header. This gives me the REST API endpoint. `wafw00f` featured next, used to see whether the website is behind a web application firewall and which one exactly. Finally, I used `dnsrecon` to list out the DNS records of our target. This gives me a key insight into the target website's infrastructure.  

#### Reconnaissance with Google Hacking Database: Webcams
Using Google Hacking Database (GHDB) I was able to find ten live vulnerable security cameras and ten downloadable mathematics textbooks. As I do not have the explicit permission of the webcam owners, I have censored sensitive information like IP addresses and links. Full details are provided in the attached  relevant PDF. Each dork led to a website that allowed me to view various webcams all over the world. This was only possible because many of these webcams use old, deprecated software and hardware, making them easy to find with modern technology.

#### Ebook Dorks
The ebook details however, are provided in full because they were deliberately made public by the owners. I have listed them below:

|No. |Link| Relevant Dork|
|:---| :---| :---|
|1.|https://www.thomasaquinas.edu/sites/default/files/media/file/senior-mathematics-manual.pdf |`site:edu filetype:pdf "mathematics" "textbook"` |
|2.|https://jontallen.ece.illinois.edu/uploads/537.F18/Papers/MathematicsandItsHistory-johnStillwell.pdf|`site:edu filetype:pdf "mathematics" "textbook"` |
|3.|https://www.ms.uky.edu/~sohum/ma330/files/william-dunham-journey-through-genius-the-great-theorems-of-mathematics-penguin-non-classics1991014014739x.pdf |`site:edu filetype:pdf "mathematics" "textbook"`|
|4.|https://sites.math.rutgers.edu/~zeilberg/akherim/PCM.pdf|`site:edu filetype:pdf "mathematics" "textbook"`|
|5.|https://www.textbookequity.org/Textbooks/Linear-Algebra-theory_apps_OTCe.pdf |`intitle:"linear algebra" filetype:pdf site:org` |
|6.|https://philarchive.org/archive/MAYPAP-6 |`intitle:"linear algebra" filetype:pdf site:org` |
|7.|https://www.gutenberg.org/files/41568/41568-pdf.pdf |`intitle:"introduction" "math" filetype:pdf site:org`|
|8.|https://discrete.openmathbooks.org/pdfs/dmoi-tablet.pdf|`intitle:"discrete mathematics" "textbook" filetype:pdf`|
|9.|https://mathdept.byu.edu/~doud/Transition/Transition.pdf |`intitle:"advanced mathematics" "textbook" filetype:pdf` |
|10.|https://fsw01.bcc.cuny.edu/mathdepartment/Courses/Math/MTH01/ArithBook5thEd.pdf|`intitle:"arithmetic" "textbook" filetype:pdf`| 

## What I Learned
* **Passive Reconnaissance Fundamentals:** Using Kali Linux tools like `whois`, `whatweb`, `nslookup`, and `dnsrecon` reveals critical target infrastructure—such as IP addresses, DNS records, and exact CMS versions without directly alerting the target.
* **Header & Firewall Analysis:** Fetching HTTP headers with `curl -i` exposes underlying endpoints like REST APIs, while `wafw00f` helps determine if a Web Application Firewall (WAF) is actively filtering traffic.
* **The Power of Google Dorking (GHDB):** Advanced search operators can uncover both intentionally public resources (like academic PDFs) and sensitive, unintended exposures hidden behind standard search results.
* **Risks of Legacy IoT Devices:** Unsecured webcams running outdated or deprecated software remain easily discoverable on the public internet, highlighting the importance of regular firmware updates and proper access controls.
* **Ethical & Legal Boundaries in Pentesting:** Obtaining explicit written permission before scanning a target and redacting sensitive third-party data (such as exposed webcam IPs) are essential practices for responsible security research.
