[论文原件](lsmtree.pdf)
N 多年前，谷歌发表了 Bigtable 的论文，论文中很多很酷的方面，其一就是它所使用的文件组织方式，这个方法更一般的名字叫 Log Structured-Merge Tree。LSM 是当前被用在许多产品的文件结构策略：HBase、Cassandra、LevelDB、SQLite，甚至在 MongoDB 3.0 中也带了一个可选的 LSM 引擎（Wired Tiger 实现的）。LSM 有趣的地方是它抛弃了大多数数据库所使用的传统文件组织方法。实际上，当你第一次看它时是违反直觉的。这篇论文可以让你明白这个技术。（如果读起来有些费解的话，你可以看看中文社区里的这几篇文章：[文章一](https://www.cnblogs.com/siegfang/archive/2013/01/12/lsm-tree.html)、[文章二](https://kernelmaker.github.io/lsm-tree)。）
---
