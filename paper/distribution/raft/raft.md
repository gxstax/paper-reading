
[论文-原件](raft.pdf)
---
因为 Paxos 算法太过于晦涩，而且在实际的实现上有太多的坑，并不太容易写对。所以，有人搞出了另外一个一致性的算法，叫 Raft。


<h1 align="center">寻找一种易于理解的一致性算法</h1>
<div align="center">Diego Ongaro and John Ousterhout
Stanford University</div>

## 摘要
Raft 是一种用于管理复制日志的共识算法。它的结果与（多实例）Paxos 等价，效率也与 Paxos 相当，但其结构与 Paxos 不同；这种差异使得 Raft 比 Paxos 更易于理解，同时也为构建实际系统提供了更好的基础。为了增强可理解性，Raft 将共识的关键要素——如领导者选举、日志复制和安全性——进行了分离，并通过强制实施更强的一致性，减少了需要考虑的状态数量。一项用户研究的结果表明，学生学习 Raft 比学习 Paxos 更容易。Raft还包含一种新的集群成员变更机制，该机制通过使用重叠多数（overlapping majorities）来保证安全性。

## 1. 引言
共识算法使得一组机器能够作为一个协调一致的群体协同工作，并能够容忍其中部分成员的故障。正因如此，它们在构建可靠的大型软件系统中扮演着关键角色。在过去十年中，Paxos [15, 16] 一直主导着共识算法的讨论：大多数共识算法的实现都基于 Paxos 或受其影响，Paxos 也成为了向学生讲授共识知识的主要载体。

然而，尽管有许多尝试使其更易于理解，Paxos 本身仍然非常难以掌握。此外，它的架构需要进行复杂的修改才能支持实际系统。因此，无论是系统构建者还是学生，都对 Paxos 感到困难重重。

在我们自己也经历了与 Paxos 的艰难斗争之后，我们决定寻找一种新的共识算法，以期为系统构建和教育提供更坚实的基础。我们的方法颇为不同：我们的首要目标是可理解性——我们能否为实际系统定义一种共识算法，并以一种比 Paxos 显著更容易学习的方式来描述它？此外，我们希望该算法能够帮助建立系统构建者所必需的直觉认知。重要的不仅仅是算法“能工作”，更要让人一眼就能明白“它为什么能工作”。

这项工作的成果是一种名为 Raft 的共识算法。在设计 Raft 时，我们应用了特定的技术来提升其可理解性，包括模块化分解（Raft 将领导者选举、日志复制和安全性分离开来）和状态空间缩减（与 Paxos 相比，Raft 减少了非确定性的程度，以及服务器之间可能不一致的方式）。一项在两所大学针对 43 名学生开展的用户研究表明，Raft 显著比 Paxos 更容易理解：在学习了两种算法之后，其中 33 名学生回答关于 Raft 的问题表现优于回答关于 Paxos 的问题。

Raft 在许多方面与现有的共识算法相似（最著名的是 Oki 和 Liskov 提出的 Viewstamped Replication [29, 22]），但它也包含了几项创新特性：

* 强领导者（Strong Leader）：Raft 采用了一种比其他共识算法更强的领导形式。例如，日志条目只能从领导者流向其他服务器。这简化了复制日志的管理，也使 Raft 更易于理解。

* 领导者选举（Leader Election）：Raft 使用随机化定时器来选举领导者。这种方法只需在任何共识算法都必需的心跳机制上增加极少的复杂性，却能简单而快速地解决选举冲突。
* 成员变更（Membership Changes）：Raft 改变集群服务器集合的机制采用了一种新的联合共识（joint consensus） 方法，在配置转换期间，两个不同配置的多数派会重叠。这使得集群在配置变更过程中仍能正常运行。

