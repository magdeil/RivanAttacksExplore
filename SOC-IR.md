<div align="center">
  <img src="https://github.com/user-attachments/assets/e4d90e60-ee23-4e28-b9c1-ab35e68fed13" alt="Rivan Cyber Training Institute Logo" width="200">
  <h1>RIVAN CYBER TRAINING INSTITUTE</h1>
</div>

<hr>



<hr>

<div align="center">
<img width="1280" height="720" alt="1753705128100" src="https://github.com/user-attachments/assets/c1dc4f0f-5404-4ced-8e8d-5e9ae60eef6c" />
</div>


# Step 1: Opening ELK-STACK and OTRS Ticketing System
* Under the File Button, Click the Open button
<img width="1135" height="490" alt="image" src="https://github.com/user-attachments/assets/86f26c5c-357f-4553-a494-62bf66868e61" />

<hr>

* Under _RivanVMs or on your Downloads folder on D: Drive or C: Drive, Find the OTRS-ELK.v3, open the .vmx file
* If it is not yet extracted we need to extract it to get the .vmx file
* Under _RivanVMs or on your Downloads folder on D: Drive or C: Drive, Find the OTRS-ELK.v3
* then right click on the folder, then select winrar or any other extractor and click extract to*
<img width="789" height="542" alt="image" src="https://github.com/user-attachments/assets/efdd38c3-144d-4396-8b0d-3746ca75d0d2" />

<img width="308" height="287" alt="image" src="https://github.com/user-attachments/assets/78639aeb-928b-4ddb-96de-984fd8aa24e1" />

* Next is opening the .vmx file, double click the .vmx file to open it on VMware
<img width="675" height="368" alt="image" src="https://github.com/user-attachments/assets/14719c06-b135-4dc0-b3ae-e417efdb14e8" />


# Step 2: Powering ELK-Stack and OTRS Ticketing System
* Click Power on this virtual machine, don't forget to check if the Network adapter is set to "NAT"
* If there is a pop-up that the virtual machine is being used just click "Take Ownersship" and if the virtual machine has been moved or copied just click "I copied it"
<img width="1024" height="420" alt="image" src="https://github.com/user-attachments/assets/41644471-d52f-4e31-8bf8-7673154e34a4" />

* Next is logging in on the ELK-STACK, the username and password is root:C1sc0123
<img width="1225" height="597" alt="image" src="https://github.com/user-attachments/assets/a0891d5a-ec6f-4e2f-9f94-ebf51a25315f" />



# Step 2.1: Pre-Requisites - enabling Daemon, Cron, and Mailhog processes
* In the OTRS-ELK.v3 VMware environment, the OTRS Daemon, Cron, and MailHog services must be enabled to support email processing and background operations.
* * OTRS Daemon handles background tasks such as ticket processing, notifications, and email handling.
* *Cron executes scheduled system and maintenance tasks required by OTRS.
* * MailHog provides a local SMTP service for capturing and testing outgoing emails in the lab environment.
* These services are required to ensure proper email sending/receiving and automated task execution before continuing with further configuration.

Use the Following commands to execute the process:

* Change Directory to /opt/otrs 
```bash
cd /opt/otrs/
```
<img width="366" height="81" alt="image" src="https://github.com/user-attachments/assets/88c0320c-fc81-4bbf-929f-7c5ca2dc2abc" />

* Then start the Daemon process and Cron Job using the commands below:
```bash
su -c "bin/otrs.Daemon.pl start" -s /bin/bash otrs
```
<img width="721" height="116" alt="image" src="https://github.com/user-attachments/assets/e19c29d4-ec03-45b5-a1e4-bed3ea0e940d" />

```bash
su -c "bin/Cron.sh start" -s /bin/bash otrs
```
<img width="658" height="84" alt="image" src="https://github.com/user-attachments/assets/2f892ee1-6593-416e-a301-b61436217110" />

* Finally access the mailhog
* After accessing mailhog, we will not be typing or accessing anymore of the VMWare we will not access our TUNAY na PC
```bash
mailhog
```
<img width="597" height="169" alt="image" src="https://github.com/user-attachments/assets/68b9529e-a59b-4a28-ae89-0d9b5f100334" />


# Step 2.3: Editing the IP Address to make it a DNS type of Address
* on your system, we can edit the IP address to make it look more a real-world like SOC
* On your Drive Navigate to this link "c:\Windows\System32\drivers\etc"
<img width="1137" height="347" alt="image" src="https://github.com/user-attachments/assets/6f3fed9b-8544-4d53-bdab-1ab36f7ff3bc" />

* Then right click on hosts file and select either edit with notepad or notepad++
<img width="628" height="422" alt="image" src="https://github.com/user-attachments/assets/45c902bd-8671-4312-b34e-19a6acb12663" />

* We can then add the IP Address of the given IP Address of linux to change the DNS of it, to our liking for example:
* after changing the name, save it and access the GUI of the ticketing system
<img width="675" height="450" alt="image" src="https://github.com/user-attachments/assets/77c13fbe-47a3-4c9c-bc6f-9e44e17d839f" />


# Step 3: Accessing GUI of Ticketing System and Mailhog
* Type the command to show the list of ipv4 addressses, and remember the et0 network adapter
```bash
ip -4 addr
```
<img width="864" height="175" alt="image" src="https://github.com/user-attachments/assets/4998775c-44fe-412b-b688-cf474c1afd2b" />


# Step 3.2: Znuny OTRS Ticketing System
* Access the Index and Customer Dashboard for ticketing system
```bash
http://208.8.8.146/otrs/index.pl?
```
or
```bash
http://socir.ticket.com/otrs/index.pl?
```

