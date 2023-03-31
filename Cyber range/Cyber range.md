Research tasks:
> - Research a method to inject vulns into virtual machines
> - Define the back-end tech stack for the range:
> 	- Punicci (TOSCA processor)
> 	- Devstack (Openstack minimum installation)
> 	- Ansible (VM configuration)
> - Build a running PoC


# 1. INTRODUCTION

## 1.1 Motivation
Trend of cyber sec attack -> The need for cybersec training 

[The cyber range: A guide](https://www.nist.gov/system/files/documents/2020/06/25/The%20Cyber%20Range%20-%20A%20Guide%20%28NIST-NICE%29%20%28Draft%29%20-%20062420_1315.pdf)
[Inefficiencies in Cyber-Security Exercises Life-Cycle: A Position Paper](https://ceur-ws.org/Vol-2269/FSS-18_paper_3.pdf)
[Modeling attack and defense scenarios for cyber security exercises](https://is.muni.cz/publication/1543326/proceeding.pdf#page=9) - Cyber training gamification

## 1.2 Research questions

## 1.3 Scope of the thesis

# 2. BACKGROUND

## 2.1. Research/Design methods (BACKGROUND)

#### [Model-driven engineering](https://citeseerx.ist.psu.edu/document?repid=rep1&type=pdf&doi=3f21283d368ca0c88ea4f93a8afd1d4a84538467)

## 2.2. RELATED WORK

### Write about literature review 

### 2.2.1. TAXONOMY

#### [A Review of Cyber-Ranges and Test-Beds: Current and Future Trends](https://arxiv.org/pdf/2010.06850.pdf)

![](Pasted%20image%2020221130173707.png)


### 2.2.2. SCENARIO LIFE CYCLE

#### [The Scenario Development Workflow (SDW)](https://www.cyberwiser.eu/system/files/CYBERWISER_D4.3_Cyber_training_scenarios_and_scenario_development_method_InitialVersion_v1.0.pdf)

The workflow of the scenario development method follows an iterative approach between its steps to allow the creation of complex scenarios, consisting of the following high-level steps:  
1) Designing
2) Creation  
3) Validation  
4) Instantiation  
5) Configuration and Testing  
6) Finalization



#### [The cybersecurity exercise life cycle](https://sci-hub.se/10.1109/FIE.2017.8190713)




### 2.2.3. SCENARIO MODELING AND GENERATION

#### [HYPERVISOR AGNOSTIC SCENARIO DEFINITION LANGUAGE FOR CYBER RANGES](file:///home/dumbcate/Downloads/60a20e7e32394552b060b0cabb12abf4-1.pdf)

#### [ADLES: A specification for cyber range development](https://sci-hub.se/https://doi.org/10.1016/j.cose.2017.12.007)

"One of the major challenges hampering the rapid adoption of hands-on learning in computing   and cybersecurity is the difficulty of providing safe, secure, dynamic, and repeatable educational computing environments [16, 17]. At present, creating hands-on virtual educational environments  
requires specialized Information and Communication Technology (ICT or IT) knowledge and skills in addition to significant time dedication [18]. In addition, there is currently no standard for specifying educational computing environments, making it impossible to share them without having to manually rebuild and redeploy most of each environment every time it is needed."

"In order to help greatly increase the number of hands-on cybersecurity and information  
technology activities available to students we created a project with the following two aims:

A) Help improve educational institutions’ processes and efficiency when creating and deploying  
virtual educational computing environments.

B) Enable the straightforward sharing for instructors and institutions of complete virtual  
educational computing environments.

The contributions reported in this article toward achieving the two aims above are:  
###### ***1. ADLES Specification***: 

Designed and developed a formal specification language that enables the complete and self-contained formal description of virtual educational environments. The specification is composed of 3 files:

> - **The Package specification**: Describes the contents of an ADLES exercise package and contains metadata for the package itself.
>- **The Exercise specification**: Describes the virtual environment for an educational exercise. 
>- **The Infrastructure specification**: Describes the hardware and software infrastructure that will be hosting the environments.

###### 2. ***ADLES Tool-set***: 

Designed and developed a free and open source system that is capable of semi-automatically creating and deploying hands-on exercise environments described by an ADLES specification."



#### [Modeling and executing cyber security exercise scenarios in cyber ranges](file:///home/dumbcate/Downloads/1-s2.0-S0167404822000347-main.pdf)
##### Preparation

