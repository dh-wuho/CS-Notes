## **Redundancy** 
### Resiliency in Storage
- replication: erasure encoding(storage cost)
- parity(computation cost)

### EC
- super set and both(parity and replication)
- form of FEC(Forward Error Correction)
    - msg length(k)
    - code word length(m)
    - n = m + k
    - code rate = k/n

### Voting
- send bit 3 times
- 8 cases, accept the majority

### Reed-Solomon codes
- family of codes
- old

### RAID parity
n = k + 1
N(wordsize) = 1

RAID 6
n = k + 2
N = 1

### Erasure encoding
- k disks & data
- n disks
- m disks of code, n = k + m
- w-bit words

Assume 1 w-bit word/disk
$$data = d_0, d_1, ... d_{k-1}$$
$$code = c_0, c_1, ... c_{m-1}$$

$$c_0 = a_{0, 0}d_0 + ... + a_{0, k-1}d_{k-1}$$
$$...$$
$$c_{m-1} = a_{m-1, 0} + ... + a_{m-1, k-1}d_{k-1}$$

### Example
1. Parity: "+" - XOR; "*" - AND; with 1.

2. Max distance separable MDS
- reconstruct from any m failures

3. Longer W
- richer set of erasure codes
- must define arithmetic
- positive numbers
- overflow
- Galois Field/Finite Field

Linux RAID 6 (W = 8)
$$c_0 = a_{0, 0}d_0 + a_{0, 1}d_1$$
$$c_1 = a_{1, 0}d_0 + a_{1, 1}d_1$$
$$p = d_0 xor d_1$$

4. Diagonal. Use multiple disks to recover
In storage system, bits are lost rather than flipped.

### Python lib: rs
RSCoder(h, m) encode and decode
RS: Reed-Solomon