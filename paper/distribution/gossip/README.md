# Gossip 一致性算法

用来做数据同步的 Gossip 协议的原始论文是
* [Gossip协议原始论文](paper/distribution/gossip/flow-gossip.md)
Gossip 算法也是 Cassandra 使用的数据复制协议。这个协议就像八卦和谣言传播一样，可以“一传十、十传百”传播开来。但是这个协议看似简单，细节上却非常麻烦。
Gossip 协议也是 NoSQL 数据库 Cassandra 中使用到的数据协议；


Gossip算法动画演示
* [Gossip Visualization](https://rrmoelker.github.io/gossip-visualization/)