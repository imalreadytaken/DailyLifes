##数据类型
- STRING
	- 最大长度 : 512M
	- 二进制安全，可以存图、序列化对象等
	- 可进行append，incr等操作
- LISTS
	- Redis列表只是单纯的字符串列表 
> Redis Lists are simply lists of strings, sorted by insertion order. It is possible to add elements to a Redis List pushing new elements on the head (on the left) or on the tail (on the right) of the list.

	- 最大长度：2^32-1 = 4294967295

##集群
- 扩充节点
	- 增加节点时，