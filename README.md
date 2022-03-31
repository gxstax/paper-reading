# 程序员不可不读的论文
你要不断提高你的认知，你要不断努力探索事务最本质的东西！



[toc]

## 分布式数据调度

### Paxos算法

* [Bigtable: A Distributed Storage System for Structured Data](https://static.googleusercontent.com/media/research.google.com/en//archive/bigtable-osdi06.pdf)

* [The Chubby lock service for loosely-coupled distributed systems](https://static.googleusercontent.com/media/research.google.com/en//archive/chubby-osdi06.pdf)

* [The Google File System](https://static.googleusercontent.com/media/research.google.com/en//archive/gfs-sosp2003.pdf)

* [MapReduce: Simplifed Data Processing on Large Clusters](https://static.googleusercontent.com/media/research.google.com/en//archive/mapreduce-osdi04.pdf)

* [Paxos Made Live – An Engineering Perspective](https://static.googleusercontent.com/media/research.google.com/en//archive/paxos_made_live.pdf) :Paxos 算法细节

* [Neat Algorithms - Paxos ](http://harry.me/blog/2014/12/27/neat-algorithms-paxos/) :比较容易读懂的

  

  **如果你要自己实现 Paxos 算法，这里有几篇文章供你参考。**

* [Paxos Made Code](https://www.inf.usi.ch/faculty/pedone/MScThesis/marco.pdf) -代码库[libpaxos](http://libpaxos.sourceforge.net/)

* [Paxos for System Builders](http://www.cnds.jhu.edu/pub/papers/cnds-2008-2.pdf)

* [Paxos Made Moderately Complex](http://www.cs.cornell.edu/courses/cs7412/2011sp/paxos.pdf)

* [Paxos Made Practical](https://web.stanford.edu/class/cs340v/papers/paxos.pdf)

* [Plain Paxos Implementations Python & Java](https://github.com/cocagne/paxos)

* [A go implementation of the Paxos algorithm](https://github.com/xiang90/paxos)

* [Zab: High-Performance broadcast for primary-backup systems](https://www.semanticscholar.org/paper/Zab%3A-High-performance-broadcast-for-primary-backup-Junqueira-Reed/b02c6b00bd5dbdbd951fddb00b906c82fa80f0b3?p2df)

  

### Raft算法

* [In search of an Understandable Consensus Algorithm (Extended Version) ](https://raft.github.io/raft.pdf) - [Raft 一致性算法论文译文](https://www.infoq.cn/article/raft-paper/)

  **Raft 算法的动画演示**

* [Raft – The Secret Lives of Data](http://thesecretlivesofdata.com/raft/)

* [Raft Consensus Algorithm](https://raft.github.io/)

* [Raft Distributed Consensus Algorithm Visualization](http://kanaka.github.io/raft.js/)

### 逻辑钟和向量钟

* [Dynamo: Amazon’s Highly Available Key Value Store](http://bnrg.eecs.berkeley.edu/~randy/Courses/CS294.F07/Dynamo.pdf)
* [马萨诸塞大学课程 Distributed Operating System](http://lass.cs.umass.edu/~shenoy/courses/spring05/lectures.html) -第10节 [Clock Synchronization ](https://lass.cs.umass.edu/~shenoy/courses/spring05/lectures/Lec10.pdf)
* [Why Vector Clocks are Easy](https://riak.com/posts/technical/why-vector-clocks-are-easy/)
* [Why Vector Clocks are Hard](https://riak.com/posts/technical/why-vector-clocks-are-hard/)

### Gossip 协议

* [Efficient Reconciliation and Flow Control for Anti-Entropy Protocols](https://www.cs.cornell.edu/home/rvr/papers/flowgossip.pdf)

  **Gossip图画演示**

* [gossip visualization](https://rrmoelker.github.io/gossip-visualization/)

### 分布式数据库

* [Amazon Aurora: Design Considerations for High Throughput Cloud –Native Relation Databases](https://www.allthingsdistributed.com/files/p1041-verbitski.pdf)

* [Spanner: Google’s Globally-Distributed Database](http://static.googleusercontent.com/media/research.google.com/zh-CN//archive/spanner-osdi2012.pdf)

  **基于 Spanner 论文的开源实现 **

* [CockroachDB](https://github.com/cockroachdb/cockroach)

* [TiDB](https://github.com/pingcap/tidb)

  



## 其他