* The user and password for the index is root@localhost:C1sc0123, then click enter or login
* We also have users for L1 - L3 agents, we will access this later for ticket handling and ticket escalating process
* We need to use the admin user which is root@localhost to add services, types, queues, etc.
```bash
l1.agent
C1sc0123
```
```bash
l2.agent
C1sc0123
```
```bash
l3.agent
C1sc0123
```
<img width="1913" height="650" alt="image" src="https://github.com/user-attachments/assets/91fcdfd2-3f52-45bd-8d1a-e3bf564eef08" />

<img width="1906" height="947" alt="image" src="https://github.com/user-attachments/assets/fa82b950-3d26-41fc-b459-cd5a9a73b073" />

<hr>

```bash
http://208.8.8.146/otrs/customer.pl
```
or
```bash
http://socir.ticket.com/otrs/customer.pl
```
* The user and password for the customer is user1:C1sc0123, then click enter or login
<img width="1914" height="691" alt="image" src="https://github.com/user-attachments/assets/38965a9c-e11c-4e1b-91d5-dd49fe0d3d10" />

<img width="1916" height="579" alt="image" src="https://github.com/user-attachments/assets/532a925e-7b3e-4c1a-8a7c-5771cddeec71" />




# Step 4: Creating 1st Ticket aka at Service Desk
* On the Customer Panel, we have to create a ticket
* click "Create your 1st ticket"
* at 1st creating tickets on customer panel, itsome of the panels or selection of types, sending it to, service and Service Level Agreement are not yet configured so we have to configure it through admin by adding all levels and incidents.

<img width="574" height="257" alt="image" src="https://github.com/user-attachments/assets/f81c37ac-9e5e-40b7-b282-0cc20c995c7e" />

<img width="388" height="175" alt="image" src="https://github.com/user-attachments/assets/22b37d73-c2a5-42cf-ba68-e0a1c2eac4b8" />

<img width="367" height="111" alt="image" src="https://github.com/user-attachments/assets/e75278d8-ada3-4304-a6bb-73db78dbb947" />

<img width="363" height="56" alt="image" src="https://github.com/user-attachments/assets/c50243a1-4ad3-424a-938c-61b269504e0e" />


# Step 5: Adding and Managing Ticket Types
* On the Admin Side, we can add and manage ticket
* Ticket types are managed through the Admin Panel and are used to define how incidents are categorized within the system. These types help structure ticket handling and ensure consistent incident classification.
* Access the Admin Panel
* Navigate to Ticket Settings / Types
<img width="1615" height="788" alt="image" src="https://github.com/user-attachments/assets/91e774f2-573f-4eaf-9316-cf41b37c1e23" />

* Add or modify ticket types based on operational or security needs
<img width="1672" height="351" alt="image" src="https://github.com/user-attachments/assets/c7cb395b-296e-44f4-9494-ee91aedd6bf7" />


1. Phishing Email Reports
Description: Users report suspicious emails that may contain malicious links or attachments. These emails often impersonate legitimate services or internal contacts.
SOC Task: Analyze the email headers, URLs, and attachments; sandbox suspicious content; block the sender or domain; educate the user.
* Save and apply changes to make the types available in the Customer Panel

<img width="1254" height="262" alt="image" src="https://github.com/user-attachments/assets/32800c2f-941a-4e2a-868e-330afce87c67" />



2. Endpoint Malware Detection
Description: Antivirus or EDR solutions detect malware (e.g., Trojans, ransomware, adware) on user endpoints.
SOC Task: Investigate the detection; isolate the device if necessary; analyze the malware behavior; initiate remediation steps.
* Save and apply changes to make the types available in the Customer Panel

<img width="1211" height="249" alt="image" src="https://github.com/user-attachments/assets/43e31c41-3eb8-4049-a722-7285553ab1f9" />



3. Suspicious Login Activity
Description: Unusual or impossible logins (e.g., logins from different countries within minutes) are flagged by the SIEM or IAM solution.
SOC Task: Verify if login is legitimate or compromised; reset credentials; analyze source IP and geolocation; apply MFA if not enabled.
* Save and apply changes to make the types available in the Customer Panel

<img width="1161" height="202" alt="image" src="https://github.com/user-attachments/assets/647bcc30-e770-44ce-afc0-cf6f7f4bec13" />

* We can then Confirm this on the added types on the admin or on the customer side
* Admin Side
<img width="1904" height="362" alt="image" src="https://github.com/user-attachments/assets/e98154e8-1660-446e-991c-30b4db737e46" />

* Customer Side
<img width="532" height="384" alt="image" src="https://github.com/user-attachments/assets/b2546959-0aa9-4ee2-9e7a-d83c035bfc47" />



# Step 6: Adding and Configuring Queues (SOC Tier Structure)
* Queues were created in the OTRS Admin Panel to simulate a multi-tier Security Operations Center (SOC) workflow. Each queue represents a specific SOC role responsible for handling incidents at different levels of complexity.

* This setup demonstrates how tickets are triaged, escalated, and resolved in real-world security operations.
* On the Admin Panel, click Admin and click Queues
<img width="960" height="619" alt="image" src="https://github.com/user-attachments/assets/492df1b0-c9b8-4d35-bb3f-c4f0ddce2331" />

* Add Queues
<img width="1716" height="318" alt="image" src="https://github.com/user-attachments/assets/e8ecde25-9e12-4252-b47b-292590cfde72" />

* Input this info:

## L1 – Alert Analyst (Frontline / Monitoring & Triage)

* This queue is used for initial alert monitoring and triage. All newly created security-related tickets are first assigned to this queue.

* Escalation Settings (SLA Behavior)
* Escalation rules were configured to enforce timely incident handling:

* Group - Under SOC-L1
* First Response Time: 15 minutes

* * Ensures that alerts are acknowledged quickly after ticket creation.

* Update Time: 15 minutes

* * Requires analysts to provide status updates while the ticket is being investigated.

