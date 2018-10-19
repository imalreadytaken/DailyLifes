## 数据类型
- String
	- 最大长度 : 512M
	- 二进制安全，可以存图、序列化对象等
	- 可进行append，incr等操作
- List
	- Redis列表只是单纯的字符串列表 
> Redis Lists are simply lists of strings, sorted by insertion order. It is possible to add elements to a Redis List pushing new elements on the head (on the left) or on the tail (on the right) of the list.
	
	- 最大长度：2^32-1 = 4294967295
- Hash
	- 哈希表
- Set
	- 集合
- SortedSet
	- 有序集合

## 集群
- 键空间
	- 键空间分割为2^14=16384个slot，即集群节点个数最多16384个
	- 使用CRC16哈希算法，取结果的14位
- 节点信息
	- IP，PORT(TCP)
	- flags(master, slave ?)
	- 负责处理的哈希slot
	- 节点最近一次使用集群连接发送 PING 数据包（packet）的时间
	- 节点最近一次在回复中接收到 PONG 数据包的时间
	- 集群将该节点标记为下线的时间
	- 该节点的从节点数量
	- 如果该节点是从节点的话，那么它会记录主节点的节点 ID 。 如果这是一个主节点的话，那么主节点 ID 这一栏的值为 0000000
- 节点握手
	- 节点响应所有ping包
	- 不响应集群节点外的非ping数据包
	- 一个节点想加入一个集群，需要向集群中的节点发送MEET信息，强制让其承认自己是集群的一份子，之后一起向外传播新节点信息，最终集群中所有节点都承认其是集群的节点
	- 
- 扩充节点
	- 增加节点时，
