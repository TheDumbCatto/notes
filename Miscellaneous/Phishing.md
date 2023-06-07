# Nature of phishing
- Definition: URL-based Phishing is the act of using fake, convincing websites to trick/manipulate a user into revealing sensitive personal details, or to execute malicious activities on the user's end.
- some-bullshit.alsdkfasldkfjkowjefoqw.ebay.apple.com
- not.bullshit.com
- Phishing is Semantics-based (which means hard to detect, since it's not based on software/hardware vulnerabilities). [Phishing environments, techniques, and countermeasures: a survey](https://sci-hub.se/https://doi.org/10.1016/j.cose.2017.04.006)
- A Phishing Attack consists of several phases, but it can be summarized as the following: [Phishing environments, techniques, and countermeasures: a survey](https://sci-hub.se/https://doi.org/10.1016/j.cose.2017.04.006), [Phishing Attacks Survey: Types, Vectors, and Technical Approaches](https://sci-hub.se/https://doi.org/10.3390/fi12100168), [Phishing Attacks: A Recent Comprehensive Study and a New Anatomy](https://www.frontiersin.org/articles/10.3389/fcomp.2021.563060/full)
	- Preparation: Communication Media (E-mail, Social Media,...), Target Environments (PC, phone,..), Material Preparation (Communication Content, Malicious Content)
	- Execution: Material Distribution
	- Post Attack

# Techniques
[Phish Phactors: Offensive and Defensive Strategies](https://sci-hub.se/10.1016/S0065-2458(06)70005-5)
- **Bad domain names:** 
	- Straight up bad domain names
	  *e.g. adf98w34rjasdfn.ebay.com*
	- Character replacement - uses visually similar characters to trick users
	 *e.g. using "app1e.com" to imitate "apple.com"*
	 - [IDN homograph attack](https://en.wikipedia.org/wiki/IDN_homograph_attack) - uses [Punycode](https://en.wikipedia.org/wiki/Punycode) to force browsers to use a sequence of ascii characters to display a character in another format
		 *e.g. domain name "xn–80ak6aa92e.com" will be displayed by browsers as "apple.com". See: [XuDongz's IDN phishing blogpost](https://www.xudongz.com/blog/2017/idn-phishing/)*
- **Shortened URL:** bitly.com or other alternatives to mask/redirect to the malicious domain
- **Host name obfuscation**: uses IPs in URLs instead of texts
  e.g. http://10.3.144.15/login instead of http://<domain_name>/login
- **Website-based exploitation**
# Countermeasure method categories
[Phishing environments, techniques, and countermeasures: a survey](https://sci-hub.se/https://doi.org/10.1016/j.cose.2017.04.006)
- **Machine Learning:**
	- Classification - uses a labeled database.
	- Clustering - separates URL data into 2 clusters: phishing and legitimate.
	- Anomaly Detection - discovers abnormal behaviors comparing to legitimate behaviors
  Features that can be fed into an ML model include (Table H in the paper lists example features):
	- URL features
	- Textual features - the textual content of the website/email
	- Hybrid features - both textual and URL features
- **Text Mining:** refers to utilizing data mining and machine learning techniques to discover trends, patterns, or useful knowledge from texts. Text mining identifies phishing attempts by analyzing the patterns of suspicious material, which include URLs. This technique is usually used as pre- and/or post-processing steps in creating other phishing detection solutions.
- Human Users
- **Profile Matching:**
	- Usage History Matching - ?
	- Pattern Matching - ?
	- Visual Matching - ?
	- White and Blacklist Matching - matches the suspected URL with databases of known bad URLs. Lots of free, popular databases on the Internet: OpenPhish, PhishTank, AlientVault OTX, SpamHaus,...
- **Others**
	- Ontology - uses text-based semantics to detect novel phishing contents.
	  *"Very few anti-phishing techniques have incorporated ontology to date."*
	- Search Engines - as phishing domains aren't usually indexed by search engines, this can be a useful feature used for a detection model.

# Types of Anti-phishing Tools/Engines
[Detecting Fake Websites: The Contribution of Statistical Learning Theory](https://sci-hub.se/https://doi.org/10.2307/25750686)
- **Lookup/Blacklist systems** - the same as Profile Matching/White and Blacklist Matching technique described above
- **Classifier/Pattern Matching systems** - the same as Profile Matching and Machine Learning techniques described above
[Review: Phishing Detection Approaches](https://sci-hub.se/10.1109/ICTCS.2019.8923069)
- **Content-based:**
	- [Phishing website detection using URL-assisted brand name weighting system](https://sci-hub.se/10.1109/ISPACS.2014.7024424) 
	 Assign weights to words drawn from URL and web content based on the words' positions in those locations. Use [TF-IDF](https://viblo.asia/p/tf-idf-term-frequency-inverse-document-frequency-JQVkVZgKkyd) to **find most important words, then use a search engine to find the top domains that use those words the most frequently** - which are often legitimate domains. After that a WHOIS lookup is done to grab the owner of the examined domain, as well as the domains from the search result. **The examined domain is a phishing URL if its owner isn't any of the owners of the domains from the search result**.
	  **The paper achieved 97% accuracy** with a dataset of 220 websites.
	- [Utilization of website logo for phishing detection](https://sci-hub.se/https://doi.org/10.1016/j.cose.2015.07.006) 
	 Use Machine Learning techniques to **extract the logo of the examined website, then run that logo through a search engine to find the most relevant, and is often legitimate, owner of that logo**. **Compare the owner of the examined website and the owner of the domain which "owns" the logo** using a WHOIS lookup. A result indicating different owner means the examined website is fraudulent.
	  **Relatively low accuracy I'd say**. The whole experimental result section is quite ambiguous.
	- [New Rule-Based Phishing Detection Method](https://sci-hub.se/https://doi.org/10.1016/j.eswa.2016.01.028)
	 Use SVM and Decision Tree with 2 feature sets. First feature set includes:
		- Whether or not domain name is IP address (Host name obfucscation)
		- Whether or not the website uses HTTPS
		- Number of sub-domains
		- Web-address length
		- Blacklist keywords?
	  Second feature set includes:
		- [Levenshtein distance](https://en.wikipedia.org/wiki/Levenshtein_distance) to calculate the similarity between the website's URL and the sources of the website's elements (href tags, scripts, CSS, images)
		- Whether or not the sources of the website's elements (href tags, scripts, CSS, images) use HTTPS
	  **The paper achieved 98% accuracy in classifying e-banking phishing** with a dataset of 1158 phishing and 549 legitimate websites.
- **Heuristic-based**
	- [Detect Phishing by Checking Content Consistency](https://sci-hub.se/10.1109/IRI.2014.7051880) 
	 Categorize websites through 2 phases: Pre-filtering and Classification Phase. Pre-filtering considers any websites whose 2nd-level domain appears in a Consistency checking Identities list, (a list of domain names taken from search engine logs and web browsing logs that are clicked on with enough number of times) to be legitimate. The Classification Phase calculates a website's phishing confidence score by using 4 different features:
		- Randomness of URL
		- Position of domain token http://asldkfjasdlkfjwer.asdfoj-ascd.com/?id=abc&xyz
		- Ratio of found domain token http://facebook.com
		- Conceptual similarity
	  Details of how to calculate each feature is available in the paper. **The paper achieved a 98% overall accuracy** using up-to-date data and a dataset of ~2.8k phishing and ~5k legitimate websites.
	  - 
- **Fuzzy-based**
# Nice notes
[Phishing environments, techniques, and countermeasures: a survey](https://sci-hub.se/https://doi.org/10.1016/j.cose.2017.04.006)
![](Pasted%20image%2020230331153348.png)
[Why is phishing still successful?](https://sci-hub.se/https://doi.org/10.1016/S1361-3723(20)30098-1)
![](Pasted%20image%2020230331162530.png)

# Features
1- Having IP address
2- URL Length
3- Shortening Service
4- @ ~ & symbol in URL
5- Double slash redirection
6- Pre/suffixes "-"
```
having subdomain?
https://arxiv.org/pdf/2009.11116v1.pdf
```
`7- SSL state` - Disabled due to correct verification taking too long
8- Domain Registration Length
9- Favicon: If the favicon is loaded from a domain other than that shown in the address bar, then the webpage is likely to be considered a Phishing attempt
```
using non-standard port?
https://arxiv.org/pdf/2009.11116v1.pdf
```
10- HTTPs token in URL
11- Request URL - Whether the  external objects contained within a webpage such as images, videos, and sounds are loaded from another domain.
12- URL of \<a\> tag
```
links in tags?
https://arxiv.org/pdf/2009.11116v1.pdf
```
13- URL of \<form\> tag: `“#”, “about:blank”, an empty string, or  “javascript:true"`
14- Info submitted to email
15- Abnormal URL: It is extracted from the WHOIS database. For a legitimate website, identity is typically part of its URL
16- Website redirection count
17- Status Bar Customization: Use JavaScript to show a fake URL in the status bar to users  
18- Disabling Right Click: It is treated exactly as using onMouseOver to hide the Link  
19- Using Pop-up Window: Showing having pop-up windows on the webpage.
20- IFrame
21- Domain Registration Age
22- Web Traffic: This feature measures the popularity of the website by determining the number of visitors.  
23- Page Rank: Page rank is a value ranging from 0 to 1. PageRank aims to measure how important a webpage is on the Internet.  
24- Google Index: This feature examines whether a website is in Googles index or not.  
25- Links Pointing To Page: The number of links pointing to the web page.  
26- Statistical Report: If the IP belongs to top phishing IPs or not.
27- Randomness of URL
28- Position of domain token
```
CSim - Conceptual similarity
3.2.4 - https://sci-hub.se/10.1109/IRI.2014.7051880
```

29- [Levenshtein distance](https://en.wikipedia.org/wiki/Levenshtein_distance) to calculate the similarity between the website's URL and the sources of the website's elements (href tags, scripts, CSS, images)
30- Whether or not the sources of the website's elements (href tags, scripts, CSS, images) use HTTPS
31- Subdomain Level count
32- Path Level count
33- TLD or ccTLD in subdomain
34- TLD or ccTLD in paths
35- Form contains Image only