## **DFS(Distributed File System)**

How to compare different file systems? What's the measurements of DFS?

---

### 1. View
- hierarchical FS
- global view: all clients have the same view
- local view: client can have different views, mount

### 2. State
- open on clients also open on server(connection)
- server must remember
- client must close

comparison(statefull vs stateless)

- message is longer(stateless)
- server is simpler
- idempotent(stateless)
- lock or lease
    stateful    ->  client locks a file
    stateless   ->  lease a period of time

### 3. Cache
Where does the caching occur?
- clients: memory/disks
- server: memory

Cache Size Choice: once it's determined, changing it is risky!(Cache background....any solution to it)
Cache Replacement Policy: LRU, approximate policy - clock

Consistency: replication, update
Cache Consistency Policy:
- UNIX file consistency: no design on it,it leaves to the application to handle the consistency problem. e.g. Google doc.
- write-through-cache(relatively write-through-disk)
- dealyed-write: delay some files
- write-on-close: delay one single file
- delayed-write-on-close: the lifetime of files are usually short

### 4. Replication
##### block-based access
- raw block: typically high performance
- applicaiton must provide all data manage
- leverage: e.g. ls file
- clustered file server

##### file-based access
- Virtualization. Benefits over block-based access: 
    abstraction hides the implementation
    server independence
- Fine-grained data management
    permission
    backup(e.g. S3)
- share data
- cost
    high CPU per request
    network technology
    infi band
    RDMA, rget, rput
