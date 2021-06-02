# MySQL
## 体系架构
```
Server层
连接器
分析器
优化器
执行器
------------
存储引擎层
```

## 底层
### InnoDB记录结构
* VARCHAR(M)类型的列最多可以占用65535个字节
* MySQL对一条记录占用的最大存储空间是有限制的，除了BLOB或者TEXT类型的列之外，其他所有的列（不包括隐藏列和记录头信息）占用的字节长度加起来不能超过65535个字节。
* Dynamic(默认) Compressed COMPACT 
* 记录溢出 768字节 Compact(多个行记录, 真实数据最后有指针指针其他行记录) Compressed Dynamic 不会在记录的真实数据处存储字段真实数据的前768个字节，而是把所有的字节都存储到其他页面中，只在记录的真实数据处存储其他页面的地址

变长字段长度列表      | NULL值列表      | 记录头信息 | 列1的值 | 列2的值 | ...|隐藏列| 
逆序 1/2字节 不存NULL |逆序 二进制 整数 |5字节 | |...| row_id transaction_id roll_pointer |

列名	|是否必须	|占用空间	|描述
-|-|-|-
DB_ROW_ID	|否	|6字节	|行ID，唯一标识一条记录
DB_TRX_ID	|是	|6字节	|事务ID
DB_ROLL_PTR	|是	|7字节	|回滚指针

### 数据页
* 多种页
* 数据页用来存行记录
* 数据页有7部分, `File Header` `Page Directory`
* 每个数据页的`File Header`部分都有上一个和下一个页的编号，所以所有的数据页会组成一个`双链表`
* 每个记录的头信息中都有一个`next_record`属性，从而使页中的所有记录串联成一个`单链表`
## 存储引擎
### InnoDB
页
* 一个页中至少存放两行记录
* 主键生成策略: 自定义主键->unique主键->添加一个row_id
## 事务
### 四大特性
`Write Ahead Log`

### redo日志 
重做
只记录修改
### Undo日志
撤销
事务id
### 实战
```
>BEGIN [WORK]
>START TRANSACTION
>COMMIT [WORK]
>ROLLBACK
>SAVEPOINT [NAME]
>ROLLBACK [WORK] TO [SAVEPOINT]
>RELEASE SAVEPOINT [NAME]
```
## 隔离级别

## 锁
### 悲观锁和乐观锁区别
### 全局锁
### 表锁
### 行锁
### MVCC实现
两阶段锁协议
死锁
死锁处理: 检测 超时
检测死锁: 控制并发数量 优化数据库
### 间隙锁
## 索引
### 索引类型
* UNIQUE
* PRIMARY KEY
* 普通索引
* 组合索引
* 全文索引
### 底层数据结构选择
### 索引优化
## 


