<h1>Phishing Email Threat Analysis</h1>

<h2>Introduction</h2>
My intentions for this project were to simulate how a security analyst would investigate phishing emails within a real-world Security Operations Center. My goal was to document a simple, repeatable method for analyzing suspicious emails, identifying indicators of compromise (IOCs), and determining the potential risk they pose to users and organizations. By working through one of my actual spam emails, this project demonstrates practical investigative skills used in everyday cybersecurity operations. 

Phishing is a form of social engineering in which attackers attempt to deceive individuals into revealing sensitive information. They will use tactics to try to trick the user into clicking malicious links, or downloading harmful attachments. These messages often impersonate trusted organizations, create a sense of urgency, and rely on psychological manipulation to bypass technical defenses. Common phishing objectives include credential theft, financial fraud, malware delivery, and unauthorized account access.
 
In a SOC environment, phishing emails are one of the most frequent initial access vectors investigated by analysts. Security teams must be quick tovexamine sender information, email headers, embedded links, and supporting infrastructure to determine whether a message is malicious and what actions should be taken. Failure to detect and respond to phishing attempts can lead to data breaches, account compromise, ransomware infections, and broader organizational impact.

<h2>Tools Used</h2>

- <b>An active email address</b> 
- <b>Google Header Analyzer</b>
- <b>IP Lookup Tool</b>
- <b>URL Scanner</b> 

<h2>DISCLAIMER!!</h2>
It's really important to be aware of the "DO NOT'S" when working on this project

- <b>DO NOT click links directly</b> 
- <b>DO NOT download any attachments</b>
- <b>ALWAYS use a scanner instead</b> 
- <b>ALWAYS treat all spam as malicious</b>

<h2>Step 1: Analyze the Sender</h2>
For the first step of the project, I found an email in my spam folder that had potential to be a phishing email. This case displays an email from someone pretending to be Apple iCloud. The first alert would be that my this message popped up in my spam inbox and not the primary inbox. The email alerts that I've been blocked from my iCloud and I must click this link attached to update payment and secure my data. If not, all photos and videos will be deleted from my device. 

<img width="1022" height="685" alt="Screenshot 2026-02-14 at 2 28 18 PM" src="https://github.com/user-attachments/assets/a4605541-202c-42c9-9d67-1b08400344e6" />
<h2>Step 2: Sender Analysis</h2>
Upon opening this email, the first thing I had noticed was a really bad sender address. Below the sender address displays a message that says, "This message was sent from a trusted sender". An image is also displayed mimicking Apple's iCloud logo. They claim to be from the account security and subscription team and they want to help me secure my data before it's too late. The biggest red flag would have to be the giant button at the bottom of the email telling me to update my payment method by clicking the link.

<img width="1019" height="260" alt="Screenshot 2026-02-13 at 10 13 00 PM" src="https://github.com/user-attachments/assets/12b53487-aef6-43b2-9ac5-bf7ac9b38c0e" />
<img width="687" height="251" alt="Screenshot 2026-02-13 at 10 23 13 PM" src="https://github.com/user-attachments/assets/ee77dd0d-3e1b-41ee-a59b-e90511c6f915" />
<img width="867" height="618" alt="Screenshot 2026-02-13 at 10 24 47 PM" src="https://github.com/user-attachments/assets/1401724d-a976-4504-855a-6e14b61a25da" />
<h2>Step 3: Header Analysis</h2>
Next step in this project would be to analyze the header. To find information about this, you can click on the ellipsis located at the top right of the email. Most people know this as the "three dots". When you click on the ellipsis you will look for "show original". Clicking on show original will then open a new window that will display the full email headers, including the message ID, created date, and authentication status(SPF/DKIM). The images below display the results and they both showed that the SPF and DKIM were given a "PASS" rating. The only thing that was given a "FAIL" was the DMARC. For those who don't know, a DMARC is an email security protocol that prevents hackers from using your domain for phishing and spoofing. I noticed this and immediately felt that I had to check the IP address.

<img width="303" height="524" alt="Screenshot 2026-02-13 at 10 26 03 PM" src="https://github.com/user-attachments/assets/c85774e0-a190-48d3-b54b-c0c90521a267" />
<img width="1346" height="523" alt="Screenshot 2026-02-13 at 10 28 26 PM" src="https://github.com/user-attachments/assets/38170ad2-3c3a-4fe2-9530-17dbc6d8fb9a" />
<h2>Step 4: Infrastructure Investigation</h2>
I began this step by using Google's header analyzer. Upon opening the website, you will notice a big text box where you can copy/paste the original email information into the text box. When that's done you can then select the "Analyze The Header" button. You will then be brought to a page that show more information about the email that was sent to you, including the IP address it came from. I then copied the IP address into a free IP checker and found the location and the original domain of the websites name. The domain DID NOT match the one that was written in the original file. This is a prime example of spoofing. Spoofing is when some disguises an email address, sender name, phone number, or website URL to convince you that you are interacting with a trusted source. The real domain is listed in the image below along with the location of the IP address.

