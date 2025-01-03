##  9.2 Lesson Plan: Email Networks and Security
 
### Overview

Today's class builds on previous networking concepts, with a focus on sending, receiving, and securing emails. If time remains, we will also review the various topics covered in the previous two weeks of classes.


### Class Objectives

By the end of class, students should be able to:

- Validate DNS records using `nslookup`.

- Describe the process, protocols, and headers associated with email communication.

- Analyze email headers to identify suspicious content. 


### Instructor Notes

- The second half of today's class is a review of the topics covered in Modules 8 and 9. However, if you need more time completing lectures or activities from 9.1 or 9.2, you can use that review time to catch up. 

### Lab Environment

<details><summary>Lab Details</summary>
<br>


You will use your web lab virtual machine for today's activities. Please note that instructors and students have different access credentials.

  - Instructor access:
    - Username: `instructor`
    - Password: `instructor`
  - Student access:
    - Username: `sysadmin`
    - Password: `cybersecurity`

</details>

 
### Online Classroom Strategies 

Refer to the following guidelines and best practices for conducting this class online: 

- [Cybersecurity Online Classroom Strategies](../../../00-Teaching-Staff-Prework/OnlineStrategies.md)


### Module Day 2 Contents

- [x] [01. Instructor Do: Welcome and Introduction](LessonPlan.md#01-instructor-do-welcome-and-introduction-005)
- [x] [02. Instructor Do: DNS Record Types](LessonPlan.md#02-instructor-do-dns-record-types-010)
- [x] [03. Student Do: DNS Record Types Activity](LessonPlan.md#03-student-do-dns-record-types-activity-010)
- [x] [04. Instructor Do: Review DNS Record Types Activity](LessonPlan.md#04-instructor-do-review-dns-record-types-activity-010)
- [x] [05. Instructor Do: Introduction to Email Networking](LessonPlan.md#05-instructor-do-introduction-to-email-networking-010)
- [x] [06. Student Do: Email Networking Activity](LessonPlan.md#06-student-do-email-networking-activity-015)
- [x] [07. Instructor Do: Review Email Networking Activity](LessonPlan.md#07-instructor-do-review-email-networking-activity-010)
- [x] [08. Instructor Do: Email Security Issues](LessonPlan.md#08-instructor-do-email-security-issues-015)
- [x] [09. Student Do: Email Security Activity](LessonPlan.md#09-student-do-email-security-activity-015)
- [x] [10. Instructor Do: Review Email Security Activity](LessonPlan.md#10-instructor-do-review-email-security-activity-010)
- [x] [11. Break](LessonPlan.md#11-break-015)
- [x] [12. Optional Instructor Do: Setting Up Networking Concepts Activity](LessonPlan.md#12-optional-instructor-do-setting-up-networking-concepts-activity-005)
- [x] [13. Student Do: Networking Concepts Review Activity](LessonPlan.md#13-student-do-networking-concepts-review-activity-015)
- [x] [14. Instructor Do: Review Networking Review Activity](LessonPlan.md#14-instructor-do-review-networking-review-activity-008)
- [x] [15. Optional Instructor Do: Setting Up Networking Attacks Activity](LessonPlan.md#15-optional-instructor-do-setting-up-networking-attacks-activity-005)
- [x] [16. Optional Student Do: Networking Attacks Activity](LessonPlan.md#16-optional-student-do-networking-attacks-activity-015)
- [x] [17. Optional Instructor Review: Networking Attacks Activity](LessonPlan.md#17-optional-instructor-review-networking-attacks-activity-007)

### Slideshow

- The lesson slides are available on Google Drive here: [9.2 Slides](https://docs.google.com/presentation/d/1531A_LYibVH6f83PT5e7s83pwQ6zScVFVv60u4Ejy6o/edit#slide=id.g2459dec5bc3_0_1902)

- To add slides to the student-facing repository, download the slides as a PDF by navigating to **File** > **Download as** and choosing **PDF document**. Then, add the PDF file to your class repository along with any other necessary files.

- **Note:** Editing access is not available for this document. If you or your students wish to modify the slides, please create a copy by navigating to **File** > **Make a copy**.

### Time Tracker

- The lesson time tracker is available here: [9.2 Time Tracker](https://docs.google.com/spreadsheets/d/12tDEik_fcO3LwJsrWr7EVPZuTd1urMVSui6egtNcbhE/edit#gid=1145703143)

### Student Guide

Distribute the student-facing version of this lesson plan after class: [9.2 Student Guide](StudentGuide.md).

---

### 01. Instructor Do: Welcome and Introduction (0:05)

Welcome students to the second day of the second week of networking. Briefly review what was covered in the previous class:    

- Networking concepts including DHCP, NAT, routing protocols, and wireless.

- How each of these networking concepts assists with transmitting data across networks to reach its destination.

Explain that today will build on the previous class with networking concepts related to sending, receiving, and securing emails. 
	
Explain that we will cover the following concepts in the first half of the class:

- The various DNS record types and how they assist with sending and securing emails.

- Email protocols and the structure of an email.

- Email security issues and how to identify them.

In the second half of the class, we will review all the networking concepts covered up to this point.

[<- Back to Module Contents](LessonPlan.md#module-day-2-contents)

---

### 02. Instructor Do: DNS Record Types (0:10)

Remind the class that the **Domain Name System (DNS)** is the "phone book of the internet." Note that we've covered how DNS is used to translate a domain name into a numerical IP address.
  
  - For example, DNS translates the domain `www.google.com` into the IP address `64.233.177.139`.

  - DNS commonly operates on UDP port 53, but TCP port 53 is used as well.

    - UDP port 53 is primarily used for listening to DNS queries. Communication occurs in cleartext.

    - TCP port 53 is mostly used for zone transfers. It might also be utilized for queries and replies.

  - The domain name needs to be translated because computers connect to each other with IP addresses, not domain names.

  - This translation of a domain to an IP address is a type of **DNS record**.

Occasionally, DNS needs to provide other details about a domain.
  
  - For example: When you send an email, your email server needs to find the mail server name for the domain receiving the email.
  
  - These details are provided by the many other **DNS record types**. 

Define **DNS zone file** as an actual file containing all the DNS records for a particular domain.

  - A DNS zone file lives in a DNS server.
  
  - A DNS zone file contains a **Time to Live (TTL)**, indicating how long a **DNS cache** will remember the information in the file before having to request an updated copy from the DNS server.

  - A DNS zone file also contains the DNS records with information about the domain.
  
#### DNS Record Types  
  
Explain that while there are many available DNS record types, a handful of common DNS record types are important to know:

- **A record** translates a domain into an IP address.
  - For example: An A record for widgets.com points to `23.43.54.234`.

- **PTR record**, opposite of an A record, translates an IP address into a domain.
  - For example: The PTR record of `23.43.54.234` points to widgets.com.

- **CNAME record** (_canonical name_), is an alias record used to point one domain to another domain.

  - For example: A CNAME record pointing widgets2.com to widgets.com so a second DNS record doesn't need to be created for widgets2.com.

- **SOA record** (_start of authority_) contains administrative details about a domain, such as:
  - Email address of the administrator
  - TTL value
  - When the domain was last updated

- **NS record** (_name server_) indicates which server contains actual DNS records for a domain. It is also known as **authoritative name server**.

    - For example: A device wants to know the IP address for widgets.com, and makes a DNS request asking which authoritative name server exists for widgets.com. Once the **NS record** is confirmed, the device can trust this record for obtaining the IP address (or any other DNS record type) from the domain widgets.com.
  
 A domain can have multiple NS records for redundancy (if one fails, another is available).
  - For example: widgets.com has two name servers containing its DNS records:
    - `ns1.dnscompany.com`
    - `ns2.dnscompany.com`

  - NS records can also be used to point **subdomains** to name servers. For example, we can point the subdomain marketing.widgets.com to a DNS server of ns3.dnscompany.com.

#### Common DNS Attacks

- **DNS cache poisoning:** This is when a malicious actor intercepts a DNS request from a client and replaces the legitimate DNS entry with the address of a malicious website. 

    - **Prevention method:** Using DNSSEC is one way of preventing DNS poisoning. In simple terms, this adds verification steps to confirm the authenticity of a DNS's information.

![Image depicting DNS Poisoning scenario](./Images/DNS_Cache_Poisoning.png) 


- **DNS hijacking:** This is when a malicious actor takes over a domain registrar account and can point traffic to their DNS server. This would allow them to direct users to any malicious site that they choose.

    - **Prevention method:** Practice good password hygiene using complex passwords. In addition, multi-factor authentication should be used, if possible. When available, use domain name registry lock through your domain registrar to prevent unwanted changes.

![Image depicting DNS Hijacking scenario](./Images/DNS_Hijacking.png)

- **DNS amplification:** Attackers flood a DNS server with a variety of domain name requests using a spoofed source address that points to a targeted victim's address. This sends all of the responses to the target's address to overload the target.

    - **Prevention method:** Make sure that the DNS server is updated and configured using good security practices. Disable recursive query services on internet-facing DNS servers and block requests from known attack sources. Another possible solution is to invest in IDS appliances that limit requests from certain IP addresses.

![Image depicting DNS Amplification scenario](./Images/DNS_Amplification.png)

#### DNS Records and Email Communication

Explain that there are DNS record types that assist with email communications. 

- **MX record** (_mail exchange_) directs emails to a specific mail server for a domain. 

  - For example: widgets.com has a mail server called mailhost.widgets.com.
    
    - If an email is sent to bob@widgets.com, the sender will validate that the MX record for widgets.com is `mailhost.widgets.com`.
    
    - The sender then directs the email to the mail server mailhost.widgets.com.
  
  - Just like NS records, domains can have multiple MX records for redundancy, in case one goes down or can't handle a large amount of traffic.  

- MX records have **preferences** for setting the primary and secondary mail servers. 

  - These preferences are set with numerical **preference numbers** in front of the mail server name. The lower the preference number, the higher the priority.

  - For example: gadgets.com has the following MX records:
      - `10  mailhost_Atlanta.gadgets.com`
      - `5  mailhost_NewYork.gadgets.com`
      - `20  mailhost_LA.gadgets.com`

  - If an email comes into gadgets.com, it is first received by the New York mail server, because it has the lowest preference number. If the New York server is down, it will try Atlanta. If Atlanta is down, it will try the LA mail server. 


**TXT record** (_text_) was originally created to include human-readable notes, such as an associated company name. These also include computer-readable data. 

  - For example: The **SPF record** (_sender policy framework_), which determines if an email is from a trusted server, is an example of computer-readable TXT data.

    - Not all organizations send emails from mail servers within their domain.

    - Their mail servers may exist in another domain, or another organization may send marketing emails on behalf of an organization.

  - An SPF record indicates which mail servers are allowed to send emails on behalf of a domain.

  -  An SPF record's main purpose is to prevent spam, phishing, and email spoofing by detecting emails that may have a forged sender email. 

An example of an SPF record is: `v=spf1 ip4:192.41.100.193`.

- Break down the syntax:

  - `v=` is the version of SPF used.
  - `ip4:`indicates that an IPv4 host is allowed to send emails.
  - `192.41.100.193` is the IP of the mail server allowed to send emails on behalf of the domain. 
  
Explain how SPF records work with the following example:  

  - widgets.com's DNS SPF record indicates that `23.43.54.235` and `23.43.54.236` are the IP addresses of mail servers allowed to send emails on its behalf. 

  - gadgets.com received a suspicious email from a widgets.com email.
  
  - When the receiving email server at gadgets.com receives the email, it completes the following steps:
    
    1. Checks the sending mail server's IP address, `12.54.54.23`.
    
    2. Validates the DNS record of widgets.com's SPF record to confirm the sending mail server's IP address is either `23.43.54.235` or `23.43.54.236`.

    3. Since the sender's IP is `12.54.54.23` (not `23.43.54.235` or `23.43.54.236`), gadgets.com's mail server can identify the email as spam and potentially reject it or send it to the recipient's spam folder.
      
Take a moment to address any remaining questions on DNS record types before proceeding to the `nslookup` demo.

#### `nslookup`

Explain that networking and security professionals often need to look up a domain's DNS records.

  - For example: If emails aren't reaching their final destination, we would check the MX DNS record for that particular domain to make sure it's accurate.

Explain that there is a command-line tool called `nslookup` (_name server lookup_) that allows us to easily look up the DNS records of any domain.

- `nslookup` is typically available on most operating systems without having to be installed.

#### `nslookup` Demonstration

:warning: **Heads Up:** DNS records often change, so DNS lookup results may vary.

- Open the command line in your terminal and enter the following command:

   `nslookup gadget.com`
      
  - Explain the syntax for the request: `nslookup`  `[domain]`.
  

- Press Enter and your results should return in the following format:

    ```
    Server:	   127.0.0.53
    Address:   127.0.0.53#53

    Non-authoritative answer:
    Name:	    gadget.com
    Address:    162.243.110.34

    ```

- Break down the results:
    ```
    Server:    127.0.0.53
    Address:   127.0.0.53#53
    ```
  - Your default DNS server and its associated IP address.
  
  - **Instructor note:** You will have different results based on your default DNS server.
    
        
  ```
  Non-authoritative answer:
  ```

   - It indicates that this information is cached and not from the domain's primary (authoritative) name server.
   
    ```
    Name:    gadget.com
    Address: 162.243.110.34
    ```       
   - The result from the A record, indicating the IP address of gadgets.com is `162.243.110.34`. 
   
Explain that `nslookup` can look up specific DNS record types:

- Enter the following command:

    `nslookup -type=NS gadget.com`
   
- Explain the syntax:

  `nslookup`   `-type=[NS record type]`   `[domain]`
    
- Press Enter. Your new results should include the two name server records and their associated IP addresses:

    ```
    Server:		    127.0.0.53
    Address:            127.0.0.53#53

    Non-authoritative answer:
    gadget.com	    nameserver = ns1.dnsnameservers.net.
    gadget.com	    nameserver = ns2.dnsnameservers.net.

    ```

- Explain that you can look up other DNS record types by changing the value `NS` to another DNS record type. 
 
   For example: 

   - To look up the MX record:

       `nslookup -type=MX gadget.com`
    
   - To look up the A record:
    
       `nslookup -type=A gadget.com`
    
   - To look up the SOA record:

       `nslookup -type=SOA gadget.com`
  
Explain that in the next activity, students will get to use `nslookup` to look up multiple DNS record types.

Take a moment to address remaining questions before proceeding to the DNS record types activity.

[<- Back to Module Contents](LessonPlan.md#module-day-2-contents)

---

### 03. Student Do: DNS Record Types Activity (0:10)

Explain the following to students:

- In this activity, you will play the role of security analysts at Acme Corp.

- Acme Corp updated several domain DNS records and would like you to validate that the updates worked. 

- Your task is to use `nslookup` to validate the DNS records for each of the domains provided.

Send students the following file:

- [Activity File: DNS Record Types](Activities/03_DNS_Record_Types/unsolved/readme.md) 

[<- Back to Module Contents](LessonPlan.md#module-day-2-contents)

---

### 04. Instructor Do: Review DNS Record Types Activity (0:10)

In this activity, students used `nslookup` to analyze multiple DNS records for several domains, and answered several questions about their findings. 

Completing this activity required the following steps:

- Using `nslookup` for three domains. 

- Determining several DNS record types for each domain.

- Analyzing your findings.

**Instructor note:** Since these are live DNS requests, the results may change.

Send students the following solution file:

- [Solution Guide: DNS Record Types](Activities/03_DNS_Record_Types/solved/readme.md) 

Take a moment to address remaining questions before proceeding to the next section.   

[<- Back to Module Contents](LessonPlan.md#module-day-2-contents)

---

### 05. Instructor Do: Introduction to Email Networking (0:10)

Explain to the class that, while it seems simple to send an email from one address to another, there are many processes and technologies working in the background to make this magic happen.

- Understanding how this detailed process works can assist network and security professionals to identify email issues or attacks.

Explain the following scenario to illustrate the steps involved in sending and receiving an email.

**Step 1: Bob uses Microsoft Outlook to send an email to Alice.** 

- Bob, whose email is Bob@bob.com, composes an email to send to Alice, whose email is Alice@alice.com.

- Once Bob clicks **Send**, the email is forwarded to Bob's company's email server.

- The email server is also referred to as the **MTA** (mail transfer agent).

**Step 2: Bob's mail server finds Alice's mail server.**

- Bob's mail server does a DNS lookup against alice.com to determine its mail server. 

- Bob's mail server gets this information from alice.com's MX record.

**Step 3: Bob's mail server forwards the email to Alice's mail server.**

- Using a protocol called **SMTP** (Simple Mail Transfer Protocol), Bob's mail server sends the email to Alice's mail server.

- SMTP uses port `25` and is part of Layer 7: Application of the OSI model.

**Step 4: Alice pulls Bob's email onto her local computer to read it.**

- Bob's email is currently sitting on Alice's email server, and Alice needs to pull it from this server in order to read it.

- Two protocols can be used to transfer the email to Alice's local computer:

    1. **POP3**
        - With POP3 (Post Office Protocol), when Alice logs in and checks her email from Bob, the POP3 mailbox doesn't keep a copy of the email.

        - Alice would not be able to log in to another computer to view Bob's email, as it has already been downloaded from the mail server.

        - POP3 has a security benefit, as the email will not exist on a server the recipient doesn't control.

        - POP3 uses port `110` and is part of Layer 7: Application of the OSI model.
    
    2. **IMAP**

        - With IMAP (Internet Message Access Protocol), a copy of the email is kept on the server.

        - Even after Alice logs in and checks her email from Bob, she can check it again from another computer.

        - IMAP has the benefit of preventing data from being lost, as it backs up emails on a server.

        - IMAP uses port `143` and is part of Layer 7: Application of the OSI model.
    
Understanding these steps is important for diagnosing and troubleshooting email issues.

  - For example: If employees at your organization are able to send emails but not receive them, it's possible there is a DNS issue, or your DNS MX record may possibly be misconfigured.
    
#### Email Headers

Explain that, to complete the steps in the email process, emails have specific **headers**, which contain fields that assist with the process.

For the following demo, use the slides provided illustrating the parts of a Gmail email.

  - __Instructor note:__ If you would like, you can also use your own email.

Explain that there are many header fields that can be used for emails, some required and some optional.

- Students will be familiar with some fields, as they are displayed in standard email clients: 

    - **From email address:** The email of the sender (required). 
    - **To email address:** The email of the recipient (required). 
    - **Email subject:** The field for describing the subject of the email (optional).
    - **Email message body:** The field containing the message (optional).
    - **Date/Time**: Date and time the email was sent. This is added by the email client.
      
  ![email1](./Images/email1.png)         
      
- Some fields that students are not familiar with are available by viewing the complete, raw email in your email client.
    
- To view the raw email in Gmail, click on the three vertical dots on the right side of the email.
  
  ![email2](./Images/email2.png)  
  
- Select "Show Original" from the dropdown to view the raw email.
  
  ![email3](./Images/email3.png) 
  
- Scroll down on this page, and you will see the raw email.
  
  ![email4](./Images/email4.png)
  
- Explain that some of the most important fields in this raw email are:
  
  - **Return-path:** Specifies the sender's return email.

  - **Delivered-to:** Specifies the recipient's email. 

  - **Received:** Shows a list of mail servers, illustrating the path taken by the email from its source to destination.

    - This is an important field because it contains the IP address of the originator of the email.

  - The following image only shows one mail server, but occasionally the Received header will show an email passing through multiple mail servers.

  ![email5](./Images/email5.png) 
    
  - **Message-ID:** A unique string created by the sending mail server as an identifier of the email.

  - **Received SPF:** The SPF verification field, which we will cover in more detail in the next activity.
    
  ![email6](./Images/email6.png) 
   
Students may notice email headers that begin with an "x", such as: **x-mailer** and **x-Google-Smtp-Source**.

  - The "x" signifies an e**x**tension of the standard headers. 

  - These header records are optional and are typically used for custom applications.

  - They can also provide additional services for tracking, reporting, and authentication.  
   
   
Explain that in the next activity, students will analyze several emails and identify several important headers.

Take a moment to address remaining questions before proceeding.

[<- Back to Module Contents](LessonPlan.md#module-day-2-contents)

---

### 06. Student Do: Email Networking Activity (0:15)

Explain the following to students:

- In this activity, you will continue to play the role of a security analyst at Acme Corp.

- Acme Corp's CFO recently received several suspicious emails.

- You must analyze the header records of the suspicious emails and document several data points.

Send students the following files:

- [Activity File: Email Networking](Activities/06_Email_Networking/unsolved/readme.md) 
- [Suspicious Emails](./Resources/emails.pdf)

[<- Back to Module Contents](LessonPlan.md#module-day-2-contents)

---

### 07. Instructor Do: Review Email Networking Activity (0:10)

In this activity, students analyzed several suspicious emails sent to the Acme Corp CFO, and documented data points from the email headers.

Completing this activity required the following steps:

- Reviewing the suspicious email headers from the emails provided.

- Documenting several data points found in the email headers.
   
Send students the following file:

- [Solution Guide: Email Networking](Activities/06_Email_Networking/solved/readme.md) 

#### Review 

**Email 1**

  - Delivered-To: juliejones@acme.com
  - Return-Path: jonathanthomas@microsoft.com
  - IP address of source: `40.76.4.15`
  - Message-ID: 1689837351.2998569.1568044304435@mail.microsoft.com


**Email 2**

  - Delivered-To: juliejones@acme.com
  - Return-Path: xzvvvret34344@yahoo.com
  - IP address of source: `74.6.130.41`
  - Message-ID: 1689837351.2998569.1568044304435@mail.yahoo.com


**Email 3**

  - Delivered-To: juliejones@acme.com
  - Return-Path: timmytom@widgets.com
  - IP address of source: `34.86.130.49`
  - Message-ID: 1gytrdd9837351.987987abs9.1568044304435@mail.widgets.com

**Email 4**

  - Delivered-To: juliejones@acme.com
  - Return-Path: return@irs.org
  - IP address of source: `64.71.74.115`
  - Message-ID: 404021289698796556000_11022028878758757117@jdq.hentersss.com

**Email 5**

  - Delivered-To: juliejones@acme.com
  - Return-Path: billybob@companyA.com
  - IP address of source: `209.85.210.51`
  - Message-ID: CACLG$52234Ygm1FNJZWXQc=dR-cv-jw+KRbRPf455BU6E-Xp_xDEA@mail.gmail.com


Take a moment to address remaining questions before proceeding to the next section.   

[<- Back to Module Contents](LessonPlan.md#module-day-2-contents)

---

### 08. Instructor Do: Email Security Issues (0:15)

Explain that while email provides many benefits, it also comes with many security concerns.

Explain that one of the top email concerns for most users and businesses is **spam**. Introduce spam by covering the following:

  - Spam is not an acronym. It is defined as "the sending of unsolicited emails."

  - Over 60% of all emails can be identified as spam.

  - While spam isn't inherently dangerous, a large number of spam emails can be very inconvenient for organizations.

  - Many email systems have developed advanced methods for detecting and stopping spam emails.

    - These methods involve using SPF records, matching lists of known spam senders, and identifying keywords.
 

Explain that a second email issue is sending confidential emails across **unencrypted channels**. Explain the following: 

  - Emails are almost always **not** encrypted.

  - Emails are typically routed across multiple mail servers before reaching their destinations, opening up the risk of email interception and views by unauthorized users.
  
  - Several technologies can be used to encrypt confidential emails such as: 

    - **PGP** (Pretty Good Privacy)
    - **S/MIME** (Secure/Multipurpose Internet Mail Extensions)
 
  - The challenge of PGP and S/MIME is that they involve coordination and setup between the email sender and the email receiver.
  
A third email security issue is **email spoofing**.

  - Email spoofing is when an email is designed to trick the receiver into believing it is coming from a trusted source.
 
 - Explain how email spoofing works with **phishing** by covering the following:

    - **Phishing** is an attempt to gain sensitive information from an email recipient and is often accomplished through email spoofing.
     
      - For example: A scammer sends you an email pretending to be from your bank, asking you to update your username and password.
      
      - At first glance, the spoofed email looks like it legitimately came from your bank.
    
      - The email may contain a **phishing URL** that has a fake bank login page, which maliciously captures your banking username and password. 

   - According to a recent report from Microsoft, phishing attacks are by far the most common cybersecurity threat—increasing a massive 250% since the previous report was published. [(Source: CPO Magazine)](https://www.cpomagazine.com/cyber-security/phishing-attacks-now-more-common-than-malware/)
 
 Fortunately, email spoofing can be detected with several methods, which analyze the raw email headers in sent emails.
 
 #### Method 1: The *From* Email Header
 
Explain that the simplest way to check for phishing is to look at the From email header. 

 - Spammers and phishers often disguise their true source email, changing the displayed email source to a name the recipient will trust or recognize. For example:

   - You check your inbox and see an email from "Citibank."

   - When you view the raw email header in either the "From" field, or the "Return-Path," the true email address of the sender is displayed.

   - The email address is sdfs2344dsf@yahoo.com—it doesn't have a @citibank domain. This is an indicator of a malicious email.

- Another method used by phishers is to make a slight change to the name of the sending domain.

   - Look closely at the email for any small misspellings.

    - For example, a phisher could use the from email domain of @cittibank.com, with an additional "t" in the domain.
     
    ![phish1.png](./Images/phish1.png)
     
 #### Method 2: The *Received-SPF* Email Header
 
 As we mentioned earlier, the SPF record is used to identify which mail servers are authorized to send emails on behalf of a domain.

 - Received-SPF is an email header that displays the results of validating the SPF record.

 - Received-SPF uses the IP address from the Received field and determines if it's an IP of an authorized sender.
  
    - If the IP is accepted, it will display as a "pass."
      
      For example: 
      
      `Received-SPF: pass (google.com: domain of michael@acme.com designates 76.87.4.15 as permitted sender)` 
    
    - If the IP is not accepted, it will display as a "fail."
      
      For example: 
      
      `Received-SPF: fail (google.com: domain of michael@acmers.com does not designate 174.81.74.11 as permitted sender)`
     
#### Method 3: The *Received* Email Header  
     
Remind the class that the Received header includes the source IP of the mail server that sent the email.

 - There are many web tools available to look up IP address information. 
 
   - For example, the [ARIN Whois/RDAP tool](https://search.arin.net/rdap/).
 
 - While this isn't always the simplest way to validate a legitimate email sender, it is used by security professionals to provide additional information about the sender.
 
Provide the following example of a case in which this method would be useful: 

   - You receive an email from a US-based government organization, such as the IRS.

   - The IP address from the Received header record is `41.32.23.52`.

   - Looking up this IP on arin.net shows the location of the IP is Egypt.

   - This indicates that the email is probably not legitimate, as it's unlikely that a US-based government organization would have a mail server based in Africa.
   

Explain that many email systems have built-in technologies that automate these methods to identify and detect spoofed and phishing emails.  
  
  - However, these automated systems aren't perfect, and can miss spoofed and phishing emails.

  - Therefore, it's important for security professionals to understand how to use these methods themselves.
   
   
Conclude this lesson by explaining that in the next activity, students will continue to analyze the emails from the previous activity.  

The students will use the methods explained here in combination with the header data to determine which of the emails is not legitimate.

Take a moment to address remaining questions before proceeding.

[<- Back to Module Contents](LessonPlan.md#module-day-2-contents)

---

### 09. Student Do: Email Security Activity (0:15)

Explain the following to students:

- In this activity, you will continue to play the role of a security analyst at Acme Corp.

- Acme Corp believes that several of the suspicious emails received by the CFO are spoofed.

- You must further analyze the emails to determine which are spoofed and which are legitimate.

Send students the following files:

- [Activity File: Email Security](Activities/09_Email_Security/unsolved/readme.md) 
- [Suspicious Emails](Resources/emails.pdf)

[<- Back to Module Contents](LessonPlan.md#module-day-2-contents)

---

### 10. Instructor Do: Review Email Security Activity (0:10)

In the exercise, students continued to analyze the suspicious emails sent to the CFO of ACME Corp to determine which of the emails were spoofed.

Completing this activity required the following step:

- Reviewing the headers in each email for indicators of spoofing. 
   
Send students the following file:
   
- [Solution Guide: Email Security](Activities/09_Email_Security/solved/readme.md) 

#### Review 

**Email 1**

- Received-SPF: "Pass" indicates that it is an authorized sender on behalf of Microsoft.
- From: Jonathan Thomas <jonathanthomas@microsoft.com>—the email and name match.
- Summary: While there is no 100% guarantee that this is a legitimate email, the records in the header indicate it is safe.


**Email 2**

- Received-SPF: "Pass" indicates that it is an authorized sender on behalf of Yahoo.
- From: Michael Smith <xzvvvret34344@yahoo.com>—the name and email do not match and the email looks suspicious.
- Summary: While there is no 100% guarantee that this is a spoof email, the mismatch of the name makes it likely.


**Email 3**

- Received-SPF: "Fail" indicates that it is not from an authorized email provider.
- From: Timmy Tom <timmytom@widgets.com>—the name and email match. 
- Summary: While there is no 100% guarantee that this is a spoof email, the failed SPF record usually indicates a spoofed email. 


**Email 4**

- Received-SPF: "Fail" indicates that it is not from an authorized email provider for the IRS.
- From: IRS Assistance Programs <m1T7pqweeqweD8G@thought.bestwebsitesabc.com>—the name and email do not match.
- Summary: While there is no 100% guarantee that this is a spoof email, the failed SPF record and the obvious mismatch of the from email address is a strong indicator this is a spoofed email. 


**Email 5**

- Received-SPF: "Pass" indicates this is an authorized sender for CompanyA. 
- From: Billy Bob <billybob@companyA.com>—the email and name match. 
- Summary: While there is no 100% guarantee that this is a legitimate email, the records in the header indicate it is safe.

An email fails the Received-SPF verification, but was a legitimate email.
    
  - What does this indicate?
  - What would you recommend to prevent future emails from failing this validation?

This most likely indicates that the mail server sending emails on behalf of the domain doesn't have a DNS SPF record.

To resolve this, an SPF record should be added with the IP of the mail server sending these emails.

Take a moment to address remaining questions before proceeding to the next section.   

[<- Back to Module Contents](LessonPlan.md#module-day-2-contents)

---

### 11. Break (0:15)

[<- Back to Module Contents](LessonPlan.md#module-day-2-contents)

---

### 12. Optional Instructor Do: Setting Up Networking Concepts Activity (0:05)

:warning: **Heads Up:** The remaining activities are reviews of the concepts from the previous two modules. These are optional and can be completed if time remains.

For the remainder of the class, we will review the networking concepts covered in the previous networking classes. 

Explain the following about the review:

  - These review topics and questions are focused on the most important takeaways from the previous networking classes.

  - These topics will likely be covered on security exams such as Security+ and CEH (Certified Ethical Hacker).

Explain that students will be tasked with:

  - Opening up the provided assets, such as PCAP files and documents.

  - Answering the provided questions.

Recommend that the class use all available resources, such as:
  
  - Previous class slides

  - Previous class notes
  
  - Online searches
  
  - Their classmates 
  
Explain to the class that this is a concept review that will help prepare them for the next class: a Networking Capture the Flag contest.   

[<- Back to Module Contents](LessonPlan.md#module-day-2-contents)

---

### 13. Student Do: Networking Concepts Review Activity (0:15)

Send students the following activity file:

- [Activity File: Networking Review](Activities/13_Networking_Review/unsolved/readme.md)

[<- Back to Module Contents](LessonPlan.md#module-day-2-contents)

---

### 14. Instructor Do: Review Networking Review Activity (0:08)

Remind the class that the purpose of the review was to cover the most important topics from the previous networking classes.

-  Ask the class if there were any sections they found particularly challenging.

-  Review a few questions from the class.

Conclude by sending out the following answers for the review:

- [Solution Guide: Networking Review](Activities/13_Networking_Review/solved/readme.md)

[<- Back to Module Contents](LessonPlan.md#module-day-2-contents)

---

### 15. Optional Instructor Do: Setting Up Networking Attacks Activity (0:05)

Explain to the class that the last part of the networking concepts review will focus on networking attacks.

Similar to the previous review, you will be tasked with:

  - Opening the provided assets, such as PCAP files or documents.

  - Answering the provided questions.

Recommend that the class use all available resources, such as:

  - Previous class slides

  - Previous class notes

  - Online searches

  - Their classmates

[<- Back to Module Contents](LessonPlan.md#module-day-2-contents)

---

### 16. Optional Student Do: Networking Attacks Activity (0:15)

Send students the following activity file:

- [Activity File: Networking Attacks Review](Activities/16_Networking_Attacks_Review/unsolved/readme.md)

[<- Back to Module Contents](LessonPlan.md#module-day-2-contents)

---

### 17. Optional Instructor Review: Networking Attacks Activity (0:07)

Remind the class that the goal of these activities was to review the most important topics from the last few days of networking.

-  Ask the class if there were any sections they found particularly challenging.

-  Review a few questions from the class.

Conclude with sending the solutions for review:

- [Solution Guide: Networking Attacks Review](Activities/16_Networking_Attacks_Review/solved/readme.md)

[<- Back to Module Contents](LessonPlan.md#module-day-2-contents)

---

© 2023 edX Boot Camps LLC. Confidential and Proprietary. All Rights Reserved. 
