# Onboarding

## Dependencies
- The number of web apps, or sites
- The existence of multi-level authentication

## Service levels

![WhiteHat Dynamic service levels](WhiteHat%20Dynamic%20service%20levels.png)

![WhiteHat Service Level Matrix - without Site Criticality](WhiteHat%20Service%20Level%20Matrix%20-%20without%20Site%20Criticality.png)

![Pasted image 20230713161829](WhiteHat%20Service%20Levels%20-%20with%20Site%20Criticality.png)



## Onboarding services

- Deployment Planning
- Training
- Onboarding
- Setup and configuration assistance
- Coverage review and optimization
- Vulnerability review
- Single point of contact for support

![](WhiteHat%20onboarding%20expectations%20and%20activities%20timeline.png)

![](Pasted%20image%2020230713164552.png)

## Reminders

Requirements of a valid AHN:
1. The current application must rely on the potential associated hostname to enable     or improve upon the functionality/purpose of the base application.
2. The associated hostname shares a session with the base domain.
3. The associated hostname cannot have a separate login function

![](Pasted%20image%2020230713164916.png)


## Onboarding process checklist

### Initial config

- All necessary credentials are provided by clients
- All of White Hat's necessary IPs have full access to the application
- AHNs:
	- Check if the application contains links or makes requests to other hostnames
	- Check if the hostname is under contract on a different asset
	- Check for [Incompatible tech](#Incompatible%20tech)


### Parse scan


### Confirm site coverage

- Perform manual spider and compare the resulting links with the initial parse scan's link results



#
***

# Processes

## Vuln Verification

- Review the vuln
- Categorize the vuln: By the **resource URL** and **vuln**
- Grade the vuln: By **threat** and **severity** score

## Vuln Manual Retests


# Tech details

## Incompatible tech

- APIs
- Client-side apps (Thick Clients)
- Windows/Mac native apps
- Plugin apps
- ActiveX Silverlight
- Apps with single-page client-side JS architecture (React, Deku, Riot,..) ***// Questionable***
- Apps with anti-automation functionality (Dynamic links, WebSphere, Anti-automation tokens, Sites that enforce requests to be sent in orders,...)
- Non-HTTP authentication (Physical token, one-time login codes, 2f authen other than SMS/Email)