* Solution Time: 60 minutes

* * Defines the expected time to resolve or escalate the ticket to the next SOC tier.

* Then Click save
<img width="1212" height="791" alt="image" src="https://github.com/user-attachments/assets/b7444e0d-7fd0-42e1-928f-79ef75be0811" />

<img width="383" height="178" alt="image" src="https://github.com/user-attachments/assets/18bb35c6-8acb-4d41-a3ad-86fc8e78bed7" />


## Tier 2 – Incident Responder (Investigation & Escalation)

* This queue is used for incidents escalated from Tier 1 that require deeper investigation and response.

* Escalation Settings (SLA Behavior)
* Escalation rules were configured to enforce timely incident handling:
* Group - Under SOC-L2
* First Response Time: 15 minutes

* * Ensures that alerts are acknowledged quickly after ticket creation.

* Update Time: 15 minutes

* * Requires analysts to provide status updates while the ticket is being investigated.

* Solution Time: 60 minutes

* * Defines the expected time to resolve or escalate the ticket to the next SOC tier.

* Then click Save

<img width="1252" height="785" alt="image" src="https://github.com/user-attachments/assets/f90da185-74d9-47a6-9053-2bb98734f9df" />

<img width="408" height="191" alt="image" src="https://github.com/user-attachments/assets/92512890-61f2-4dc0-b000-6c97e7cd4995" />


## L3 – Threat Hunter / Forensics Expert

* This queue is used for advanced analysis of incidents that require threat hunting or forensic investigation beyond standard incident response.
* Escalation Settings (SLA Behavior)
* Escalation rules were configured to enforce timely incident handling:
* Group - Under SOC-L3
* First Response Time: 15 minutes

* * Ensures that alerts are acknowledged quickly after ticket creation.

* Update Time: 15 minutes

* * Requires analysts to provide status updates while the ticket is being investigated.

* Solution Time: 60 minutes

* * Defines the expected time to resolve or escalate the ticket to the next SOC tier.

* Then click Save

<img width="1326" height="805" alt="image" src="https://github.com/user-attachments/assets/65c24a07-6929-412e-909d-8fc887d51b3c" />


<img width="385" height="162" alt="image" src="https://github.com/user-attachments/assets/36920e3f-f504-4b69-9750-850d3140ea2a" />


### We can then check if it makes the changes
* On admin side
<img width="1610" height="245" alt="image" src="https://github.com/user-attachments/assets/fd983ad3-4ff2-43b4-9289-06d12a6fabff" />

* On customer side
<img width="557" height="366" alt="image" src="https://github.com/user-attachments/assets/1ad9de30-8e68-4b88-8da1-9051b8565a87" />

# Step 7: Adding and Configuring Templates 0 - 5/6
* Response templates were created in the OTRS Admin Panel to standardize ticket communication at each SOC escalation level. These templates allow analysts to send consistent and professional responses without manually typing messages.

* Templates were created from Level 0 (auto reply) up to Level 5/6 (management and resolution).
* Navigate to Admin → Template Management → Add Template

<img width="1415" height="784" alt="image" src="https://github.com/user-attachments/assets/cda8fa65-5369-4b6e-ad6e-f0eeef90b999" />


* Click add template
<img width="602" height="267" alt="image" src="https://github.com/user-attachments/assets/0954fec3-d62f-44a3-a3fd-19f3db6abdb1" />


* Create Template 0
* Under Type, select:
* * Answer

* Under Name, enter:
* * Template 0 – Auto Reply

* In the Template Content field, enter the following message:
```bash
Hello,

Your ticket has been received by the Service Desk.
Our team is currently reviewing the issue and will provide updates shortly.

Thank you.
```

* Set Validity to:
* * valid

* Click Save
<img width="1326" height="618" alt="image" src="https://github.com/user-attachments/assets/1ec804d6-9ccf-45e1-8a77-39c9e377e5d5" />


* After that select only L1 because it is linked to the template 0 - auto reply, for best practice do not select them all, after that click save and finish
Template 0 (Auto Reply) was linked only to the Tier 1 queue to ensure users receive a single acknowledgement upon ticket creation.
<img width="429" height="261" alt="image" src="https://github.com/user-attachments/assets/cc719a7d-561c-4270-b1cb-5273e4060e31" />

## Step 7.2 Creating Template 1 – Initial Analysis (Tier 1)
* Template 1 is used to inform the user that their ticket is undergoing initial analysis and triage by the Tier 1 SOC team.
* Navigate to Admin → Template Management → Add Template

* Under Type, select:
* * Answer

* Under Name, enter:
* * Template 1 – Initial Analysis

* In the Template Content field, enter the following message:
```bash
Hello,

We are currently reviewing your reported issue and performing initial analysis.
At this stage, we are validating the alert and checking for any immediate risks.

We will provide an update once this process is complete.

Thank you.
```

* Set Validity to:
* * valid

* Click Save
<img width="1383" height="608" alt="image" src="https://github.com/user-attachments/assets/11d5b53c-d5ce-45e2-8160-8ba695d28d83" />

* Queue Assignment
* Link this template to the following queue:
✔ L1 – Alert Analyst
Do NOT assign this template to higher tiers
* After that click save and finish
<img width="436" height="256" alt="image" src="https://github.com/user-attachments/assets/2cb22a74-2994-44cf-8813-b798725ec2bf" />

## Step 7.3: Creating Template 2 – Investigation Ongoing (Tier 2)
* Template 2 is used to notify the user that the ticket has been escalated to Tier 2 for deeper investigation and incident response.
* Navigate to Admin → Template Management → Add Template

* Under Type, select:
* * Answer

* Under Name, enter:
* * Template 2 – Investigation Ongoing