Scenario Modeling In this phase of the scenario, a logical network topology with vulnerabilities was modeled, attacker and defender capabilities to exploit or defend those vulnerabilities were defined, and probable attack and defense strategies were analyzed and logically verified

We simplified the cybersecurity operation in an exercise into five general operations: infrastructure orchestrator, vulnerability injector, attacker agent, defender agent, and traffic generator
-> **Variables used in the Scenario Modeling language**:
- Infra orchestrator
- Vuln injector
- Attacker agent
- Defender agent
- Traffic generator

These operations have their specific properties in a cybersecurity exercise scenario; to simplify things, **the properties of our scenario modeling language are presented in BNF** (Backus-Naur  
form) [\[1\]](https://isaaccomputerscience.org/concepts/dsa_toc_bnf?examBoard=all&stage=all)

The scenario modeling was performed through our developed scenario language, which was verified logically by [Datalog](https://docs.racket-lang.org/datalog/)

Multiple models have been proposed for modeling the attackers’ and defenders’ behavior during a cyber engagement: [Cyber Kill Chain](https://books.google.com.vn/books?hl=en&lr=&id=oukNfumrXpcC&oi=fnd&pg=PA80&ots=fcLO7qj_-c&sig=HD0ULx4QN69syevMXQ1KK-9aDcQ&redir_esc=y#v=onepage&q&f=false) methodology to protect computer network damage espionage, [MITRE](https://attack.mitre.org/.), ...

-> **Four basic predicates for our scenario modeling**: 1) *link*, 2) *vulnerable*, 3) *capability*, and 4) *killchain*

##### Dry run

##### Execution

##### Evaluation

##### Repetition


#### [Model-driven Cyber Range training - A Cyber Security Assurance Perspective](https://www.researchgate.net/publication/339379617_Model-Driven_Cyber_Range_Training_A_Cyber_Security_Assurance_Perspective)

