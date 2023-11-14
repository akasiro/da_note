# 1 基本概念
在绝大部分场景下，Spark-SQL相比Hive都表现出了更好的查询性能，以及更低的资源开销代价。
```sql
set hive.smart.router.failback.enable=false; --来避免Spark回滚MR
```

| 概念 | 说明 |
| -- | -- |
| Application | Hive一个Sql可能有多个，但是Spark-sql只会有一个 |
| Jobs | 一个application里有多个。针对每个action（e.g. reduce/collection/count等)spark会创建一个执行图和启动一个Spark Job|
| Stages | 每个job有多个。实现最终RDD所需数据转化的步骤|
|tasks| 每个stage有多个，是实际调度执行的最小单元，等价于Mapreduce中的map/reduce task,包含读取的输入数据量和shuffle 生成和读取的数据量等|


## 2 分片参数详解
Spark任务执行过程通常会包含多轮Stage，不同按照操作类型不同大致上可以分为Scan、Shuffle、Merge三类：

**Scan操作**：从HDFS scan读取的实际输入数据量，等同于Mapreduce作业中的map阶段，其task个数等价于map task数，根据输入数据量和分片大小划分；对应于Stage页面上Input列不为空的stage；

**Shuffle操作**：任务执行过程中通过shuffle进行数据交换，等同于Mapreduce作业中的reduce阶段，其task个数等价于reduce task数，spark的reduce处理完后的临时数据不会固化到HDFS，而是继续以shuffle write的方式写到本地磁盘，等待下一轮stage读取，直到最终输出stage；对应于Stage页面Shuffle Read列不为空的stage；

**Merge操作**：当任务最重输出到HDFS上的文件平均大小低于一定阈值时会触发小文件合并操作，以减少HDFS上的文件数，具体可参考：[https://kstack.corp.kuaishou.com/article/3308](https://kstack.corp.kuaishou.com/article/3308) ； 文本的参数对于Merge操作无影响