* In the Template Content field, enter the following message:
```bash
Hello,

Your ticket has been escalated for further investigation.
Our team is analyzing relevant logs and systems to determine the root cause of the issue.

We will provide updates as the investigation progresses.

Thank you.
```

* Set Validity to:
* * valid

* Click Save
<img width="1505" height="667" alt="image" src="https://github.com/user-attachments/assets/148428a0-2e74-4667-8f1e-02524e828ae1" />

* Queue Assignment
* Link this template to the following queue:
✔ L2 – Incident Responder
* Do NOT assign this template to other queues
* Purpose in Workflow
* * Informs the user of escalation
* * Sets expectation for deeper analysis
* * Aligns communication with SOC escalation flow
* Then click Save and finish
<img width="457" height="279" alt="image" src="https://github.com/user-attachments/assets/e185e8f7-5db7-44ca-9868-f2d9d24b7f2a" />


## Step 7.4: Creating Template 3 – Advanced Analysis / Resolution (Tier 3)
* Template 3 is used when a ticket reaches Tier 3 for advanced analysis or final resolution. This may involve threat hunting, forensic review, or confirmation that no further action is required.
* Navigate to Admin → Template Management → Add Template

* Under Type, select:
* * Answer

* Under Name, enter:
* * Template 3 – Advanced Analysis / Resolution

* In the Template Content field, enter the following message:
```bash
Hello,

Your ticket is currently undergoing advanced analysis.
Our security team is reviewing the findings and applying final actions as needed.

You will be notified once the analysis is completed or the issue is resolved.

Thank you.
```
* Set Validity to:
* * valid

* Click Save
<img width="1439" height="659" alt="image" src="https://github.com/user-attachments/assets/b31a04a4-d318-4064-aa89-7fbcf8618768" />

* Queue Assignment

* * Link this template to the following queue:
✔ L3 – Threat Hunter / Forensics Expert
* Do NOT assign this template to other queues

* Purpose in Workflow
* * Communicates advanced investigation status
* * Indicates final-stage handling
* * Keeps user informed without exposing technical details
  * Click save and finish
<img width="531" height="274" alt="image" src="https://github.com/user-attachments/assets/fe11ffe9-fa12-4777-998e-017e16e14b1b" />

* Overview of added templates and queues
<img width="1618" height="233" alt="image" src="https://github.com/user-attachments/assets/0ab0850c-ef36-42e7-9393-7d14c3ec6a37" />

# Step 8: Creating Ticket 2nd run
* On Customer Side Panel, Create again your 1st ticket
* click "Create your 1st ticket"
<img width="574" height="257" alt="image" src="https://github.com/user-attachments/assets/f81c37ac-9e5e-40b7-b282-0cc20c995c7e" />

* On type, select Phishing Email Reports
<img width="409" height="226" alt="image" src="https://github.com/user-attachments/assets/5f9ef216-f06c-4deb-8689-87cfee8f40fa" />


* Send it to: "L1 - Alert Analyst"
<img width="396" height="184" alt="image" src="https://github.com/user-attachments/assets/ebe5fa70-3285-4408-9538-9f18aff4fcd8" />


* Subject (example):
```
Suspicious Email Received – Possible Phishing
```

Text (example content):
``` bash
Good day,

I received an email claiming to be from our IT department asking me to click a link and verify my account.

The email looks suspicious and may be a phishing attempt.
Please investigate.

Thank you.
```

* Leave these EMPTY for now:

* * Service

* * SLA

* Click Submit

✅ Ticket will be created

✅ Template 0 (Auto Reply) should trigger

✅ Ticket should land in L1 – Alert Analyst

<img width="1177" height="753" alt="image" src="https://github.com/user-attachments/assets/a4f85cb5-a4c1-4706-ae2d-3a7b4ddbb6f2" />

* After submitting the ticket, the ticket can now be seen to the customer or user
<img width="1907" height="234" alt="image" src="https://github.com/user-attachments/assets/4a8fcc25-4dc4-4190-9ce1-8217f2cba6fc" />

# Step 9: Verifying and Applying Template
* For demonstration purposes, a single administrative agent account was used to simulate L1, L2, and L3 SOC roles. Tickets were manually routed between queues to demonstrate escalation workflows.
* Under Index panel → Tickets → Queues

<img width="957" height="483" alt="image" src="https://github.com/user-attachments/assets/b29d206f-009a-4cad-a274-78afeee0d3d7" />

* Then Click the L1 - Alert Ticket
<img width="601" height="318" alt="image" src="https://github.com/user-attachments/assets/865113a5-fc6e-4d96-a9df-f0ff8adcd08a" />
<img width="1904" height="647" alt="image" src="https://github.com/user-attachments/assets/2a7a49fc-cc8d-4aac-b701-8da0461af1ee" />

## Step 9.3: Applying Template 0 - Auto Reply
* This step demonstrates how the Service Desk or SOC analyst applies the appropriate response template during the early stage of ticket handling.
* We can now then apply the appropriate template by clicking the reply button and the blank message
* But in Real-World Situations, tickets are automatically will receive an email or an corresponding message whatever the siuation is. For that we will Continue to add auto response to our ticketing system.
<img width="1464" height="589" alt="image" src="https://github.com/user-attachments/assets/fe752198-916a-4b5d-8860-e1245a169fad" />

## Sub-Step 9.4: Configuring Auto Response aka Template 0 - Auto Reply
* Create a True Auto Response (System-Level)
* Go to:
* * Admin → Auto Responses → Add Auto Response
<img width="1003" height="422" alt="image" src="https://github.com/user-attachments/assets/a3fb4fec-311e-483a-a3dc-9a5ca4cebc9c" />

<img width="338" height="184" alt="image" src="https://github.com/user-attachments/assets/0a383f2e-b3a0-4810-b057-ff1d2d0274c7" />

* Configure as follows:
* Name:
```
Auto Reply – Ticket Received
```

