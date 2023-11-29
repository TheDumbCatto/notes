# Synopsys FAQ

## Coverity

- Can you create a new view with filters for defects with Medium impact and above?
> Hell yeah

- Can you down-level a particular defect's (a defect at a specific line) impact (set impact from High to Medium, for example), and persist that settings in subsequent scans?


# Menlo Security FAQ
- What are the scenarios for HEAT assessment?
- How does Menlo's agent-less approach work exactly?

# 07/07

Tech questions Vietinbank asked:

## Basic functionalities

- Can BD scan docker images?
- Which IDEs can BD integrate w/?
- Does BD pin point the exact flawed LOC?
- Does Coverity's CodeSight plugin scan through the whole code when presented w/ a brand new code file?
- Can BD create policy template for resuse?
- Can BD's policy be applied for a subset of project?
- Can BD integrate w/ various CI/CD tools and ticketing systems?

## Other
- Is CodeDX primarily used for dev or sec team?
- How does BD policy work in the context of CICD pipeline?

# 07/13

**Synopsys**
- Emphasize on the ability of maintaining development velocity & cost reduction

**Interfacing**
- Be precise on terminologies
- Every vendors, big or small, have their own story. Focus on that
- Be precise on when to use vuln vs weakness

**Homework**
- What is SBOM exactly? Who defined SBOM?
- Create slides which emphasize the correlation between Synopsys' solutions and SSDF's requirements, and an accurate overview of SSDF's 4 requirement groups


# 08/01
Presentation flow:
- Overview of what Synopsys does (slide 2)
- What problems does Synopsys SIG solve (slide 3, 4)
- A sneak peek into how SIG solve those problems  (slide 5-9)

# 08/03
Questions:
**Menlo**
- What are the scenarios for HEAT assessment?
- How does Menlo's agent-less approach work exactly?
- **How does Menlo's phishing prevention work exactly (e.g when a client inputs sensitive data into a phishing website)?**
- **Can Menlo (in Cloud deployments) see sensitive information in isolated email/websites?**
- What is Menlo's mechanism to detect malwares and malicious stuff?
- **How does Menlo prevent malicious exectuables? What if the executable is a zero-day malware and hasn't appeared in any malware databases?** 
- How does Menlo improve the security posture, as a whole, for the following system:
> Data -> DC (using LGSP, connected to API Gateway, already with end-to-end encryption), DC -> Headquarter (HQ will mine those data).

- **If Menlo's deployed on-premise, where is the malware database stored?**

**Illumio**
- How does Illumio's ZTS differ from Palo Alto's micro-firewall?
- How does Illumio fit into the current "Level 3" system's requirements (with all IDS/IPS/Firewalls already in-place)? In another word, how does Illumio maps into the requirements for a level 3/4 system?
- Compares Illumio's with web/database firewall?
- Is Illumio fully agent-based?
- What can Illumio's agents detect?
- What can we see with Illumio's traffic map?

# 08/14
Plans:
- Synopsys MISA (CodeDX, BlackDuck), Omninext (CodeSight)

PoC review:
- Success criteria
- Customer satisfaction

![](Pasted%20image%2020230814092117.png)

# 08/21
Present:
- Sale sections:
	- Overview on related terminologies
- Tech sections:
	- What can solution X do?
	- How solution X works?
	- What are the deployment models?
- Demo:
	- (Prep) Request demo walkthrough from Eugene
	- (Prep) Build ur own demo scenarios w/ unique & important features of solution X
	- 

# 08/24

**Coverity** key features for DEMO
- Point & scan
- Coverity Connect vuln UI,  3 levels of remediation
- Coverity Connect triage
- Coverity Connect dashboard
- Coverity Connect's custom checkers -> This where customized checkers are added, file exetension is .cxm
- Integration with Jira

**Black Duck** key features for DEMO
- Showcase detailed views of the 3 risks
- Showcase advantages of having BDSA
- Showcase policy rules, CI/CD policy rules

# 08/28
- MFA, can integrate w/ 3rd-party MFA
- Cloud directory
- Real time AD sync
- Password reset self-service

Questions:
- What kind of identites does 1L provide? -> Human identities, not service accounts
- Authentication methods supported? -> Application focused, but can do Desktop level auth (non-AD-joined)
- Which attributes to sync from AD? -> Minimum username (or email), first name, last name
- Auth flow for in-house app how?
- 1L auth with PAM system how? -> 1L own PAM (SafeGuard, not privileged access mgmt) provide app connector, provide access & login mgmt for SafeGuard users
- 1L handle authorization mgmt for in-house application how?

