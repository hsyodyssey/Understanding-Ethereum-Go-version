# 00_万物的起点从geth出发

### go-ethereum 源代码目录结构
go-ethereum项目进行过若干次的重构，本文基于最新的版本Marljeh (version-1.9.25 updated time 2020-12) 进行分析。

目前，go-ethereum项目的目录结构如下所示。

	accounts/		以太坊的账户模块
	 ├──abi			解析Contracts中的ABI的信息
	 	├──abi.go	
	build/			主要是编译和构建的一些脚本
	core/			以太坊核心模块，包括核心数据结构，statedb及其算法实现
	 ├──state/
	 ├──types/		包括Block在内的以太坊核心数据结构
	 	├──block.go		以太坊block
		├──bloom9.go		一个Bloom Filter的实现
		├──transaction.go	以太坊transaction的数据结构与实现
		|──transaction_signing.go	用于对transaction进行签名的函数的实现
		|──tx_pool.go
		├──receipt.go		以太坊收据的实现，用于说明以太坊交易的结果
	├──consensus/
		├──consensus.go		共识相关的参数设定，包括Block Reward的数量
	├──console/
		├──bridge.go
		├──console.go		Geth Web3 控制台的入口
	├──eth/
	├──ethdb/				Ethereum 本地存储的相关实现, 包括leveldb的调用
		├──leveldb/			Go-Ethereum使用的与Bitcoin Core version一样的Leveldb作为本机存储用的数据库
	├──miner/
		├──miner.go			矿工的基本的实现。
		├──worker.go		矿工任务的模块，包括打包transaction
		├──unconfirmed.go
	├──p2p/					Ethereum 的P2P模块
	├──params				Ethereum 的一些参数的配置，例如: bootnode的enode地址
		├──bootnodes.go		bootnode的enode地址 like: aws的一些节点，azure的一些节点，Ethereum Foundation的节点和						Rinkeby测试网的节点
	├──state/
		├──statedb.go		StateDB结构用于存储所有的与Merkle trie相关的存储, 包括一些循环state结构
	├──rlp/					RLP的Encode与Decode的相关实现
	├──rpc/					Ethereum RPC客户端的实现
	├──les/					Ethereum light client的实现
	


 `geth console 2`