* Subject:
```
[Ticket#<OTRS_TICKET_TicketNumber>] Ticket Received
```

* Response Body:
```
Hello,

Your ticket has been successfully received by the Security Operations Center.

Our team is currently reviewing the issue and will provide updates as soon as possible.

Please do not reply to this message unless additional information is required.

Thank you,
SOC Team
```

* Type - auto reply
* Validity:
✔ valid

➡ Click Save
<img width="1507" height="718" alt="image" src="https://github.com/user-attachments/assets/62b31401-c4e4-4a8c-a150-ed4cdb5d0c67" />


## Sub-Step 9.4: Assign Auto Response to L1 Queue (CRITICAL)
* Go to Admin → Queues → L1 – Alert Analyst
<img width="726" height="571" alt="image" src="https://github.com/user-attachments/assets/ef360851-a52b-4e96-bf51-d808169be53c" />

* Under Related Actions, find "Queues → Auto Responses :
<img width="277" height="543" alt="image" src="https://github.com/user-attachments/assets/38a2318f-2669-4f1f-a1e2-cd2cbce54106" />


* Then Click "L1 - Alert Analyst":
<img width="806" height="215" alt="image" src="https://github.com/user-attachments/assets/ce5affb3-83c4-4cb2-9c68-88eb2d510ede" />

* Configure:
auto reply: Auto Reply – Ticket Received
➡ Click Save and finish
<img width="1014" height="269" alt="image" src="https://github.com/user-attachments/assets/a087d6f1-69dd-42b6-8f7e-e244d4d4ff18" />

## Re-continouing Sub-Step 9.2.2: Automatic Acknowledgement or automatic reply upon ticket creation
* Configure as follow to have an auto reply
* On the customer side, recreate another ticket, then click submit
<img width="350" height="189" alt="image" src="https://github.com/user-attachments/assets/0f876157-cd79-4210-87f6-e85aea813dc6" />

<img width="1594" height="802" alt="image" src="https://github.com/user-attachments/assets/412c7ee1-db34-40e1-a5a9-7b5852e3bd11" />

* After submitting, you will then receive an auto response by the system
<img width="1642" height="887" alt="image" src="https://github.com/user-attachments/assets/2a7cc888-f1bf-4f88-b1db-0c606ef3a7fb" />

# Step 9.4: Applying Template 1 on L1 - Alert Analysis: 
* We can now then apply the appropriate template by clicking the reply button and the blank message
* Under Tickets -> click the given ticket and select template 1 - Initial Analysis
* From there another TAB will automatically open and click the -> send mail button
<img width="1416" height="795" alt="image" src="https://github.com/user-attachments/assets/3b0bbd15-bb40-47eb-a572-4d9c8c9c58d7" />

* After sending the mail, the customer will receive the Template 1 – Initial Analysis response
* On the customer side panel, click the ticket and verify that the response is received
* The customer should see a message stating that the ticket is undergoing initial analysis and triage

![Customer side showing Template 1 response received](screenshots/01-customer-template1.png)


# Step 10: Escalating Ticket from L1 to L2 – Incident Responder
* After the L1 Analyst has completed the initial triage and determined that the ticket requires deeper investigation, the ticket must be escalated to the L2 queue.
* This simulates a real-world SOC escalation where Tier 1 analysts pass complex incidents to Tier 2 Incident Responders.

* On the Admin/Agent Panel (Index), open the ticket that was handled by L1
* Click the ticket to view its details

![Opening the ticket from L1 queue](screenshots/02-agent-ticket-l1.png)

## Step 10.1: Moving the Ticket Queue from L1 to L2
* To escalate the ticket, we need to move it from the L1 queue to the L2 queue
* Inside the ticket, click the "Move" button or the Queue dropdown
* Select "L2 – Incident Responder" from the queue list
* This action transfers the ticket to the L2 queue for further investigation

![Moving ticket to L2 queue](screenshots/03-move-to-l2.png)

* After moving the ticket, verify that it now appears under the L2 – Incident Responder queue
* Navigate to Tickets → Queues → L2 – Incident Responder

![Ticket now visible in L2 queue](screenshots/04-ticket-in-l2.png)

## Step 10.2: Applying Template 2 – Investigation Ongoing on L2
* Now that the ticket is in the L2 queue, the Incident Responder must apply the appropriate template
* Click the ticket under the L2 queue
* Click the Reply button
* Select "Template 2 – Investigation Ongoing" from the template dropdown
* The template content will auto-fill the response body
* Click the Send Mail button

![Applying Template 2 in L2](screenshots/05-apply-template2-l2.png)

* After sending, the customer will receive a notification that their ticket has been escalated for further investigation
* On the customer side, verify that the response from L2 is visible

![Customer side showing Template 2 response](screenshots/06-customer-template2.png)

<hr>

# Step 11: Escalating Ticket from L2 to L3 – Threat Hunter / Forensics Expert
* If the L2 Incident Responder determines that the incident requires advanced threat hunting or forensic analysis, the ticket is escalated to L3.
* This represents the highest level of technical escalation in the SOC workflow.

## Step 11.1: Moving the Ticket Queue from L2 to L3
* Inside the ticket (currently in L2 queue), click the "Move" button or the Queue dropdown
* Select "L3 – Threat Hunter / Forensics Expert" from the queue list

![Moving ticket from L2 to L3 queue](screenshots/07-move-to-l3.png)

* Verify that the ticket now appears under the L3 – Threat Hunter / Forensics Expert queue
* Navigate to Tickets → Queues → L3 – Threat Hunter / Forensics Expert

![Ticket now visible in L3 queue](screenshots/08-ticket-in-l3.png)

