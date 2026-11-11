<h1 align="center"> Penetration Testing Report with Kali and Google Hacking Database</h1>

<div align="center"> 
  
  |  |  |
  | :---: | :---: |
  |**Name**| Ashley-Megan Ikhialose Ehiede |
  |**Batch Number**| 084|
  |**Modules Completed**| PM1: Multiple Kali Tools <br> PM2: Footprint with GHDB  |
  |**Target**|`networkwalks.com`|
  |**Permission obtained from target?**| Yes |
  |**Phases Covered**| Phase 1: Reconnaissance| 

</div>

## Liability Disclaimer
*I have performed these activities only on the systems & devices where I had secured written permission or the devices/systems that I own myself. All these materials are for education and research purpose only. Do not use anything from here to break the law. The instructor, the authors and Networkwalks are not responsible for what you do with this knowledge. Every action you take is your own responsibility. Misuse can lead to criminal charges, heavy fines, loss of your job and a permanent record. In most countries unauthorized access is a crime even when nothing is damaged.*



## Introduction
In this project, I completed modules one and two of the available five for week two of my internship with Networkwalks. For the first task, I set out to perform passive recon on the target network, networkwalks.com. I obtained  explicit, written permission before I began. The goal was to find any information that could be useful in the planning stages of an attack. For the second module, I found 10 unsecured web cameras live streaming on the internet, and 10 publicly available downloadable math textbooks.

<div align="center">
  
  |**Tools and Commands Used**| Purpose |
  | :---:| :---: |
  |Kali Linux| Operating System used |
  |`whois`| Checks public registration database to see who owns a domain, their contact details and when the domain was registered or expires |
  |`whatweb`| Scans a website to fingerprint the tech it runs on |
  |`nslookup`| Queries DNS servers to translate a domain name into its underlying IP address  |
  |`curl -I`| Sends a web request to a site and displays the raw HTTP response headers |
  |`wafw00f`| Exposes the Web Application Firewall protecting a site |
  |`dnsrecon`| Reveals the public DNS infrastructure of a given website |
  | Google Hacking Database (GHDB)| Source of dorks used for advanced searches |

</div>

## Activities Executed
#### Reconnaissance on Kali
I performed recon against networkwalks.com, putting myself in the shoes of an attacker to see what they would see. Using the `whois` command on Kali, I was able to get basic information about the registration, like expiry dates and registrar abuse contact email and phone number. Next, I used `whatweb` to get the exact technologies running on this website. This exposed the exact software version (WordPress 7.1.4, WordPress Download Manager 3.3.76), an email address and the website's IP address (192.232.216.135). I used `nslookup` afterwards to reveal the server's IP as 10.250.146.113 and confirm the previously revealed website IP.

After I used `curl` with `-I` flag to fetch the HTTP header only. This gives me the REST API endpoint. `wafw00f` featured next, used to see whether the website is behind a web application firewall and which one exactly. Finally, I used `dnsrecon` to list out the DNS records of our target. This gives me a key insight into the target website's infrastructure. For example, that the web server and mail server resolve to the same IP address and are possibly sharing a machine.

#### Reconnaissance with Google Hacking Database: Webcams
Using Google Hacking Database (GHDB) I was able to find ten live vulnerable security cameras and ten downloadable mathematics textbooks. As I do not have the explicit permission of the webcam owners, I have censored sensitive information like IP addresses and links. Full details are provided in the attached  relevant PDF. Each dork led to a website that allowed me to view various webcams all over the world. This was only possible because many of these webcams use old, deprecated software and hardware, making them easy to find with modern technology.

#### Mathematics Ebook Dorks
The eBook details however, are provided in full because they were deliberately made public by the owners. I have listed them below:

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

## Risk Analysis and Potential Impact
Based on information gathered during these activities, I identified the following risks:

|No | Finding | Potential Impact | Risk Level |
|:---| :---| :---| :---|
|1.| Identified Server IP Address| An IP address tells an attacker the location of a server |🟡|
|2.| Email Exposed in `whatweb` response| This email could be targeted in a phishing or social engineering campaign |🟡|
|3.| Web Technology Exposed (WordPress, WordPress Download Manager) | Attackers can test for known vulnerabilities of these versions|🟠|
|4.| WAF Technology Exposed | Shows an attacker the architecture of the network. |🟡|
|5.| Unsecured Webcams and Sensitive Files Exposed by Advanced Google Searches| Private cameras and PDFs are easily found using dorks, potentially giving attackers access to sensitive data|🔴|

<sup>
 Key: 🟡 = Low  🟠 = Medium 🔴 = Critical
</sup>

### Recommendations
* Regularly audit publicly exposed information.
* Plain text emails left in HTTP headers or code should not have admin level privileges.
* Ensure all software is updated regularly. 
* Review HTTP headers and minimize unnecessary information contained within.
* Replace technology (like web cameras) once security updates are discontinued by the manufacturer.
* Remove exposed cameras from the internet immediately.
  

## Lessons Learned
* **Passive Reconnaissance Fundamentals:** Using Kali Linux tools like `whois`, `whatweb`, `nslookup`, and `dnsrecon` reveals critical target infrastructure such as IP addresses, DNS records, and exact CMS versions without directly alerting the target.
* **Header & Firewall Analysis:** Fetching HTTP headers with `curl -i` exposes underlying endpoints like REST APIs, while `wafw00f` helps determine if a Web Application Firewall (WAF) is actively filtering traffic.
* **The Power of Google Dorking (GHDB):** Advanced search operators can uncover both intentionally public resources (like academic PDFs) and sensitive, unintended exposures hidden behind standard search results.
* **Risks of Legacy IoT Devices:** Unsecured webcams running outdated or deprecated software remain easily discoverable on the public internet, highlighting the importance of regular firmware updates and proper access controls.
* **Ethical & Legal Boundaries in Pentesting:** Obtaining explicit written permission before scanning a target and redacting sensitive third-party data (such as exposed webcam IPs) are essential practices for responsible security research.

## Conclusion
Overall, this reconnaissance exercise showed how much information is publicly available about a target before an active attack even begins. Using passive Kali Linux tools against `networkwalks.com` revealed key details about its hosting infrastructure, software versions, and firewall setup, while Google Dorking demonstrated how easily misconfigured devices and public files can be found across the web. Addressing these exposures through regular updates, header minimization, and proper access controls will significantly reduce the attack surface and improve overall security posture.
