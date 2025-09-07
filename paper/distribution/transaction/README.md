# 分布式事务-Paxos

Paxos 算法，是莱斯利·兰伯特（Lesile Lamport）于 1990 年提出来的一种基于消息传递且具有高度容错特性的一致性算法。但是这个算法太过于晦涩，所以一直以来都属于理论上的论文性质的东西。其真正进入工程圈，主要是来源于 Google 的 Chubby lock——一个分布式的锁服务，用在了 Bigtable 中。直到 Google 发布了下面这两篇论文，Paxos 才进入到工程界的视野中来。

* [Bigtable: A Distributed Storage System for Structured Data](Bigtable-ADistributedStorageSystemForStructuredData.md)
* [The Chubby lock service for loosely-coupled distributed systems](The-Chubby-lock-service-for-loosely-coupled-distributed-systems.md)

Google 与 Bigtable 相齐名的还有另外两篇论文。

* [The Google File System](he-Google-File-System.md)
* [MapReduce: Simplified Data Processing on Large Clusters](MapReduce-SimplifiedDataProcessingOnLargeClusters.md)


不过，这几篇文章中并没有讲太多的 Paxos 算法上的细节,反而在

* [Paxos Made Live - An Engineering Perspective](PaxosMadeLive-AnEngineeringPerspective.md)
这篇论文中提到了很多工程实现的细节。这篇论文详细解释了 Google 实现 Paxos 时遇到的各种问题和解决方案，讲述了从理论到实际应用二者之间巨大的鸿沟。

Paxos 算法的原版论文比较晦涩，也不易懂。这里推荐一篇比较容易读的——
* [Neat Algorithms - Paxos](NeatAlgorithms-Paxos.md)
