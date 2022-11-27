## Definition
REST is the software architectural style for a system which defines the interface for the communication between applications or devices.

REST aims to provide a uniform interface which [decouples](Decoupling%20definition.md) 2 sides of a communication, especially in the interaction between a client and a server in a client-server architecture.

## Constraints
RESTful designs has to conform to the 6 following constraints:
1.  **Client-server architecture**
Per REST's aim, the communication between a system and its' clients should be as separated as possible, thus conforming to the client-server architecture.
2. Statelessness
RESTful systems, the receiving end of a network interaction, should not have to store any session information about the interaction. Each packets sent from the sender should be understood in isolation, therefore removing the context-memorizing responsibility from the receiver and enhance its' performance.
To accomplish this, session information can instead be stored by the clients or intermediary components.
3. Cacheability
4. Layered system
5. Code on demand (optional)
6. Uniform interface