## Step 11.2: Applying Template 3 – Advanced Analysis / Resolution on L3
* Click the ticket under the L3 queue
* Click the Reply button
* Select "Template 3 – Advanced Analysis / Resolution" from the template dropdown
* The template content will auto-fill the response body
* Click the Send Mail button

![Applying Template 3 in L3](screenshots/09-apply-template3-l3.png)

* After sending, the customer will receive a notification that their ticket is undergoing advanced analysis
* On the customer side, verify that the response from L3 is visible

![Customer side showing Template 3 response](screenshots/10-customer-template3.png)

<hr>

# Step 12: Creating Template 4 – Escalation to Management
* Template 4 is used when a security incident is severe enough to require management-level awareness and decision-making. This is typically triggered during high-impact incidents such as data breaches, ransomware attacks, or incidents affecting critical infrastructure.
* Navigate to Admin → Template Management → Add Template

* Under Type, select:
* * Answer

* Under Name, enter:
* * Template 4 – Escalation to Management

* In the Template Content field, enter the following message:
```bash
Hello,

This is to inform you that your reported security incident has been escalated to the SOC Management team due to its severity and potential impact.

Our leadership is now involved in coordinating the response and will ensure that all necessary actions are taken to contain and remediate the issue.

You will receive further updates as the situation progresses.

Thank you,
SOC Management
```

* Set Validity to:
* * valid

* Click Save

![Creating Template 4 in Admin Panel](screenshots/11-create-template4.png)

* Queue Assignment
* Link this template to the following queue:
✔ L3 – Threat Hunter / Forensics Expert
* This template is assigned to L3 because management escalation typically occurs at the highest technical tier
* Do NOT assign this template to lower-tier queues
* Then click Save and finish

![Linking Template 4 to L3 queue](screenshots/12-link-template4-l3.png)


## Step 12.1: Creating Template 5 – Closure / Post-Incident Review
* Template 5 is the final communication template used to formally close a ticket after the incident has been fully investigated, contained, and remediated. It informs the customer that the case is resolved and may reference a post-incident review.
* Navigate to Admin → Template Management → Add Template

* Under Type, select:
* * Answer

* Under Name, enter:
* * Template 5 – Closure / Post-Incident Review

* In the Template Content field, enter the following message:
```bash
Hello,

We are pleased to inform you that your reported security incident has been fully investigated and resolved.

Summary of Actions Taken:
- The incident was analyzed and classified.
- Containment and remediation actions were applied.
- Relevant systems have been verified and restored to normal operation.

A post-incident review will be conducted to improve our processes and prevent similar incidents in the future.

If you have any further concerns, please do not hesitate to create a new ticket.

Thank you for your patience and cooperation.

Best regards,
SOC Team
```

* Set Validity to:
* * valid

* Click Save

![Creating Template 5 in Admin Panel](screenshots/13-create-template5.png)

* Queue Assignment
* Link this template to ALL queues:
✔ L1 – Alert Analyst
✔ L2 – Incident Responder
✔ L3 – Threat Hunter / Forensics Expert
* This template is available at all levels because ticket closure may happen at any tier depending on the incident complexity
* Then click Save and finish

![Linking Template 5 to all queues](screenshots/14-link-template5-all.png)

* Overview of all added templates (Templates 0–5)

![Template overview showing all 6 templates](screenshots/15-template-overview.png)

<hr>

# Step 13: Applying Template 4 – Escalation to Management
* If the situation requires management involvement, apply Template 4 while the ticket is still in L3
* Click the ticket under the L3 queue
* Click the Reply button
* Select "Template 4 – Escalation to Management" from the template dropdown
* Click the Send Mail button

![Applying Template 4 on the ticket](screenshots/16-apply-template4.png)

* After sending, the customer will be notified that the incident has been escalated to SOC Management
* On the customer side, verify the response

![Customer side showing Template 4 response](screenshots/17-customer-template4.png)

<hr>

# Step 14: Closing / Resolving the Ticket
* After the incident has been fully handled and all necessary actions have been taken, the ticket must be formally closed
* This step demonstrates the complete resolution workflow

## Step 14.1: Applying Template 5 – Closure / Post-Incident Review
* Click the ticket (in whichever queue it currently resides)
* Click the Reply button
* Select "Template 5 – Closure / Post-Incident Review" from the template dropdown
* Click the Send Mail button

![Applying Template 5 closure template](screenshots/18-apply-template5.png)

## Step 14.2: Changing Ticket State to Closed
* After sending the closure notification, we need to change the ticket state
* Inside the ticket, look for the "State" dropdown or click the "Close" action
* Change the State to:
* * "closed successful" – if the incident was resolved successfully
* * "closed unsuccessful" – if the incident could not be fully resolved

![Changing ticket state to closed successful](screenshots/19-close-ticket.png)

* After closing the ticket, verify on both the Admin and Customer side

* Admin Side – the ticket should show as "Closed" with the appropriate status
![Admin side showing closed ticket](screenshots/20-admin-closed.png)

* Customer Side – the customer should see the ticket marked as closed along with the closure message
![Customer side showing closed ticket](screenshots/21-customer-closed.png)

<hr>

# Step 15: Verifying Email Notifications on MailHog
* MailHog captures all outgoing emails from the OTRS system for testing purposes
* This step verifies that all ticket-related email notifications were properly sent throughout the SOC workflow

* On your browser, access MailHog using the IP address of the ELK-OTRS VM on port 8025:
```bash
http://(IP Address of ELK-OTRS VM):8025
```

* MailHog should display all the emails that were sent during the ticket lifecycle:
* * Auto Reply (Template 0) – Acknowledgement of ticket creation
* * Template 1 – Initial Analysis notification
* * Template 2 – Investigation Ongoing notification (after L1 → L2 escalation)
* * Template 3 – Advanced Analysis notification (after L2 → L3 escalation)
* * Template 4 – Escalation to Management notification
* * Template 5 – Closure / Post-Incident Review notification

