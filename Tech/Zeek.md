# The What-s and Why-s

## What is Zeek
***


## Capabilities
***
**Aiding Incident Detection and Response Workflow**

- 'Matching' investigations: Automating the discovery of anomalies by applying search queries according to a set of known malicious activity patterns.
- 'Hunting' investigations: Finding anomalies by applying search queries according to hypotheses rather than a fixed set of patterns.
- Correlating alerts seen by IDS with Zeek events.

**Enrich SIEM data**

# Under the hood

## Main components of Zeek
***

![](Pasted%20image%2020230126112300.png)

### Event Engine
***
**Reduces incoming events into a series of high-level events**. This component includes some other sub-components, one of which in particular is the packet processing pipeline consisting of:
- **Packet analysis** - Analyze low-level protocols from data link to transport layers.
- **Session analysis** - Analyze application layer protocols (FPT, HTTP, DNS,...).
- **File analysis** - Extract files included in the packet being analyzed.

Event engine's capabilities can be improved by integrating plugins from external sources.

### Script Interpreter
***
Scripts are *event handlers* which represents security policies and rules, and can define what to be done against certain types of events seen.

Scripts are written in *Zeek scripting language*.

Can perform event processing/handling by utilizing existing frameworks, installing external Zeek packages or writing custom scripts.

## Zeek cluster
***
Each Zeek instance can only utilize a single core on a machine. A Zeek cluster takes advantage of the multi-core nature of a single device and the multi-device nature of a system by letting Zeek run as a cluster of multiple instances of different roles, with multiple instances/processes either installed on a single machine or on different machines.

The architecture of each Zeek instances/roles of a Zeek cluster is defined below.

![](Pasted%20image%2020230126115217.png)

### Frontend

A component (mechanism placed on a dedicated separated machine or on-host) that load-balances incoming traffic to other Zeek instances that are performing network analysis jobs.

### Manager

The central Zeek process that manages other Zeek network analyzing instances. The Manager receives all notices and logs from other Zeek instances and generates concise log outputs from discrete Zeek sources and data. The Manager can also perform other functionalities and analysis that requires a centralized log view.

### Proxy/Logger

**Logger**: A Zeek instance that receives all logs and notices from Zeek network analyzing instances for the Manager node. If used, the Manager can just retrieve logs from Logger.

**Proxy**: A zeek instance that can offload data or arbitrary workload. Can greatly increase cluster scalability if utilized rather than performing the same tasks on a single Manager node. 

### Worker

The Zeek node that performs analysis of all network traffic coming through an interface or belonging to a defined traffic flow.

## Zeek logs
***
Could either be produced in TSV (Tab-Separated Values) or JSON format.

## Zeek scripts

**Callables:**
- **Function**
- **Event handler**
	- An ***event handler*** must be used to handle an ***event type*** that was declared beforehand
	- Invoked in 3 different ways:
		- ***From the event engine***: When the event engine detects an event for which you have defined a corresponding event handler, it queues an event for that handler. The handler is invoked as soon as the event engine finishes processing the current packet and flushing the invocation of other event handlers that were queued first.
		- ***With the `event` statement from a script***
		- ***Via the `schedule` expression in a script***
	- There can be multiple ***event handler***'s body definitions for the same ***event type***, all of which will be executed against the matching event type.
- **Hooks**
	**Hooks**, like functions, are synchronous and immediately invoked in a script; and like event handlers,  there can be multiple hook's body definitions all of which will be executed. The user can interrupt the execution chain of hooks by using `break` in a hook's body.


**Zeek_init() and Zeek_done()**

![](Pasted%20image%2020230203113838.png)





## Zeek events

Find the right events for specific use cases using `grep` or `bif` files.

# Zeek on ATD

## Current policy scripts

- **misc/loaded-scripts**: logging which scripts are loaded into zeek on startup
- **tuning/defaults**: load some default tuning parameters including:
> - maximum file size for extraction
> - TTL for next TCP fragments
> - warnings on Zeek's startup

