## **GFS(Google File System)**

### What does it do?
- set out to build a DFS
- willing to change anything(e.g. client API: gfs-open, gfs-read...)
- apps modification/cooperation

---

### Design constraints
- compliant to failure in norm
    bugs, human errors, power loss
    maintaining, detecting and recovery
- files are huge
    multi-GB are common. 
    Comparing to billions of KB files
- most modification are appends
    random writes are practically non-exist
    many files are written once and read many times sequentially
- two types of reads
    large streaming read
    small random reads
    google gathers websites and build inddddd indice. skip and forward, always in forwad dimention.
- sustained bandwidth 7 latency

### Architectual Design
- GFS cluster
    - a single master
    - multiple chunk servers
    - chunk servers can be accessed by clients
    - ooooooo linux servers
- File
    - represent as fix-sized chunk(like object in Ceph)
    - 64-bits unique ID
    - stored at chunk server(deliver directly from chunk server, reducing throughput latency)
    - 3 way replication
- Master
    - metadata
    - management
- Clients
    - master the metadata
    - data from chunk servers
    - it doesn't use VFS
    - no caching at clients. I/O are usually streaming, no temporary cache .....

### Why Single Master Design?
- simple. Multi-masters have to cooperate or replicate master.
- master only ensuadsf chunk locations
- clients typically ask for multiple chunk locations in one request
- chunk size 64MB or 64bits(ID)
- fewer requests to master
- fewer metadata entries
- fragmentation(64MB per chunk)
- 64bits per 64MB chunk, cache chunk ID in memory
- chunk location
    - no persistent: clients just know the chunks but not their locations
    - startup: send info to master
- operation logs
    - metadata updates are logs
    - take global snapshots to truncate logs

### Lease
- 60s time-out
- renew indefinitely