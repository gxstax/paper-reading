[译文原件](nsdi15-paper-sharma.pdf)
Wormhole 是 Facebook 内部使用的一个 Pub-Sub 系统，目前还没有开源。它和 Kafka 之类的消息中间件很类似。但是它又不像其它的 Pub-Sub 系统，Wormhole 没有自己的存储来保存消息，它也不需要数据源在原有的更新路径上去插入一个操作来发送消息，是非侵入式的。其直接部署在数据源的机器上并直接扫描数据源的 transaction logs，这样还带来一个好处，Wormhole 本身不需要做任何地域复制（geo-replication）策略，只需要依赖于数据源的 geo-replication 策略即可。
---