![MailHog inbox showing all ticket notification emails](screenshots/22-mailhog-inbox.png)

* Click on each email to verify the content matches the templates that were configured
* This confirms that the email pipeline is working correctly from OTRS through MailHog

![MailHog showing email content](screenshots/23-mailhog-email.png)

<hr>

# Step 16: Adding and Configuring Services
* Services define the type of IT or security service that the ticket is related to. Configuring services helps categorize tickets more precisely and ties into SLA management.
* Navigate to Admin → Services → Add Service

![Admin panel navigating to Services](screenshots/24-admin-services.png)

## Step 16.1: Adding Service – Security Monitoring
* Under Name, enter:
```
Security Monitoring
```
* Set Validity to:
* * valid
* Click Save

![Adding Security Monitoring service](screenshots/25-add-service1.png)

## Step 16.2: Adding Service – Incident Response
* Under Name, enter:
```
Incident Response
```
* Set Validity to:
* * valid
* Click Save

![Adding Incident Response service](screenshots/26-add-service2.png)

## Step 16.3: Adding Service – Threat Intelligence
* Under Name, enter:
```
Threat Intelligence
```
* Set Validity to:
* * valid
* Click Save

![Adding Threat Intelligence service](screenshots/27-add-service3.png)

* Overview of all added services

![Admin panel showing all 3 services configured](screenshots/28-services-overview.png)

## Step 16.4: Assigning Services to Customer Users
* For customers to select a service when creating a ticket, the services must be linked to the customer user
* Navigate to Admin → Customer Users ↔ Services
* Select the customer user (e.g., user1)
* Check all services that should be available:
✔ Security Monitoring
✔ Incident Response
✔ Threat Intelligence
* Click Save

![Linking services to customer user](screenshots/29-link-services-customer.png)

* Verify on the Customer Side that the services now appear when creating a new ticket

![Customer side showing available services](screenshots/30-customer-services.png)

<hr>

# Step 17: Adding and Configuring Service Level Agreements (SLA)
* SLAs define the expected response and resolution times for each service. They ensure that tickets are handled within agreed-upon timeframes based on incident priority.
* Navigate to Admin → Service Level Agreements → Add SLA

![Admin panel navigating to SLA management](screenshots/31-admin-sla-nav.png)

## Step 17.1: Adding SLA – Critical Incident SLA
* Under Name, enter:
```
Critical Incident SLA
```

* Under Service, select:
* * Security Monitoring
* * Incident Response
* * Threat Intelligence

* Configure Escalation Times:
* * First Response Time: 10 minutes
* * Update Time: 15 minutes
* * Solution Time: 30 minutes

* Set Validity to:
* * valid
* Click Save

![Creating Critical Incident SLA](screenshots/32-create-critical-sla.png)

## Step 17.2: Adding SLA – Standard Incident SLA
* Under Name, enter:
```
Standard Incident SLA
```

* Under Service, select:
* * Security Monitoring
* * Incident Response
* * Threat Intelligence

* Configure Escalation Times:
* * First Response Time: 30 minutes
* * Update Time: 60 minutes
* * Solution Time: 120 minutes

* Set Validity to:
* * valid
* Click Save

![Creating Standard Incident SLA](screenshots/33-create-standard-sla.png)

* Overview of all added SLAs

![Admin panel showing all configured SLAs](screenshots/34-sla-overview.png)

* Verify on the Customer Side that the SLA options now appear when creating a new ticket

![Customer side showing available SLAs](screenshots/35-customer-sla.png)

<hr>

# Step 18: Creating a Complete Ticket with Services and SLA
* Now that all configurations are complete, we can create a fully configured ticket with all fields populated
* On the Customer Panel, click "Create Ticket" or "New Ticket"

* Fill in the following:
* * Type: Phishing Email Reports
* * To/Queue: L1 – Alert Analyst
* * Service: Security Monitoring
* * SLA: Critical Incident SLA

* Subject:
```
Suspicious Link Detected – Possible Credential Harvesting
```

* Text:
```bash
Good day,

I received an email from an unknown sender with a link that redirects to a login page mimicking our company portal.

I did not click the link but I believe it is a phishing attempt targeting employee credentials.

Please investigate immediately.

Thank you.
```

* Click Submit

![Creating fully configured ticket](screenshots/36-create-full-ticket.png)

✅ Ticket will be created with full configuration

✅ Auto Reply should trigger automatically

✅ Service and SLA are now linked to the ticket

✅ Ticket should land in L1 – Alert Analyst with proper SLA timers

* After submitting, verify the ticket on both sides:
* Admin Side – ticket should show Type, Queue, Service, and SLA
![Admin side showing fully configured ticket with SLA timer](screenshots/37-admin-full-ticket.png)

* Customer Side – customer should see the ticket with auto reply
![Customer side showing the new ticket](screenshots/38-customer-full-ticket.png)

<hr>

# Step 19: Monitoring Logs on ELK-Stack (Kibana)
* The ELK-Stack (Elasticsearch, Logstash, Kibana) is used to monitor and analyze security logs in real-time. In a real-world SOC, this is where analysts observe incoming alerts and correlate events.

* On your browser, access Kibana using the IP address of the ELK-OTRS VM on port 5601:
```bash
http://(IP Address of ELK-OTRS VM):5601
```

* The credentials for Kibana are elastic:C1sc0123
* Click Login

![Kibana login page](screenshots/39-kibana-login.png)

## Step 19.1: Navigating to Discover
* After logging in, click the ☰ Hamburger icon on the top-left
* Click "Discover" under the Analytics section
* This view shows all ingested logs in real-time

![Kibana Discover page showing logs](screenshots/40-kibana-discover.png)

