# 数据库的分类

数据库可以简单的分为 `MySQL` 和 `NOSQL` 两类。这里的 `NOSQL` 不是 `NO SQL` 的意思，他的意思是 `Not Only MySQL`

**MySQL与NoSQL之间的区别：**

1、MySQL是一个基于表格设计的关系数据库，而NoSQL本质上是非关系型的基于文档的设计。

2、MySQL数据库，覆盖了巨大的IT市场；具有固定市场的MySQL数据库包含一个庞大的社区。而NoSQL数据库是最新的到来，与MySQL相比，社区正在慢慢发展。

3、MySQL的严格模式限制并不容易扩展，而NoSQL可以通过动态模式特性轻松扩展。

4、MySQL中创建数据库之前需要详细的数据库模型，而在NoSQL数据库类型的情况下不需要详细的建模。

5、MySQL提供了大量的报告工具，可以帮助应用程序有效，而NoSQL数据库缺少用于分析和性能测试的报告工具。

6、MySQL是一个关系数据库，其设计约束灵活性较低；而NoSQL本质上是非关系型的，与MySQL相比，它提供了更灵活的设计。

7、MySQL中使用的标准语言是SQL；而NoSQL中缺乏标准的查询语言。

# mongodb是什么

mongodb是一种数据库，它可以储存键值对类型的数据（json，字典）。目前流行的数据库是 MySQL ，但它并不利于初学者入门。我之前发过 Tinydb，Sqlite3 等数据库的讲解，都比较简单，那我这次来发一下mongodb数据库。

# mongodb 的数据库、集合

一个数据库下可以有多个集合，集合里存储数据。集合可以理解为 SQL 数据库中的表。

# 使用 Python 操作 mongodb

## 安装 mongodb

终端运行

```python
pip install pymongo
```

## 连接数据库

```python
client = pymongo.MongoClient(host, port)
```

`host`是地址，`port` 是端口。

## 切换数据库

### 第一种方法

```python
db_name = client['db_name']
```

其中 `db_name` 是你的数据库名。

### 第二种方法

```python
db_name = client.get_database('db_name')
```

其中 `db_name` 是你的数据库名。

### 第三种方法

```python
db_name = client.db_name
```

## 切换集合

```python
db_name.test
```

其中 `test` 是集合名，没有这个集合会自动创建。

## 添加数据

```python
def add_data(data):
    result = db_name.test.insert_one(data)
    print(result.inserted_id)
```

其中 `test` 是集合名。

添加数据用 `insert_one` 方法。

其中，data 是要插入的数据，它的类型是键值对，即 Python 中的字典。这是一条合法的 data

```python
{"name":"XiaoMing","password":123456}
```

特殊的，如果要插入在指定 id ，可以这样写

```python
result = db_name.test.insert_one({_id:1,"xxx":"xxx",...})
```

也可以插入多个，只需要把 data 变成

```python
[{"name":"XiaoMing","password":123456},{"name":"XiaoHong","password":123456}]
```

## 删除数据

```python
db.test.remove(查询表达式, isJustOne)
```

查询表达式有这些

-------

| 语法 | 操作       | 格式                     |
| ---- | ---------- | ------------------------ |
| $eq  | 等于       | {:}                      |
| $lt  | 小于       | {:{$lt:}}                |
| $lte | 小于或等于 | {:{$lte:}}               |
| $gt  | 大于       | {:{$gt:}}                |
| $gte | 大于或等于 | {:{$gte:}}               |
| $ne  | 不等于     | {:{$ne:}}                |
| $or  | 或         | {$or:[{},{}]}            |
| $in  | 在范围内   | {age:{$in:[val1,val2]}}  |
| $nin | 不在范围内 | {age:{$nin:[val1,val2]}} |

例如，删除 test 集合中 name 是 XiaoMing 的所有数据

```python
db.test.remove({name:"XiaoMing"})
```

## 修改数据

`db.collection.update(查询表达式,新值,选项)` 选项: {upsert : true/false, multi : ture/false}

- upsert：默认为 false , 作用：无相应记录是否insert,与mysql中的replace同
- multi：默认为 false ,  作用：是否作用于多条

```python
#替换文档，将name为zhangsan的第一个文档替换为{"name":"lisi","age":10}
db.stu.update({"name":"zhangsan"},{"name":"lisi","age":10})
$set修改器，指定要更新的key，key不存在则创建，存在则更新。
#将name为zhangsan的所有文档替换为{"name":"lisi","no":'100'}
db.stu.update({"name":"zhangsan"},{$set:{"name":"lisi","no":'100'}},{multi:true})
```

## 查找数据

```python
#查找所有数据
db.集合名.find()
# 查找到所有匹配数据
db.集合名.find({条件文档})
# 只返回匹配的第一个数据
db.stu.find({age:{$gt:16}}) #查询年龄大于16的记录
db.stu.find({$or:[{age:{$gt:18}},{name:"xiaoming"}]) #查询年龄大于18或者名字是xiaoming的记录
#使用$where后面写一个函数，返回满足条件的数据
db.stu.find({$where:function(){return this.age>20}})
#用于读取指定数量的文档
db.集合名称.find().limit(NUMBER)
#对查询结果排序（参数1升序，参数-1降序）
db.集合名称.find().sort({字段:1,...}) 
#统计结果中的文档数
db.集合名称.find({条件}).count()
```

# 最后

请大家持续关注，我会发表更多好文章！