- **misc/capture-loss**: Create logs and notices whenever there's too much packet loss or too little packets flowing in. In a cluster setup, the logs also include the peer's ID.
- **misc/stats**: Logs a number of different types of statistics.
- **frameworks/software/vulnerable**: Creates a notice everytime a software logged into ***software.log*** has a version as old or older than the version ranges defined by the user. Lists of softwares and their corresponding vulnerable version ranges can be stored in a TXT record of a domain name. This policy script sends hourly TXT lookup request for that domain name (which is assigned to the `option` variable `vulnerable_versions_update_endpoint`) and store the response.
- **frameworks/software/version-changes**: Creates a notice everytime an interesting software defined in `option interesting_version_changes` changes its' version.
- **?protocols/dns/detect-external-names?**: *(Why do we do dis tho)* Creates a notice whenever there are DNS A results pointing to the user's local network but the domain name is not part of the user's local zone.
- **protocols/ftp/detect**: Creates a notice whenever an FTP reply for a successful SITE exec request is seen on the wire.
- **protocols/conn/known-hosts**: Logs unique hosts that have completed TCP handshake, i.e. have established a connection. Users can specify the address zone to watch for new connections by modifying the value of `option host_tracking` in the script, with the available values are ***LOCAL_HOSTS, REMOTE_HOSTS, ALL_HOSTS, NO_HOSTS***. This keeps track of the list of IPs that were logged and flush the list once every 24hrs.
- **?protocols/conn/known-services?**: (*The script seems to only be triggered once `connection_state_remove` event is invoked*) Logs unique services seen from a host.
- **protocols/ssl/known-certs**: Logs unique certs (identified by a pair of IP address and DER formatted cert's SHA1 hash) seen on the wire.
- **?protocols/ssl/validate-certs?**: *(Certs are complicated asf)* Creates a notice everytime Zeek can't validate a X.509 cert.
- **protocols/ssh/geo-data**: Looks up the geo location of the external IP address in an SSH connection and generates a notice if the location is in a list of watched locations. In order for this script to actually look up the geo location, Zeek needs to be built with `libmaxminddb`.
- **protocols/ssh/detect-bruteforcing**: Creates a notice when a host (that's not in the whitelist defined in `const ignore_guessers &redef`) attempts too many failed SSH connections in a certain period of time. The default parameters currently are 30 failed login attempts with each attempts being no more than 30 min apart.
- **protocols/ssh/interesting-hostnames**: Creates a notice whenever there's a successful SSH connection involving *DNS, SMTP, mail, POP, IMAP, WWW, FTP* servers. The hostname is retrieved by a simple reverse DNS lookup for each IP addresses found in the SSH connection.
- **protocols/http/detect-sqli**: Creates a notice when there're (currently only URI-based) SQL injection attacks seen on the wire. The current thresholds to fire a notice is 50 SQL injection attempts with each attempts no more than 5 min apart. If a victim host is under fire (number of SQL injections targeting that host crosses the threshold) then a notice notifying about the host is also invoked.
- **frameworks/files/hash-all-files**: Adds MD5 & SHA1 file analyzers.
- **frameworks/files/detect-MHR**: Performs lookup for a file hash seen on the wire using Team Cymru's malware hash database. The lookup is done through a TXT dns request, and if the result shows that the hash has a detection rate above a certain threshold (by default is 10) then a notice for that hash is created.



## Base scripts

### files

- **pe**: Logs information resides in pe files' various headers (file headers, pe headers,...).
- **hash**: Logs hashes for files found.
- **extract**: Extracts and stores files found.
- **x509**: Logs information about x509 cert files found.

### frameworks

- **analyzer**: Allows users to perform some actions (disable, enable, register associated port,...) on analyzers.
- **notice**: Provides a mean for users to create notices for events users deem to be interesting, then those notices can be stored as logs (***notice.log***) or be sent as emails.
- **dpd (dynamic protocol detection)**: Activates port-independent protocol detection and selectively disables analyzers if protocol violations occur. A few words from the authors of Zeek:
>*Dynamic protocol detection (DPD) is a method by which Zeek identifies protocols on ports beyond those used as standard services. Rather than selecting which application protocol analyzer to use based on a connection’s server port, Zeek’s dynamic analyzer framework associates an analyzer tree with every connection. This analyzer tree permits Zeek to perform protocol analysis independently of port numbers.*
>
>*By using a set of signatures which match typical protocol dialogues, Zeek is able to look at payload to find the correct analyzers. When such a signature matches, it turns on the corresponding analyzer to confirm it. Zeek can turn off analyzers when it becomes obvious that they are parsing the wrong protocol. This allows Zeek to use “loose” protocol signatures, and, if in doubt, try multiple analyzers in parallel.*
- **signatures**: Provides a low-level pattern matching through signatures. Whenever there is a match, users can raise a `signature match` event, invoke a protocol analyzer for the data that was matched, or choose an action based on the `Action` enum defined in the base scripts. Signatures can be matched against 2 types of data:
	- ***Network traffic***: A matching condition can be specified using:
		- Packet header
		- Packet payload
	- ***File Content***: Only the file *mime type* can be used for file matching.
	[Things to keep in mind when writing Zeek signatures](https://docs.zeek.org/en/v4.0.9/frameworks/signatures.html#things-to-keep-in-mind-when-writing-signatures)
- **packet-filter**: Sets BPF filters. Users can add `capture_filters` or `restrict_filters` (in BPF filter expressions, ofc) by extending the same name tables defined in `base/init-bare.zeek`. The resulting filter sets will then be automatically compiled and installed by this framework.
- **?software?**
- **?control?**: Defines the foundational events through which Zeek instances can receive and handle remote runtime commands. The foundational events haven't yet been defined, so they can be consider just like interface definitions in programming languages.
- **intel**: Provides a mechanism for matching incoming data against a set of intelligence data. Each intelligence entry can also have an expiration (by default the expiration is set to never). The process of using the **intel** framework is divided into 3 stages:
	- ***Loading intelligence***: Loads intelligence data either by loading a file (using the input framework) or using the built-in `Intel::insert` function (could be useful when users want to add a new piece of intelligence during runtime, for example, to block a newly discovered IP).
	- ***Grabbing data for matching***: Points out exactly the piece of data that the framework should attempt to match against the intelligence data storage.
	- ***Handling matched intelligence***: The users can specify the action to perform whenever a piece of data was matched against the intelligence data storage. By default, a `Intell::match` event is raised.
- **?config?**: Allows users to modify option values (as defined by the `option` keyword in the scripts) during runtime by updating the value through config files.
- **?sumstats?**: Provides a mechanism to create summary statistics using measurements like sum or average for pieces of arbitrary number or string data received from the network traffic. The processing flow is done through 3 stages:
	- ***Creating a sumstat stream***: Users create a sumstat stream and assign the piece of data they want to perform statistical summarization on to the stream, then give that piece of data a `Sumstats::Key` if necessary.
	- ***Creating a reducer***: Users declare a reducer which will perform measurements like averaging or counting data. The reducer must be associated with a sumstat stream using the stream's ID.
	- ***Creating the final sumstat***: Users create a sumstat instance. The instance can be defined by: (i) a time interval (epoch) after which the reducer's result is collected and a callback function for when the epoch resets, (ii) a threshold to monitor the reducer's result and a callback function to define the action when the threshold is crossed, or (iii) a combination of (i) and (ii).
- **tunnel**: Logs  `conn_id` in tunneling communications and keeps track of tunnels' state (newly discovered, active, close, expired). Currently supporting monitoring on known ports for *ayiya, teredo, gtpv1, and vxlan*.

### misc

### packet-protocols

### protocols

### utils

## Packages

### BZAR

#### bzar_config_options
- Options to whitelist hosts
- Options to enable/disable reporting for each techniques/sub-techniques
- Options for sumstats' thresholds

#### SMB

##### Techniques:

- **T1021.002** - ***Remote services***: SMB/Admin Windows Shares
- **T1021.002** -> **T1570** - ***Remote services: SMB/Admin Windows Shares*** followed by ***Lateral Tool Transfer***

##### bzar_smb_consts
- Declaring sensitive shares. By default it's *c$* and *admin$* 

##### bzar_smbx_detect

- Watch for any SMB creating/reading/writing messages targeting sensitive shares: *c$* and *admin$*

#### DCE-RPC

##### Techniques:
- **T1003.006** - ***OS Credential Dumping: DCSync***
- **T1070.001** ***-  Indicator Removal on Host: Clear Windows Event Logs***
- **T1569.002 -** ***System Services: Service Execution***
- **T1047 -** ***Windows Management Instrumentation***
- **T1053.002 -** ***Scheduled Task/Job: At***
- **T1053.005 -** ***Scheduled Task/Job: Scheduled Task***
- **T1529 -** ***System Shutdown/Reboot***
- **T1547.004 -** ***Boot or Logon Autostart Execution: Winlogon Helper DLL***
- **T1547.010 -** ***Boot or Logon Autostart Execution: Port Monitors***
- **T1016 -** ***System Network Configuration Discovery***
- **T1018 -** ***Remote System Discovery***
- **T1033 -** ***System Owner/User Discovery***
- **T1049 -** ***System Network Connections Discovery***
- **T1069 -** ***Permission Groups Discovery***
- **T1082 -** ***System Information Discovery***
- **T1083 -** ***File & Directory Discovery***
- **T1087 -** ***Account Discovery***
- **T1124 -** ***System Time Discovery***
- **T1135 -** ***Network Share Discovery***

##### bzar_rpc_consts
- Declares specific RPC protocol sequences to look for in DCE RPC events seen on the wire. Each sequences is mapped to a ATT&CK technique.
- Adds additional UUID-to-endpoint mapping and some opcodes to Zeek's `DCE_RPC::uuid_endpoint_map`  and `DCE_RPC::operations`.

##### bzar_rpc_detect
- Monitors and raises a notice if certain RPC protocol sequences are observed in DCE/RPC response events. The sequences to watch for are defined in **bzar_rpc_consts**.


### bro-is-darknet
- Allows the user to provide a list of addresses in `used_address_space` and `darknet_address_space`.
- Provides a new function `Site::is_darknet` which takes in an address as the argument then determines whether or not the address belongs to the dark address space (as defined by the 4 modes of working: `DARKNET, NOT_ALLOCATED, DARKNET_OR_NOT_ALLOCATED, DARKNET_AND_NOT_ALLOCATED`) and the 2 previously mentioned lists.

### bro-simple-scan
- Detects and raises notices for scan attempts (`Address_Scan`, `Port_Scan`, `Random_Scan`). The notice threshold are different for remote and local scanning hosts.
- Provides integration with bro-is-darknet to detect darknet scanning *(for some reasons)*.

### Eternal-Safety
