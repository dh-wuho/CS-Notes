## **NAS(Network Attached Storage)**

**File-based** and **client-server** model.

---

### Protocol for NAS
- well-defined message and response
- support OS file operations

### Sketch
- client: initialize the request
- server: locate file, response the file through network, resolve conflict, prioritize
- design: 
    
    what APIs are needed to finish the jobs? (straightforward protocol)
    
    how elaborate the client/server is? (server has to handle many clients at the same time)
    
    so the simpler server is, the more concurrency server can be. e.g. JavaScript.

### Client
- translate users' calls to NAS protocol
- cooperate with server
- heart beat message
- cache(latency-tolerance device)

### Server:
- manage data(efficiently, reliably, securely...)
- could prefetch
- could upcalls(communicate with clients). upcalls are limited on stateful protocol

### Protocols of NAS
- NFS
    stateless
    hierarchy
    no upcalss from servers
- SMB(CIFS)
    more "talktive"
    generic: printer