Quy mô toàn cầu (150 DCs)


# 09/05
OneLogin's statements:
- Minimum attr: first+last name, email/username (SamAccountName or UserPrincipalName)
- AD remains the auth source for logins, no password stored on 1Login
- Once data is written to the cloud directory, 1Login have no visibility
- Customer can prohibit Support from accessing their tenant via a global config setting that they alone can control
- All data processed are subject to OneLogin's Enterprise Trust and Secrutiy framework

- Secure entry: TLS min 1.2
- Secure processing: S3 Buckets, PGP Asymmetric Encryption
- Secure storage: FIPS-compliant AES 256 soft-HSM (Data encrypted before being stored using KSM and HSM, volumes are encrypted including DB and host volumes)
- Data are secured using AWS's shared security model

# 09/06
- Are they hosting any workload in public cloud?
- How are they accessing to the public cloud applications? Is it through VPN or publicly accessible by FQDN
- EVN WAN how are they connected from DataCentre to Office LAN?
- What is PC WAN

Zscaler questions:
- deployment model => compare agent-based vs agent-less?
- Multiple IT & OT infra needs 1 or multiple Zscaler systems? => 1 Zscaler system
- ZIA support protection for both data at-rest and in-motion? => Yes
- ZPA replace traditional VPN, what's the difference?
- SSL inspection
- Minimum OS version supported for ZIA?
- Explain ZPA solution for IoT network protection
- On-prem/private-cloud deployment model for ZIA? (Private Service Edge)
- Difference between Zscaler's IoT OT privileged remote access vs PIM/PAM?
- How does Zscaler IoT OT protects level 0 compromise?
- 

# 09/08
**SecureAuth**
- Cat -> sales channel manager
- No in-region sales or support, yes in Aus and mostly in US
- Follow up email: 
	- ask business model -> Cat will talk to CMO about opportunity in APAC
	- set up session with sales & SE
	- Information to provide:
		- IdP solution (Menlo,...) to integrate w/
		- Size of company, Deal size (budget) (general VNPT's background)

# 10/30
VPS important questions:
- With your current sec stack, do you meet any problems? _(Were you forced here or are you truly interested?)_
- What solutions are in place to protect users when accessing Internet?
- How far along are you and the other vendors? How do you feel about them vendors?

# 10/31
- VPS:
    - Complementation with existing Checkpoint? FW
    - CASB detailed functionalities (up/download Skype - already achievable w/ existing solutions)
    - Cookie storage mechanism in DVC?
    - What if Checkmarx?’s category engine says allow but Webroot’s says deny?
    - On-prem architecture (what is deployed on-prem exactly? 1 server takes care of all DVC, URL filtering, DLP?)
    - File download/upload demo?
    - Web app control can?
    - FW is currently deny all
    - A Đóa, a Nam, a Kiên, c Linh

# 11/2
**MSB:**

- Anh Tu + anh Hoai (SOC), anh Luyen (architecture), anh Manh (head of Pentest + Redteam)
- SWG + Email sec by Cisco, WAF
- Email sec deletes original doc content if macro is malicious
- DLP + AV McAfee (Trellix)
- Workforce much remote + hybrid
- Remote VPN split tunnel (internal resource → VPN, internet access → not through VPN → No Internet Security), no performance issue
- Very little cloud usage (OpenShift priv. cloud)
**Inquires:**
- Can Menlo isolate email attachment if user click Save As instead of opening the doc first?
- **3rd party DLP integration can?**
- **Menlo’s AI engine’s new IoC able to be pulled by other solutions?**
- Ad banner phishing stealing device’s metadata prevention how?
- on-prem/hybrid model?
- **Allow original download only for certain people/sites can?**

# 11/17
Zscaler FAQ:
- Can admin in certain countries see only logs for that countries? -> No
- SSL handshake failure is a common problem because of Cert pinning (a website not allowing SSL inspection) -> SSL inspection bypass for that website solves the problem
- Can use URL lookup tool on the dashboard to look up the URL's category
- 2 ways to bypass: App profile or PAC file
- If device is logged out of ZCC, the mobile portal shows it as "Removed". For this, the admin can set a policy to remove the Removed devices after a certain time
- What are the Organization/Location/Department Admin scope?
- 

# 11/21
- clientevent appear in dev tools for isolated sites
- ACR1 mirrors DOM tree, ACR2 mirrors the very pixel

# 11/22
2 functions of the email Transform:
- Attachment wrapping - HTML wrapping
- Safe PDF addition