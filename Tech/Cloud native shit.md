# Principles

- Cloud native apps are usually designed using a **microservice architecture**, following the **12-principle methodology**
- Cloud native apps have a number of core principles that they are built upon, namely:
	- **Automation** of the development/deployment workflow, scaling, self-fixing
	- Prioritizing **stateless components** (not keeping track of statistics and shit), making auto-scaling, self-healing smoother
	- **Micro-perimeters** hardening all components, with a concern of zero trust in mind
	- **Resilient** to failure, having multiple point-of-failures and is capable of self-healing and auto-scaling
	- **Platform-agnostic**, with **polyglot components**, enabling the app to not be freely built using the best tech choices in the market
	- **Immutable infra components**

# Building blocks
- Apps are usually composed of a bunch of containers (the micro-services), and a orchestrator that manages them containers