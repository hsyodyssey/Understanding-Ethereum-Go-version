# Understanding-Ethereum-Go-version
Title: Understanding Ethereum(Go version)｜理解以太坊(Go 版本源码剖析)
Author: Siyuan Han 
Updated date: 2021-07

## Preface 

Blockchain作为过去几年技术社区最热点话题之一, 每当我们提到它的时候，首先就会讨论到成功运用这项技术的最火热的几个系统。但是不管是讨论到以加密货币导向（Crypto-based）的Bitcoin Network, 还是致力于实现通用框架（General-Purpose）的Ethereum的时候，通常的文档往往只是在high-level的层面来讲述他们的架构。现在的技术社区有非常多的文档来讲述，这些Blockchain System背后的数据结构，以及类似双花，梅克尔树等区块链系统的专有问题。但是某天，我忽然想到，究竟miner是怎么从transaction pool中选取transaction，他们又是按照怎么的order被打包进区块链中的呢？我尝试去搜索了一下，发现鲜有文章提到这一层面的细节。本文作为我学习的记录，将会从源码的角度来深度解析区块链系统中各个模块的实现的细节。

笔者坚信，在未来的是五到十年内，这个世界的云端服务一定是两极分化的。一极是以大云计算公司（ie： Google，MS，Oracle，Snowflake，Alibaba）为代表的中心化服务，另一极就是以Blockchain技术作为核心的去中心化的世界。在这个世界中，Ethereum是当之无愧的领头羊。Ethereum 不光在Public Chain的层面取得了巨大的成功，而且Go-Ehtereum作为其优秀的开源实现，已经被广泛的订制，来适应不同的私有/联盟场景。所以，要想真正掌握好区块链系统的实现，研究好Ethereum的原理以及其设计思想是非常有必要。

本文档基于Go-Ethereum (Marljeh version-1.9.25 updated time 2020-12)对以太坊的源码结构，以及以太坊系统设计背后的细节，原理进行剖析。

go-ethereum是以太坊协议的Go语言实现版本，目前由以太坊基金会官方维护。除了本版本之外，Ethereum还有C++, Python，Java等其他语言版本。Go-ethereum在这些所有的社区版本中，版本更新最频繁，开发人员最多，问题相对较少。其他语言的Ethereum实现版本因为更新频率相对较低，隐藏问题未知，建议初学者首先从go-ethereum的视角来理解Ethereum网络与系统的设计实现。


## Contents
- [00_万物的起点从geth出发](00_geth.md) 
- [01_Account 与State 模型](01_account.md) 
- [02_一个Transaction的生老病死](02_transaction.md) 

-----------------------------------------------------------

#### Tips

- 以太坊是基于State模型的区块链系统，miner在update new Block的时候，会直接修改自身的状态（添加区块奖励给自己）。所以与Bitcoin不同的是，Ethereum的区块中，并没有类似的Coinbase的transaction。
- 在core/transaction.go 中, transaction的的数据结构是有time.Time的参数的。但是在下面的newTransaction的function中只是使用Local的time.now()对Transaction.time进行初始化。
- 在core/transaction.go 的transaction 数据结构定义的时候, 在transaction.time 后面的注释写到（Time first seen locally (spam avoidance)）, Time 只是用于在本地首次看到的时间。
- uncle block中的transaction 不会被包括到主链上。

## Reference 

- [1] Etheruem Yellow Paper [(Paper Link)](https://ethereum.github.io/yellowpaper/paper.pdf)
- [2] Ethereum/Go-Ethereum [(link)](https://github.com/ethereum/go-ethereum)
- [3] Go-ethereum code analysis [(Link)](https://github.com/ZtesoftCS/go-ethereum-code-analysis) 
- [4] Ethereum Improvement Proposals [(link)](https://github.com/ethereum/EIPs)
- [5] Mastering Bitcoin(Second Edition)


## Talks
- Succinct Proofs in Ethereum - Barry Whitehat, Ethereum Foundation [(Youtube)](https://www.youtube.com/watch?v=TtsDNneTDDY)
