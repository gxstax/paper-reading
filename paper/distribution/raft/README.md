# Raft

因为 Paxos 算法太过于晦涩，而且在实际的实现上有太多的坑，并不太容易写对。所以，有人搞出了另外一个一致性的算法，叫 Raft。其原始论文是
   * [RIn search of an Understandable Consensus Algorithm (Extended Version)](raft.md)
寻找一种易于理解的 Raft 算法。

几个不错的Raft算法动画演示：
  * [Raft - The Secret Lives of Data](https://thesecretlivesofdata.com/raft/)
  * [Raft Consensus Algorithm](https://raft.github.io/)
  * [Raft Distributed Consensus Algorithm Visualization](https://kanaka.github.io/raft.js/)