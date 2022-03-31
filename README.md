<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [程序员不可不读的论文](#%E7%A8%8B%E5%BA%8F%E5%91%98%E4%B8%8D%E5%8F%AF%E4%B8%8D%E8%AF%BB%E7%9A%84%E8%AE%BA%E6%96%87)
  - [分布式数据调度](#%E5%88%86%E5%B8%83%E5%BC%8F%E6%95%B0%E6%8D%AE%E8%B0%83%E5%BA%A6)
    - [Paxos算法](#paxos%E7%AE%97%E6%B3%95)
    - [Raft算法](#raft%E7%AE%97%E6%B3%95)
    - [逻辑钟和向量钟](#%E9%80%BB%E8%BE%91%E9%92%9F%E5%92%8C%E5%90%91%E9%87%8F%E9%92%9F)
    - [Gossip 协议](#gossip-%E5%8D%8F%E8%AE%AE)
    - [分布式数据库](#%E5%88%86%E5%B8%83%E5%BC%8F%E6%95%B0%E6%8D%AE%E5%BA%93)
  - [其他](#%E5%85%B6%E4%BB%96)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# 程序员不可不读的论文
你要不断提高你的认知，你要不断努力探索事务最本质的东西！



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

  **基于 Spanner 论文的开源实现**

* [CockroachDB](https://github.com/cockroachdb/cockroach)

* [TiDB](https://github.com/pingcap/tidb)

  



## 其他