#### [BUILDING NEXT GEN CYBER RANGE WITH CRACK](https://www.researchgate.net/publication/341001295_Building_next_generation_Cyber_Ranges_with_CRACK#pfb)
**Previous work was** [Automating the generation of Cyber Range Virtual Scenarios with VSDL](https://www.researchgate.net/publication/333405505_Automating_the_Generation_of_Cyber_Range_Virtual_Scenarios_with_VSDL)

**Verification phase**: [Datalog](https://www.techopedia.com/definition/3915/datalog)

**SDL types built upon TOSCA's base types:**
1. ***System types***
- Has a relationship with the *Compute* type
- Represent arbitrary system/device in the CR (workstations, firewalls, phones,...)
- Can also be related to *Artifact* (some piece of data like a password file), *Software*, *User* nodes

2. ***Scenario-specific types***
- *Vulnerability node*
	**Must** specify **the conﬁguration procedure**, i.e., the steps injecting the vulnerability in the scenario, **and the exploit operations**, i.e., how the attacker uses the vulnerability.
- *Principal node*
	Represents the participant in the exercise, i.e. a Red or Blue Team-er.
- *Goal* node
	Represents the objective which the associated *Principal* node has to achieve.

3. ***Relationship types***
Some new relationship types have to be introduced to satisfy the exercise configuration.
> For instance, a relationship *GetsUsername* can connect a *Vulnerability* node to a *User* node. The meaning is that the *Vulnerability* node reads the username property of the *User* node and uses it for the conﬁguration of the vulnerability. To exemplify, think of a user enumeration vulnerability where an attacker enumerates the users of a service by testing a dictionary of common usernames. To properly conﬁgure it, one has to make sure that the target username belongs to the dictionary.

The example below shows a configuration excerpt of primitive SDL types *User* and *Principal*, and scenario-specific types *User.Linux*, *Vulnerability.Linux.EoP* and *Goal.GainPrivilege*.
Note that *User* has vulnerability capability, because a user might be vulnerable.
*Principal* should have knowledge as requirements to represent the information obtained by the *Principal* before the exercise.
![](Pasted%20image%2020221128154828.png)


#### [Cybersecurity education and training support system Cyris](https://www.researchgate.net/publication/323501641_Cybersecurity_Education_and_Training_Support_System_CyRIS)

#### [Security Scenario Generator (SecGen): A Framework for Generating Randomly Vulnerable Rich-scenario VMs for Learning Computer Security and Hosting CTF Events](https://www.usenix.org/system/files/conference/ase17/ase17_paper_schreuders.pdf)


### 2.2.4. TECHNOLOGY AND ARCHITECTURE

For citation in related work description:
- [Terraform](https://arxiv.org/pdf/2205.10676.pdf)

#### [Virtualization and Automation for Cybersecurity Training and Experimentation](https://sci-hub.se/10.1007/978-3-030-69255-1_15)

#### [Docker vs Virtualisation](https://sci-hub.se/https://doi.org/10.1016/j.procs.2020.04.152)

#### [Automation of a cyber range - Vagrant and CVE program for the creation of a vulnerable system](file:///home/dumbcate/Downloads/ABDELKEFI_99021700_2021.pdf)

#### [Cyber range automation, a bedrock for AI applications](https://ceur-ws.org/Vol-3056/paper-10.pdf)

Use Ansible, Terraform, Caldera to automate security research. Caldera has an intuitive GUI for managing agents,  adversarial profiles, and operations.

The automated solution is split into 3 main steps: provisioning, configuration, and attack simulation.
- **Provisioning**: Terraform
- **Configuration**: Ansible
- **Attack simulation**: Caldera


#### [AIT Cyber range](https://www.skopik.at/ait/2021_jowua.pdf)

Has pretty much the same technology as [Cyber range automation, a bedrock for AI applications)](#[Cyber%20range%20automation,%20a%20bedrock%20for%20AI%20applications](https://ceur-ws.org/Vol-3056/paper-10.pdf))

**Computing platform**: Openstack
**Infra provisioning**: Terraform
**Software provisioning**: Ansible

***





#### [THE CYBER RANGE AT THE UNIVERSITY OF DELAWARE](https://udspace.udel.edu/server/api/core/bitstreams/4ecbc6e5-9c81-4ce5-8c4e-e5db6153b88e/content)

#### [KYPO CYBER RANGE](https://docs.crp.kypo.muni.cz/basic-concepts/conceptual-architecture/)

# 3. DESIGN

## TOSCA

#### [TOSCA-based orchestration of complex clusters at the IaaS level](https://www.researchgate.net/publication/321231629_TOSCA-based_orchestration_of_complex_clusters_at_the_IaaS_level) 

#### Overview of TOSCA
**TOSCA base node types:**
- Compute
- Port
- Network
- Subnetwork
![](Pasted%20image%2020221128113112.png)

**A node config includes:**
- Node type
- Properties/Attributes
- Requirements/Capabilities
- Interfaces (operations to perform on the node by the orchestrator, can be standard or on-demand)

**A relationship config includes:**
> Is used to connect nodes
- Properties/Attributes
- Interfaces

**A node instance contains at least:**
- Node types
- Properties
- Requirements
> A relationship between two nodes exists when a requirement of a source node instance is bound to the name of the target.


#### [What is Tosca?](https://cloudify.co/what-is-tosca/)

The whole idea is to deploy services as a unique structure where nodes are part of the Node Template and the relationships between nodes are part of the Relationship Template. The combination of these two yields the Topology Template, which, with the addition of Plans, gives us the Service Template as the main aspect of the TOSCA model. Below is the representation of Structural Elements of a Service Template and their Relations

![](Pasted%20image%2020221128163933.png)

##### Node:
![](Pasted%20image%2020221215113801.png)

##### **Capability:**
**A Capability Type** ***is a reusable entity*** that describes a kind of capability that a Node Type can declare to expose. Requirements (implicit or explicit) that are declared as part of one node can be matched to (i.e., fulfilled by) the Capabilities declared by another node

**A Capability Definition** defines a named, typed set of data that can be associated with Node Type or Node Template to describe a transparent capability or feature of the software component the node describes.

![](Pasted%20image%2020221215113043.png)

![](Pasted%20image%2020221215113052.png)

![](Pasted%20image%2020221215111649.png)

##### **Requirement:**

**A Requirement Type** ***is a reusable entity*** that describes a kind of requirement that a Node Type can declare to expose. The TOSCA Simple Profile seeks to simplify the need for declaring specific Requirement Types from nodes and instead rely upon nodes declaring their features sets using TOSCA Capability Types along with a named Feature notation.

**The Requirement definition** describes a named requirement (dependencies) of a TOSCA Node Type or Node template which **needs to be fulfilled by a matching Capability definition declared by another TOSCA modelable entity**.

The requirement definition may itself include the specific name of the fulfilling entity (explicitly) or provide an abstract type, along with additional filtering characteristics, that a TOSCA orchestrator can use to fulfill the capability at runtime (implicitly).

![](Pasted%20image%2020221215111625.png)


##### **Relationship Type**:

**A Relationship Type** ***is a reusable entity*** that defines the type of one or more relationships between Node Types or Node Templates.

![](Pasted%20image%2020221215114131.png)


##### **Interface Type:**

**An Interface Type** ***is a reusable entity*** that describes a set of operations that can be used to interact with or manage a node or relationship in a TOSCA topology.

![](Pasted%20image%2020221215112808.png)

-  **tosca.interfaces.node.lifecycle.Standard**  
This lifecycle interface defines the essential, normative operations that TOSCA nodes may support.

```
tosca.interfaces.node.lifecycle.Standard:

derived_from: tosca.interfaces.Root  

create:  
description: Standard lifecycle create operation.  
configure:  
description: Standard lifecycle configure operation.  
start:  
description: Standard lifecycle start operation.  
stop:  
description: Standard lifecycle stop operation.  
delete:  
description: Standard lifecycle delete operation.
```

- **tosca.interfaces.relationship.Configure**
The lifecycle interfaces define the essential, normative operations that each TOSCA Relationship Types may support.

```
tosca.interfaces.relationship.Configure:  

derived_from: tosca.interfaces.Root  

pre_configure_source:  
description: Operation to pre-configure the source endpoint.  
pre_configure_target:  
description: Operation to pre-configure the target endpoint.  
post_configure_source:  
description: Operation to post-configure the source endpoint.  
post_configure_target:  
description: Operation to post-configure the target endpoint.  
add_target:  
description: Operation to notify the source node of a target node  
being added via a relationship.  
add_source:  
description: Operation to notify the target node of a source node  
which is now available via a relationship.  
target_changed:  
description: Operation to notify source some property or attribute of  
the target changed
remove_target:  
description: Operation to remove a target node.
```






#### [Model-Driven Orchestration for Cloud Resources](https://ieeexplore.ieee.org/abstract/document/8814534)
#### [Model Driven Cloud Orchestration by Combining TOSCA and OCCI](https://www.swe.informatik.uni-goettingen.de/sites/default/files/publications/paper_0.pdf)
#### [Model-Based Cloud Resource Management with TOSCA and OCC](https://arxiv.org/pdf/2001.07900.pdf)
#### [Model-Driven Continuous Deployment for Quality DevOps](https://sci-hub.se/10.1145/2945408.2945417)
#### [Towards A Model-Driven Design Tool for Big Data Architectures](https://d1wqtxts1xzle7.cloudfront.net/45312742/PID4117503-libre.pdf?1462284285=&response-content-disposition=inline%3B+filename%3DTowards_A_Model_Driven_Design_Tool_for_B.pdf&Expires=1671595853&Signature=N5GZasceAsSrskGeOnR09kAXrlyhrMHO-DdvsAlJfoT-jJBP4DSPFyxJBQWb9yxLLuUWcluQAIC13hnuCKMQOqJqyTfQ9NeFXjU0dht99olPkedEJLXHjqnSU53kdzohIzk9dzcZpxB5RluZedXIE4zvbTGSLCyeq2pCuZMOlnSj79MLcfRe1kKVeywYh6v1xwPiGfb8dfsITOFA2swZSwiKIN9vUoneJTIRvTJVGjMpC7O7jgW2HB4z3S1uYbkfuv8oT0KtBWsu1S6GSpqjxiX6e2iUDy7kO7a7bfGZU1ZEJR63T-I8rbQTttSGy7KMfstnA4vJoxny651~qYy0Vw__&Key-Pair-Id=APKAJLOHF5GGSLRBV4ZA)


## Ansible
##### 1. Installing Ansible
##### 2. Setting up an inventory
##### 3. Connecting to the managed hosts
##### 4. Setting up playbooks
- Playbooks contain Plays (which are the basic unit of Ansible execution). This is both an ‘execution concept’ and how we describe the files on which ansible-playbook operates. Playbooks are written in YAML and are easy to read, write, share and understand. To learn more about playbooks, see Ansible playbooks.

- **Plays**: The main context for Ansible execution, this playbook object maps managed nodes (hosts) to tasks. The Play contains variables, roles and an ordered lists of tasks and can be run repeatedly. It basically consists of an implicit loop over the mapped hosts and tasks and defines how to iterate over them.
> - **Roles**: A limited distribution of reusable Ansible content (tasks, handlers, variables, plugins, templates and files) for use inside of a Play. To use any Role resource, the Role itself must be imported into the Play.
> - **Tasks**: The definition of an ‘action’ to be applied to the managed host. Tasks must always be contained in a Play, directly or indirectly (Role, or imported/included task list file). You can execute a single task once with an ad hoc command using `ansible` or `ansible-console` (both create a virtual Play).
> - **Handlers**:A special form of a Task, that only executes when notified by a previous task which resulted in a ‘changed’ status.

- **Modules**: The code or binaries that Ansible copies to and executes on each managed node (when needed) to accomplish the action defined in each Task. **You can invoke a single module with a task, or invoke several different modules in a playbook**. Ansible modules are grouped in collections.
- **Plugins**: Pieces of code that expand Ansible’s core capabilities, they can control how you connect to a managed node (connection plugins), manipulate data (filter plugins) and even control what is displayed in the console (callback plugins).




## Openstack

### [Devstack](https://docs.openstack.org/devstack/latest/index.html)


## xOpera

### [Examination and Comparison of TOSCA Orchestration Tools](file:///home/dumbcate/Downloads/Examination_and_Comparison_of_TOSCA_Orchestration_Tools-1.pdf)

### [Puccini](https://puccini.cloud/clout/)

#### [Sommelier](https://sci-hub.se/10.1007/978-3-319-94764-8_1)


# 4. IMPLEMENTATION
# 4. CONCLUSION

# 5. FUTURE WORK

##### [CyRIS: a cyber range instantiation system for facilitating security training](https://www.researchgate.net/publication/311621279_CyRIS_a_cyber_range_instantiation_system_for_facilitating_security_training)
**Content Deﬁnition** This module takes the content description and generates the corresponding training content for an LMS (Learning Management System), currently using Moodle 
##### [Empirical Study on Cyber Range Capabilities, Interactions and Learning](https://webthesis.biblio.polito.it/19257/1/tesi.pdf)

"This study revealed that number of cyber range learning capabilities mainly lack the use of evaluation tools for reflection. Humans have a unique capacity to adapt their skills and competences to different natural and cultural environment and this adaptation requires the building of suitable mental representations, which help in learning and creating new concepts, skills, preferences, motivations, and emotional tendencies on the individual, social and cultural levels. Variety of factors must be considered in the effective design of cyber range learning platforms in use of training and education purpose"


"Content Deﬁnition: This module takes the content description and generates the corresponding training content for an LMS (Learning Management System), currently using Moodle."

"The cyber range description ﬁle is for describing the composition and content of the cyber range. It can be created manually or by automated tools"

##### [Alpaca: Building Dynamic Cyber Ranges with Procedurally-Generated Vulnerability Lattices](https://sci-hub.se/https://doi.org/10.1145/3299815.3314438)

Basically about a way to create CR scenarios using Vuln lattices. The construction of lattices require the following components:
1. Development of a vulnerability database. Each vulnerability includes pre-conditions, post-conditions, a configuration, and a weight.  
2. An efficient planning engine that is capable of sequencing vulnerabilities to reach the specified end goal from the specified initial state.  
3. A means of “merging” configurations so that the vulnerabilities in a path have compatible configurations; a “path-configuration” is generated by merging the individual vulnerability configurations.  
4. A procedure for finding paths whose path-configurations are compatible, and grouping these compatible paths together to generate a vulnerability lattice and a “lattice-configuration.”  
5. A means of generating scripts from a lattice (technically, from its lattice-configuration) to generate a cyber range that supports the vulnerabilities specified in that lattice.

![](Pasted%20image%2020221130171140.png)

![](Pasted%20image%2020221130171152.png)



##### [Advanced Tools for Cyber Ranges](https://www.ll.mit.edu/sites/default/files/page/doc/2018-05/22_1_2_Braje.pdf)

"To emulate the Internet, we leverage several techniques. We sample 10s of 1000s of sites very shallowly to scrape their content and efficiently and realistically rehost this scraped content by using our custom-written software."

ALIVE - application for range build-out
LARIAT - application for traffic generation and range control