<img width="1335" height="481" alt="Screenshot 2026-02-13 at 10 31 11 PM" src="https://github.com/user-attachments/assets/982b618b-4e80-4daf-9718-039b41776066" />
<img width="1120" height="527" alt="Screenshot 2026-02-13 at 10 40 23 PM" src="https://github.com/user-attachments/assets/9243de68-fea2-46b3-b494-a5cb8032137d" />
<h2>Step 5: DKIM</h2>
DomainKeys Identified Mail(DKIM) is an email authentication standard that adds cryptographic signature to outgoing messages, allowing receiving servers to verify that the email truly originated from the domain and was not altered in transit. It protects against spoofing, improves deliverability, and forms a key component of DMARC.

Even though the last step already confirmed that the domain was spoofed, I wanted to take it a step further by using a free DKIM Lookup tool. I found one on Google so I attached the domain name and the results I got confimed my suspicions even more. The results showed that there were no DMARC records found for this domain. There were also multiple flags for blacklist and multiple mail server errors.

<img width="1331" height="665" alt="Screenshot 2026-02-13 at 10 49 08 PM" src="https://github.com/user-attachments/assets/543a781b-7a2f-4e64-ae23-ee398c96718c" />
<h2>Step 6: Identified Indicator of Compromise</h2>
Indicators of Compromise(IOC) are digital forensic artifacts such as malicious IP addresses, file hashes, or unusual DNS request that signal a cyberattack, malware infection, or data breach has already occurred. Security teams use these indicators to detect, contain, and analyze security breaches to minimize damage and prevent future incidents. The IOCs indentified in this project were

- <b>Suspicious Domain</b> 
- <b>Spoofed Sender</b>
- <b>Link Indicators</b>
- <b>Malicious IP</b>

<h2>Step 7: Threat Classification</h2>
I believe that this case would be classified as phishing. All the clues were there from the start. From the email being sent directly to spam, the weird sender address, the geolocation of the IP address, and the clear case for credential harvesting. 

<h2>Step 8: Risk & Impact</h2>
It is important that people understand the risk that are involved in phishing. In this case, if I had acted careless and not used my security mindset then I could have been a vicitm of a scam. If I had clicked that suspicius link I probably would've been brought to a page where I had to enter my login information along with my card information. It only would have gotten worse from that point on. I do believe that hackers target those who are older because in most cases, older people tend to be less tech-savy. They won't know what to look out for unless they're taught. Approximately 22-30% of older adults(ages 65+) have fallen victim to a digital scam or fraud. I don't believe that elders are targeted more for online scams, but I do belive that they are most vulnerable when it comes to this.

<h2>Step 9: Recommended Mitigation</h2>
Phishing can always be prevented if we do our parts to always look out for suspicious activity. We can all choose to think like a defender when dealing with situations on the internet that can turn into a critical risk. After following this project we can begin to take precaution by blocking suspicious IP's, enforcing multi-factor authentication, and even something as simple as user awareness training.

<h2>Final Report</h2>

This project analyzed a suspicious spam/phishing email to simulate how a Security Operations Center analyst investigates a potential email-based threat. This email was examined using a structured workflow that included sender validation, header analysis, infrastructure investigation, link inspection, and indicators of compromise (IOCs).
The analysis revealed multiple characteristics consistent with phishing activity, including spoofed sender identities, suspicious sending infrastructure, deceptive messaging tactics, and embedded links designed to redirect users to potentially malicious destinations. These findings highlight how phishing remains a primary method used by attackers to gain initial access to systems and user accounts.

<h2>Project Outcome</h2>

This investigation demonstrates a simple and repeatable process for analyzing phishing emails using a structured SOC-style workflow. Through this project, the following skills were applied

- <b>email threat analysis</b> 
- <b>header and infrastructure investigation</b>
- <b>OSINT-based reputation checks</b>
- <b>IOC identification and documentation</b>
- <b>threat classification and risk assessment</b> 
- <b>security mindset and mitgation planning</b>

The project highlights how practical analysis of phishing emails can strengthen detection awareness, improve incident triage capabilities, and support real-world defensive cybersecurity roles.
