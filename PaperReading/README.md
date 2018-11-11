# Words

- disassortative：异配
- intensity：强度
- vast：大量的
- preliminary：初步的；准备工作
- diversity：多样化；分歧

# 数据集

- 人工生成网络

  - Mark Newman：GN网络
    - 节点度和社区大小均匀分布
  - LFR数据集
    - 节点度和社区大小幂律分布
- 真实世界网络

  - Karate：空手道俱乐部网络
  - Dolphins：海豚网络
  - Friends ：高中生朋友关系网络
  - Polbooks：美国政治书网络
  - Word：单词网络
  - 。。。
- 方法分类
  - Modularity-based Algorithm
  - minimum description length based algorithm
  - conductance-based algorithm
- 方法
  - infomap：aims to optimize the minimum description length of a random walk procedure on the network


# 基于矩阵分解方法的社区结构划分算法研究

1. 全局信息
   - 使用PageRank算法计算节点的重要性

2. 局部信息
   - 如果节点具有较高的局部相似度，则它们应该被划分进同一个社团



# Community detection in Location-based Social Network: AN Entropy-based Approach

- 2016
- IEEE: International Conference on Computer and Information Technology
- 基于熵的相似度分析？
- 改进LPA
- 启发式
- 使用Frequency of Point of Interest 来代表 Location
- 基于结构的算法和基于location的算法结合计算相似度，以此作为边的权重

- 步骤

  1. 预划分
     1. 计算每个节点的聚类系数：

        ​	Cv = 2  * （v的邻居中的连边数量）/ （ v的度数  *  v的度数减一 ）

     2. 从大到小，依次选取没有标记的节点，将其和其没有标记的邻居划分为同一社区，并标记。至所有节点都被划分至特定社区。

  2. LPA（Weighted）

     1. 节点的平均权重：与邻居的相似度之和 / 度数
     2. 社区的总平均权重：社区中节点的平均权重的和
     3. 传播原则：如果**社区C1**中一个**节点v**与另外一个**社区C2**中的节点的相似度之**和**大于C1的总平均权重，则此节点的所属社区改为C2

- 总结

  - 效果优于LPA，LPA无权重，无初始划分。

  - 非常启发式，眼花缭乱。

  - 使用**基于Location的熵 **作为 **衡量节点间相似度**的 <u>部分</u> 标准。

    ​	v1的熵 + v2的熵 - v1v2的交集的熵	取指数

