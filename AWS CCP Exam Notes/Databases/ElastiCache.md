- The same way [[RDS]] is to get managed Relational Databases, ElastiCache is used to get managed [[Redis]] or [[Memcached]] caches
- Caches are in-memory databases with high performance, low latency
- Helps reduce load off databases for read intensive workloads
- AWS takes care of OS maintenance / patching, optimizations, setup, configuration, monitoring, failure recovery and backups

##### Solution Architecture
[[ELB]] -> [[EC2]] -> R/W from DB (slow) and R/W from cache (fast)
reduces pressure from main database