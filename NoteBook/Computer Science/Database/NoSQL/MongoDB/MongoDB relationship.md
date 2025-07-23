---
LINK:
  - "[[NoSQL]]"
  - "[[Database]]"
  - "[[MongoDB Advanced Query Methods]]"
  - "[[MongoDB]]"
  - "[[MongoDb operation ]]"
tags: 
---





MongoDB 中的关系可以是：
- 1:1 (1对1)
- 1: N (1对多)
- N: 1 (多对1)
- N: N (多对多)




## 嵌入式关系
> [!hint]+ 使用嵌入的方法，把用戶地址嵌入到用戶的文檔中
> ```jsx
> {
>    "_id": ObjectId ("52ffc33cd85242f436000001"),
>    "contact": "987654321",
>    "dob": "01-01-1991",
>    "name": "Tom Benzamin",
>    "address": [
>       {
>          "building": "22 A, Indiana Apt",
>          "pincode": 123456,
>          "city": "Los Angeles",
>          "state": "California"
>       },
>       {
>          "building": "170 A, Acropolis Apt",
>          "pincode": 456789,
>          "city": "Chicago",
>          "state": "Illinois"
>       }]
> } 
> ```
> 以上数据保存在单一的文档中，可以比较容易的获取和维护数据。 你可以这样查询用户的地址：
> ```jsx
> db.users.findOne ({"name": "Tom Benzamin"},{"address": 1})
> ```
> 注意：以上查询中 **db** 和 **users** 表示数据库和集合。
> 
> 这种数据结构的缺点是，如果用户和用户地址在不断增加，数据量不断变大，会影响读写性能


## 引用關係
引用式关系是设计数据库时经常用到的方法，这种方法把用户数据文档和用户地址数据文档分开，通过引用文档的 **id** 字段来建立关系。

```jsx
{
   "_id":ObjectId("52ffc33cd85242f436000001"),
   "contact": "987654321",
   "dob": "01-01-1991",
   "name": "Tom Benzamin",
   "address_ids": [
      ObjectId("52ffc4a5d85242602e000000"), // id作為索引連接到別的表格
      ObjectId("52ffc4a5d85242602e000001")
   ]
}

```
我们可以读取这些用户地址的对象id（ObjectId）来获取用户的详细地址信息。
这种方法需要两次查询，第一次查询用户地址的对象id（ObjectId），第二次通过查询的id获取用户的详细地址信息。
```jsx
var result = db.users.findOne({"name":"Tom Benzamin"},{"address_ids":1})
var addresses = db.address.find({"_id":{"$in":result["address_ids"]}})
```


## 数据库引用
https://www.runoob.com/mongodb/mongodb-database-references.html



























