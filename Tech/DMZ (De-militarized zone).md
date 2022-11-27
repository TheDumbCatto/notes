DMZ is a network that sits between the external, untrusted network and the internal network. DMZ contains services that should be allowed for public access. E.g. FTP, DNS, Web servers,...

DMZ acts as a buffer serving internal resources to public untrusted requests, adding another layer of security to internal network.

DMZ's architecture usually consists of 2 firewalls: One sits between public network and the DMZ, filtering access to DMZ from untrusted network. The other one sits between the DMZ and internal network, filtering DMZ requests sent to internal network.

Some of the main benefits that DMZ provides are:
- Access control: Only certain services within the internal network are enabled for public access through DMZ policies.
- Reconnaissance prevention: Attackers would have a hard time scanning internal network due to the existence of the hardened, highly secured middle buffer that is DMZ.
- IP spoofing prevention.
- Additional layer of security for internal network.