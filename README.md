<h1>Phishing Email Threat Analysis</h1>

<h2>Introduction</h2>
My intentions for this project were to simulate how a security analyst would investigate phishing emails within a real-world SSecurity Operations Center. My goal was to document a simple, repeatable method for analyzing suspicious emails, identifying indicators of compromise (IOCs), and determining the potential risk they pose to users and organizations. By working through my actual spam emails, this project demonstrates practical investigative skills used in everyday cybersecurity operations. 

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

<h2>Step 2: Sender Analysis</h2>
Upon opening this email, the first thing I had noticed was a really bad sender address. Below the sender address displays a message that says, "This message was sent from a trusted sender". An image is also displayed mimicking Apple's iCloud logo. They claim to be from the account security and subscription team and they want to help me secure my data before it's too late. The biggest red flag would have to be the giant button at the bottom of the email telling me to update my payment method by clicking the link.
