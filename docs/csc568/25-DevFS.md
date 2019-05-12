## **Design Direct Access FS**

### New Storage Steak
- required
- existing OS
    - trap in OS
    - layers: buffer, VFS, device drivers
    - lots of overhead
- spend millions of cycles

### File System Architecture
- control planes
    - permission
    - consistency
    - sharing
- data planes
    - rw data
    - rw metadata

---

1. kernel FS
    - manage both control and data
    - trap into OS

2. lib FS
    - all ops on Application
    - hard to persist and share

3. Hybrid FS(lib + kernel)
    - common data and metadata, ops
    - no trap
    - kernel
        permission check
        share

4. Hybrid FS + trusted server
    - micro-kernel like approach
    - trusted control process facilitates, control plane ops
    - eliminte traps

5. Direct access FS

Challenges

- lib FS fails to satisfy 3 important properties: 
    - integrity. kernel FS manages in-memory and on-disks data.
    - single process
    - concurrency: crash concurrency, permission enforcement

Benefits

- can exploit the parallelism fo the hardware: multiple IO channels on CPU
- devFS can directly control
- volitile memory helps the creash recovery

Limitations

- increase the memroy footprint
- dev CPU
    are slower(to save power)
    are less capable(not have some features as ordinary CPU)
    less features(no backup, checksum, snapshot)
- separate devFS from environment

### Design Principles
1. Disentangle FS structure to embrace dev-level parallelism
2. Guarantee FS integrity without compromising direct access
3. Simplify crash recovery
4. Reduce dev memory footprint to FS
5. Enable minimal OS-level state share with dev FS

### Design
- move FS into device Hardware
- use device-level CPU and memory
- apps bypass OS for control and data planes
- Device handles: integrity, crash and recovery, security