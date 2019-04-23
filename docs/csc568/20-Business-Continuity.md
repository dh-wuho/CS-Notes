## **Business Continuity**

### Outage
- preparation for
- response to
- recovery from

### Solution to address
- unavailability
- degrading problem

---------RPO(Recovery point objective)-----||outaget||------RTO(recovery time objective)

make RPO/RTO as close to the outage as possible

### recover vs restart
- Recovery: restoring preve copy of data, backup
- Restart: restoring mirrored consistent copy, online spare

### Dentify single point failure
- network
- power
- Disk/RAID failure
- site
- HBA
- Node

### Backup
- Backup is an additional data that can be used for restoring, and may not be the only purpose.
- Backup is used only if the primary is lost or not available.

### Retention
- spentimental
- archiving(regulation)
- kinds: full, accummulative, incrementals
- hot/cold backup / snapshot

### Backup and Restore

|              |Backup | Restore      |
|:------------:|:-----:|:------------:|
|Full          |O(n)   |O(n)          |
|Accummulative |O(nt)  |O(n)+O(acc)   |
|Incrementals  |O(inc) |O(n)+T*O(inc) |