## Step 19.2: Filtering Logs
* On the Discover page, we can filter logs to find specific security events
* Use the search bar at the top to filter logs, for example:
```bash
message: "authentication" OR message: "login" OR message: "failed"
```

* You can also adjust the time range using the time picker on the top-right corner
* Set it to "Last 15 minutes" or "Last 1 hour" depending on when the activity occurred

![Kibana showing filtered logs](screenshots/41-kibana-filtered.png)

## Step 19.3: Understanding the Log Entries
* Each log entry contains important information:
* * @timestamp – when the event occurred
* * message – the actual log content
* * host.name – the system that generated the log
* * log.file.path – the source file of the log

* These logs help SOC analysts:
* * Detect suspicious activities
* * Correlate events across systems
* * Investigate incidents with evidence
* * Create reports for management

![Expanded log entry showing all fields](screenshots/42-kibana-expanded.png)

<hr>

# Step 20: Complete SOC Incident Response Workflow Summary
* Below is a summary of the complete SOC-IR workflow that was demonstrated in this documentation:

## Workflow Overview

### 1. Ticket Creation (Service Desk)
* Customer/User reports a security incident through the OTRS Customer Portal
* Ticket is categorized by Type (e.g., Phishing, Malware, Suspicious Login)
* Ticket is assigned to a Queue (L1 – Alert Analyst)
* Service and SLA are selected

### 2. Auto Acknowledgement (Template 0)
* The system automatically sends an acknowledgement email to the customer
* This confirms that the ticket has been received and is being reviewed

### 3. Tier 1 – Alert Analyst (L1)
* L1 Analyst performs initial triage and analysis
* Template 1 – Initial Analysis is sent to the customer
* If the incident requires deeper investigation → Escalate to L2

### 4. Tier 2 – Incident Responder (L2)
* L2 Analyst investigates the incident in detail
* Template 2 – Investigation Ongoing is sent to the customer
* Analyzes logs, systems, and artifacts
* If the incident requires advanced forensics → Escalate to L3

### 5. Tier 3 – Threat Hunter / Forensics Expert (L3)
* L3 Expert performs advanced analysis, threat hunting, or forensic investigation
* Template 3 – Advanced Analysis / Resolution is sent to the customer
* If the incident is severe → Template 4 – Escalation to Management is sent

### 6. Resolution and Closure
* After the incident is fully handled:
* * Template 5 – Closure / Post-Incident Review is sent
* * Ticket state is changed to "closed successful"
* * Post-incident review is scheduled

### 7. Monitoring and Verification
* MailHog verifies that all email notifications were properly sent
* ELK-Stack (Kibana) monitors and displays security logs for analysis
* SLA timers ensure tickets are handled within the agreed timeframes

<hr>

<div align="center">

### Escalation Flow Diagram

```
┌─────────────────────────────────────────────────────────────────────────┐
│                        CUSTOMER / END USER                             │
│                     (Reports Security Incident)                        │
└───────────────────────────────┬─────────────────────────────────────────┘
                                │
                                ▼
┌─────────────────────────────────────────────────────────────────────────┐
│                     SERVICE DESK (Ticket Created)                      │
│              ✉ Template 0 – Auto Reply sent to customer                │
│              📋 Type, Queue, Service, SLA assigned                     │
└───────────────────────────────┬─────────────────────────────────────────┘
                                │
                                ▼
┌─────────────────────────────────────────────────────────────────────────┐
│              L1 – ALERT ANALYST (Monitoring & Triage)                  │
│              ✉ Template 1 – Initial Analysis                           │
│              ⏱ First Response: 15 min | Solution: 60 min              │
│                                                                         │
│         ┌─── Resolved? ──► Close Ticket (Template 5)                   │
│         │                                                               │
│         └─── Needs Escalation? ──────────────┐                         │
└──────────────────────────────────────────────┬──────────────────────────┘
                                               │
                                               ▼
┌─────────────────────────────────────────────────────────────────────────┐
│          L2 – INCIDENT RESPONDER (Investigation & Escalation)          │
│          ✉ Template 2 – Investigation Ongoing                          │
│          ⏱ First Response: 15 min | Solution: 60 min                  │
│                                                                         │
│         ┌─── Resolved? ──► Close Ticket (Template 5)                   │
│         │                                                               │
│         └─── Needs Escalation? ──────────────┐                         │
└──────────────────────────────────────────────┬──────────────────────────┘
                                               │
                                               ▼
┌─────────────────────────────────────────────────────────────────────────┐
│       L3 – THREAT HUNTER / FORENSICS EXPERT (Advanced Analysis)        │
│       ✉ Template 3 – Advanced Analysis / Resolution                    │
│       ⏱ First Response: 15 min | Solution: 60 min                     │
│                                                                         │
│         ┌─── Severe? ──► Template 4 – Escalation to Management         │
│         │                                                               │
│         └─── Resolved ──► Close Ticket (Template 5)                    │
└─────────────────────────────────────────────────────────────────────────┘
                                │
                                ▼
┌─────────────────────────────────────────────────────────────────────────┐
│                     TICKET CLOSED SUCCESSFULLY                         │
│              ✉ Template 5 – Closure / Post-Incident Review             │
│              📊 Post-Incident Review Scheduled                         │
│              📧 All emails verified via MailHog                        │
│              📈 Logs monitored via ELK-Stack (Kibana)                  │
└─────────────────────────────────────────────────────────────────────────┘
```

</div>

<hr>

<div align="center">
  <h2>End of SOC Incident Response Documentation</h2>
  <p><strong>RIVAN CYBER TRAINING INSTITUTE</strong></p>
  <p>This documentation covers the complete setup and workflow of a Security Operations Center (SOC) Incident Response system using OTRS (Znuny) Ticketing System, ELK-Stack (Kibana), and MailHog within a VMware lab environment.</p>
</div>