--- 校验--
## 2. 复制状态机
一致性算法通常应用在「复制状态机」(*replicated state machines*)上下文环境中[37](#anchor-37)。状态机在服务集群中可以计算同一状态的相同副本，即使一些服务发生宕机依然能够继续工作。复制状态机被用来解决分布式系统中的容错问题。例如像[GFS](#anchor-8),[HDFS](#anchor-38),[RAMCloud](#anchor-33)等大规模系统，通常用一个单独的状态复制机来负责leader选举和保存配置信息，来保证领导者崩溃时该副本仍能存活。使用复制状态机的例子包括[Chubby](#anchor-2)和[ZooKeeper](#anchor-11).

![图1](images/raft-1.png)
<a id="raft-1"><font color="#A7535A"> **图-1:**</font></a>复制状态机架构。一致性算法会处理客户端发送的包含状态机指令的复制日志。状态机会根据日志中相同的命令顺序来处理，所以能保证相同的输出。

如图1所示，复制状态机是使用复制日志来实现的。每一台服务器都存储有状态机执行的一系列有序的命令日志。每一份日志都包含相同顺序的相同命令，所以每一台状态机会按照相同的顺序处理命令。因为状态机的顺序确定，所以计算的状态也是确定的，从而输出的也是相同的顺序。

保证复制日志的一致性，是一致性算法的工作。

## 3. 



## 引用文献
[1] BOLOSKY, W. J., BRADSHAW, D., HAAGENS, R. B.,KUSTERS, N. P., AND LI, P. Paxos replicated state
machines as the basis of a high-performance data store.In Proc. NSDI’11, USENIX Conference on Networked Systems Design and Implementation (2011), USENIX,pp. 141–154.

[2] BURROWS, M. The Chubby lock service for looselycoupled distributed systems. In Proc. OSDI’06, Symposium on Operating Systems Design and Implementation(2006), USENIX, pp. 335–350.

[3] CAMARGOS, L. J., SCHMIDT, R. M., AND PEDONE, F.Multicoordinated Paxos. In Proc. PODC’07, ACM Symposium on Principles of Distributed Computing (2007),ACM, pp. 316–317.

[4] CHANDRA, T. D., GRIESEMER, R., AND REDSTONE, J.Paxos made live: an engineering perspective. In Proc.PODC’07, ACM Symposium on Principles of Distributed Computing (2007), ACM, pp. 398–407.

[5] CHANG, F., DEAN, J., GHEMAWAT, S., HSIEH, W. C.,WALLACH, D. A., BURROWS, M., CHANDRA, T.,
FIKES, A., AND GRUBER, R. E. Bigtable: a distributed storage system for structured data. In Proc. OSDI’06,USENIX Symposium on Operating Systems Design and Implementation (2006), USENIX, pp. 205–218.

[6] CORBETT, J. C., DEAN, J., EPSTEIN, M., FIKES, A.,FROST, C., FURMAN, J. J., GHEMAWAT, S., GUBAREV,
A., HEISER, C., HOCHSCHILD, P., HSIEH, W., KANTHAK, S., KOGAN, E., LI, H., LLOYD, A., MELNIK,S., MWAURA, D., NAGLE, D., QUINLAN, S., RAO, R.,ROLIG, L., SAITO, Y., SZYMANIAK, M., TAYLOR, C.,WANG, R., AND WOODFORD, D. Spanner: Google’s globally-distributed database. In Proc. OSDI’12, USENIX Conference on Operating Systems Design and Implementation (2012), USENIX, pp. 251–264.

[7] COUSINEAU, D., DOLIGEZ, D., LAMPORT, L., MERZ,
S., RICKETTS, D., AND VANZETTO, H. TLA+ proofs.
In Proc. FM’12, Symposium on Formal Methods (2012),
D. Giannakopoulou and D. M´ery, Eds., vol. 7436 of Lecture Notes in Computer Science, Springer, pp. 147–154.

[8] GHEMAWAT, S., GOBIOFF, H., AND LEUNG, S.-T. The Google file system. In Proc. SOSP’03, ACM Symposium on Operating Systems Principles (2003), ACM, pp. 29–43.

[9] GRAY, C., AND CHERITON, D. Leases: An efficient faulttolerant mechanism for distributed file cache consistency.In Proceedings of the 12th ACM Ssymposium on Operating Systems Principles (1989), pp. 202–210.
[10] HERLIHY, M. P., AND WING, J. M. Linearizability: a correctness condition for concurrent objects. ACM Transactions on Programming Languages and Systems 12 (July 1990), 463–492.

[11] HUNT, P., KONAR, M., JUNQUEIRA, F. P., AND REED,B. ZooKeeper: wait-free coordination for internet-scale systems. In Proc ATC’10, USENIX Annual Technical Conference (2010), USENIX, pp. 145–158.

[12] JUNQUEIRA, F. P., REED, B. C., AND SERAFINI, M.Zab: High-performance broadcast for primary-backup systems. In Proc. DSN’11, IEEE/IFIP Int’l Conf. on Dependable Systems & Networks (2011), IEEE Computer Society,pp. 245–256.

[13] KIRSCH, J., AND AMIR, Y. Paxos for system builders.Tech. Rep. CNDS-2008-2, Johns Hopkins University,2008.

[14] LAMPORT, L. Time, clocks, and the ordering of events in a distributed system. Commununications of the ACM 21, 7 (July 1978), 558–565.

[15] LAMPORT, L. The part-time parliament. ACM Transactions on Computer Systems 16, 2 (May 1998), 133–169.

[16] LAMPORT, L. Paxos made simple. ACM SIGACT News 32, 4 (Dec. 2001), 18–25.

[17] LAMPORT, L. Specifying Systems, The TLA+ Language and Tools for Hardware and Software Engineers. AddisonWesley, 2002.

[18] LAMPORT, L. Generalized consensus and Paxos. Tech.Rep. MSR-TR-2005-33, Microsoft Research, 2005.

[19] LAMPORT, L. Fast paxos. Distributed Computing 19, 2 (2006), 79–103.

[20] LAMPSON, B. W. How to build a highly available system using consensus. In Distributed Algorithms, O. Baboaglu and K. Marzullo, Eds. Springer-Verlag, 1996, pp. 1–17.

[21] LAMPSON, B. W. The ABCD’s of Paxos. In Proc.PODC’01, ACM Symposium on Principles of Distributed
Computing (2001), ACM, pp. 13–13.

[22] LISKOV, B., AND COWLING, J. Viewstamped replication revisited. Tech. Rep. MIT-CSAIL-TR-2012-021, MIT,July 2012.

[23] LogCabin source code. http://github.com/logcabin/logcabin.

[24] LORCH, J. R., ADYA, A., BOLOSKY, W. J., CHAIKEN,R., DOUCEUR, J. R., AND HOWELL, J. The SMART
way to migrate replicated stateful services. In Proc. EuroSys’06, ACM SIGOPS/EuroSys European Conference on Computer Systems (2006), ACM, pp. 103–115.

[25] MAO, Y., JUNQUEIRA, F. P., AND MARZULLO, K.Mencius: building efficient replicated state machines for WANs. In Proc. OSDI’08, USENIX Conference on Operating Systems Design and Implementation (2008),USENIX, pp. 369–384.

[26] MAZIERES ` , D. Paxos made practical. http://www.scs.stanford.edu/˜dm/home/papers/paxos.pdf, Jan. 2007.

[27] MORARU, I., ANDERSEN, D. G., AND KAMINSKY, M.There is more consensus in egalitarian parliaments. In Proc. SOSP’13, ACM Symposium on Operating System Principles (2013), ACM.

[28] Raft user study. http://ramcloud.stanford.edu/˜ongaro/userstudy/.

[29] OKI, B. M., AND LISKOV, B. H. Viewstamped replication: A new primary copy method to support
highly-available distributed systems. In Proc. PODC’88,ACM Symposium on Principles of Distributed Computing (1988), ACM, pp. 8–17.

[30] O’NEIL, P., CHENG, E., GAWLICK, D., AND ONEIL, E.The log-structured merge-tree (LSM-tree). Acta Informatica 33, 4 (1996), 351–385.

[31] ONGARO, D. Consensus: Bridging Theory and Practice.PhD thesis, Stanford University, 2014 (work in progress).http://ramcloud.stanford.edu/˜ongaro/thesis.pdf.

[32] ONGARO, D., AND OUSTERHOUT, J. In search of an understandable consensus algorithm. In Proc ATC’14,USENIX Annual Technical Conference (2014), USENIX.

[33] OUSTERHOUT, J., AGRAWAL, P., ERICKSON, D.,KOZYRAKIS, C., LEVERICH, J., MAZIERES ` , D., MITRA, S., NARAYANAN, A., ONGARO, D., PARULKAR,G., ROSENBLUM, M., RUMBLE, S. M., STRATMANN,E., AND STUTSMAN, R. The case for RAMCloud. Communications of the ACM 54 (July 2011), 121–130.

[34] Raft consensus algorithm website.http://raftconsensus.github.io.

[35] REED, B. Personal communications, May 17, 2013.

[36] ROSENBLUM, M., AND OUSTERHOUT, J. K. The design and implementation of a log-structured file system. ACM Trans. Comput. Syst. 10 (February 1992), 26–52.

<a id="anchor-37">[37]</a> SCHNEIDER, F. B. Implementing fault-tolerant services using the state machine approach: a tutorial. ACM Computing Surveys 22, 4 (Dec. 1990), 299–319.

[38] SHVACHKO, K., KUANG, H., RADIA, S., AND CHANSLER, R. The Hadoop distributed file system.
In Proc. MSST’10, Symposium on Mass Storage Systems and Technologies (2010), IEEE Computer Society, pp. 1–10.
[39] VAN RENESSE, R. Paxos made moderately complex. Tech. rep., Cornell University, 2012.



