Resiliency in Storage
- replication: erasure encoding
- parity

EC
- super set and both(parity and replication)
- form of FEC

Forward Error Correcticy
- msg length(k)
- code word length(m)
- n = m + k
- code rate = k/n

Voting
- send bit 3 times
- 8 cases

Read-Soloman codes
- family of codes
- old

RAID parity
n = k + 1
v(wordsize) = 1

RAID 6
n = k + 2
N = 1

Erasure encoding
- k disks & data
- n disks
- m disks of code, n = k + m
- w-bit words

Assume 1 w-bit word/disk
d0, d1, ... d(k-1)
c0, c1, ... c(m-1)
c0 = a(0, 0)d0 + ... + a(0, k-1)d(k-1)
...
c(m-1) = a(m-1, 0) + ... + a(m-1, k-1)d(k-1)

Max distance separable MDS
- construct from any m failures

Longer w
- richer set of erasure codes
- must define  // todo
- // todo
- overflow
- GaloisField/FiniteField

Linux RAID 6
c0 = a(0, 0)d0 + a(0, 1)d1
c1 = a(1, 0)d0 + a(1, 1)d1
p = d0 xor d1