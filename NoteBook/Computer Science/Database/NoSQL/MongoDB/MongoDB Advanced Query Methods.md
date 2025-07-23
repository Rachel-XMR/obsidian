---
LINK:
  - "[[Database]]"
  - "[[NoSQL]]"
  - "[[MongoDB]]"
  - "[[Computer Science/Database/NoSQL/MongoDB/MongoDB Operation.md]]"
tags:
---




## Embedded Documents 嵌入文档
 db.collection.find()此方法选择或查看集合的嵌入/嵌套文档并将光标返回到所选文档。



### Accessing embedded/nested documents
"field. nestedField": value 






| operation | description |                                                                                                                                                                                                                                                                   syntax                                                                                                                                                                                                                                                                   |     |
| :-------: | :---------: | :----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------: | --- |
|   $add    |     相加      |             <pre style="margin-top: 0px; margin-bottom: 10px; padding: 12px; border: 0px; font-size: 12pt; vertical-align: baseline; background-color: rgb(224, 224, 224); border-radius: 10px; color: rgba(0, 0, 0, 0.9); font-family: Consolas, monospace; overflow: auto; text-wrap: wrap; overflow-wrap: break-word; letter-spacing: 0.108px; text-align: left;"><span style="margin: 0px; padding: 0px; border: 0px; vertical-align: baseline;">{ $subtract: [ &lt;expression1&gt;, &lt;expression2&gt; ] }</span></pre>              |     |
| $subtract |     相減      |             <pre style="margin-top: 0px; margin-bottom: 10px; padding: 12px; border: 0px; font-size: 12pt; vertical-align: baseline; background-color: rgb(224, 224, 224); border-radius: 10px; color: rgba(0, 0, 0, 0.9); font-family: Consolas, monospace; overflow: auto; text-wrap: wrap; overflow-wrap: break-word; letter-spacing: 0.108px; text-align: left;"><span style="margin: 0px; padding: 0px; border: 0px; vertical-align: baseline;">{ $subtract: [ &lt;expression1&gt;, &lt;expression2&gt; ] }</span></pre>              |     |
| $multiply |     相乘      | <pre style="margin-top: 0px; margin-bottom: 10px; padding: 12px; border: 0px; font-size: 12pt; vertical-align: baseline; background-color: rgb(224, 224, 224); border-radius: 10px; color: rgba(0, 0, 0, 0.9); font-family: Consolas, monospace; overflow: auto; text-wrap: wrap; overflow-wrap: break-word; letter-spacing: 0.108px; text-align: left;"><span style="margin: 0px; padding: 0px; border: 0px; vertical-align: baseline;">{ $multiply: [ &lt;expression1&gt;, &lt;expression2&gt;, ... &lt;expressionN&gt; ] }</span></pre> |     |
|  $divide  |     相除      |              <pre style="margin-top: 0px; margin-bottom: 10px; padding: 12px; border: 0px; font-size: 12pt; vertical-align: baseline; background-color: rgb(224, 224, 224); border-radius: 10px; color: rgba(0, 0, 0, 0.9); font-family: Consolas, monospace; overflow: auto; text-wrap: wrap; overflow-wrap: break-word; letter-spacing: 0.108px; text-align: left;"><span style="margin: 0px; padding: 0px; border: 0px; vertical-align: baseline;">{ $divide: [ &lt;expression1&gt;, &lt;expression2&gt; ] }</span></pre>               |     |
|   $abs    |     絕對值     |                               <pre style="margin-top: 0px; margin-bottom: 10px; padding: 12px; border: 0px; font-size: 12pt; vertical-align: baseline; background-color: rgb(224, 224, 224); border-radius: 10px; color: rgba(0, 0, 0, 0.9); font-family: Consolas, monospace; overflow: auto; text-wrap: wrap; overflow-wrap: break-word; letter-spacing: 0.108px; text-align: left;"><span style="margin: 0px; padding: 0px; border: 0px; vertical-align: baseline;">{ $abs: &lt;number&gt; }</span></pre>                               |     |
|  $floor   |   取最接近的整數   |                              <pre style="margin-top: 0px; margin-bottom: 10px; padding: 12px; border: 0px; font-size: 12pt; vertical-align: baseline; background-color: rgb(224, 224, 224); border-radius: 10px; color: rgba(0, 0, 0, 0.9); font-family: Consolas, monospace; overflow: auto; text-wrap: wrap; overflow-wrap: break-word; letter-spacing: 0.108px; text-align: left;"><span style="margin: 0px; padding: 0px; border: 0px; vertical-align: baseline;">{ $floor: &lt;number&gt; }</span></pre>                              |     |












## Condition Operators 條件操作符
`{field: {operator:value}}`

| operator  | description |
| :-------: | :---------: |
|   `$gt`   |     大於      |
| `$lt`<br> |     小於      |
|  `$gte`   |    大於等於     |
|  `$lte`   |    小於等於     |
|   `$eq`   |     等於      |
|   `$ne`   |     不等於     |
|   `$in`   |   在指定的數據中   |
|  `$nin`   |  不在指定的數組中   |




### MongoDB 與 RDBMS WHERE語句比較

| 操作    | 格式                       | 范例                                          | RDBMS中的类似语句         |
| ----- | ------------------------ | ------------------------------------------- | ------------------- |
| 等于    | `{<key>:<value>}`        | `db.col.find({"by": "香港"}).pretty()`        | `where by = '香港'`   |
| 小于    | `{<key>:{$lt:<value>}}`  | `db.col.find({"likes":{$lt:50}}).pretty()`  | `where likes < 50`  |
| 小于或等于 | `{<key>:{$lte:<value>}}` | `db.col.find({"likes":{$lte:50}}).pretty()` | `where likes <= 50` |
| 大于    | `{<key>:{$gt:<value>}}`  | `db.col.find({"likes":{$gt:50}}).pretty()`  | `where likes > 50`  |
| 大于或等于 | `{<key>:{$gte:<value>}}` | `db.col.find({"likes":{$gte:50}}).pretty()` | `where likes >= 50` |
| 不等于   | `{<key>:{$ne:<value>}}`  | `db.col.find({"likes":{$ne:50}}).pretty()`  | `where likes != 50` |




## Logical operator邏輯操作符


| operator |    作用     | Example                                       |
| :------: | :-------: | --------------------------------------------- |
|   $and   | 與，符合所有條件  | `{$and: [{age:{$gt:25}}, {city:"New York"}]}` |
|   $or    | 或，符合任意條件  | `{$or: [{age:{$gt:25}}, {city:"New York"}]}`  |
|   $not   | 取反，不符合條件  | `{age: {$not: {$gt:25}}}`                     |
|   $nor   | 或非，均不符合條件 | `{$nor: [{age:{$gt:25}}, {city:"New York"}]}` |

<span style="background:rgba(240, 167, 216, 0.55)">AND 還可以使用, 來連接</span>


> [!example] 
> ```jsx
> db.col.find(
> 	{
> 		$or: [
> 			{key1:value1},{key2:value2}
> 		]
> 	}
> ).pretty()
> ```

> [!example]+ AND 和 OR聯合使用
> ```jsx
>db.col.find ({"likes": {$gt: 50}, $or: [{"by": "菜鸟教程"},{"title": "MongoDB 教程"}]}). pretty ()
> {
>         "_id" : ObjectId ("56063f17ade2f21f36b03133"),
>         "title" : "MongoDB 教程",
>         "description" : "MongoDB 是一个 Nosql 数据库",
>         "by" : "菜鸟教程",
>         "url" : "http://www.runoob.com",
>         "tags" : [
>                 "mongodb",
>                 "database",
>                 "NoSQL"
>         ],
>         "likes" : 100
>   }
> 
> ```
> 類似常規SQL語句： `where likes > 50 AND (by='菜鳥編程' OR title = 'MongoDB 教程')` 

> [!attention] 
> **同一個key下的條件需要在同一個{}中：**
> `db. post. find ({qty:{$gt: 50,$ lt:80}})`
> 而不是
> `db.post.find({qty:{$gt:50}, gty:{$lt:80}})`
> 同一個key下的條件需要在同一個{}中


## 元素操作符
|   操作符   |     描述      |              syntax               |                        示例                         |
| :-----: | :---------: | :-------------------------------: | :-----------------------------------------------: |
| $exists |   字段是否存在    | `{ field: { $exists: boolean } }` | `db.collection.find ({ age: { $exists: true } })` |
|  $type  | 字段的 BSON 类型 |  `{ field: { $type: "type" } }`   |  `db.collection.find({ age: { $type: "int" } })`  |


## 数组操作符
|    操作符     |      描述      |                    syntax                    |                              示例                              |
| :--------: | :----------: | :------------------------------------------: | :----------------------------------------------------------: |
|    $all    | 数组包含所有指定的元素  | `{ field: { $all: [value1, value2, ...] } }` |             { tags: { $all: ["red", "blue"] } }              |
| $elemMatch | 数组中的元素匹配指定条件 |  `{ field: { $elemMatch: { condition } } }`  | { results: { $elemMatch: { score: { $gt: 80, $lt: 85 } } } } |
|   $size    |  数组的长度等于指定值  |        `{ field: { $size: value } }`         |                    { tags: { $size: 3 } }                    |


## 其他操作符 
| 操作符        | 描述                      | syntax                                                                          | 示例                                                                                 |
| ---------- | ----------------------- | ------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------- |
| $regex     | 匹配正则表达式                 | `{ field: { $regex: "pattern" } }`                                              | { name: { $regex: /^A/ } }                                                         |
| $text      | 进行文本搜索                  |                                                                                 | { $text: { $search: "coffee" } }                                                   |
| $where     | 使用 JavaScript 表达式进行条件过滤 |                                                                                 | { $where: "this.age > 25" }                                                        |
| $near      | 查找接近指定点的文档              | `{ field: { $near: [longitude, latitude], $maxDistance: distance } }`           | db.collection.find({ location: { $near: [10, 20], $maxDistance: 1000 } })          |
| $geoWithin | 查找在指定地理区域内的文档           | `{ field: { $geoWithin: { $centerSphere: [[longitude, latitude], radius] } } }` | db.collection.find({ location: { $geoWithin: { $centerSphere: [[10, 20], 1] } } }) |




## regular expression正則表達式

**syntax：**
`{ field: { $regex: "pattern" } }`


##  投影
用於控制查詢結果中返回的字段。可以使用*包含字段*和*排除字段*兩種方式

使用 0 or 1 來排除 or 包含字段


## 排序
`.sort ({(<keyname>): 1，-1})`
`{ field1: 1, field2: -1 }`：指定要排序的字段及排序顺序
1 表示升序
-1 表示降序
先按照field1排序再按照field2排序

> [!attention] **注意事项**
> - MongoDB 在执行排序时会对查询结果进行排序，因此可能会影响性能，特别是在大型数据集上排序操作可能会较慢。
> - 如果排序字段上有索引，排序操作可能会更高效。在执行频繁的排序操作时，可以考虑创建适当的索引以提高性能。



## 限制
`.limit (<number>)`
返回前number個文檔

## 跳過
`.skip (<number>)`
跳過前面number個文檔

> [!attention] 
>  當limit和skip同事使用的時候是跳過number個文件然後返回接下來的number個文件
>
>> [!example]+ 
>> ```jsx
>> db.myCollection.find(
>>    {
>> 	  $and: [ //滿足下面所有條件
>> 		  { age:{$gt:25}},
>> 		  { city:"New York"}
>> 	  ]
>>    },
>>    { name: 1, age: 1, _id:0} //顯示限制
>> ).sort({ age: -1}).limit(10); //排序和限制
>> ```
>>  查找年齡大於25且城市為“New York”的文檔 只返回 name 和 age 並且按照年齡降序排序返回前10個文檔
> 
> - `skip()` 和 `limit()` 方法通常用于配合使用，以实现<u>分页查询</u>。但是在大型数据集上使用 `skip()` <u>可能会导致性能问题</u>，因为 MongoDB 在执行查询时需要扫描并跳过指定数量的文档，因此建议仅在需要时才使用 `skip()` 方法，尽量避免在大型数据集上连续使用。
> - `skip()`, `limit()`, `sort()` 三個放在一起執行的時候，執行順序是 `sort()`, `skip()`, `limit()`
> 
> 通过使用 `limit()` 和 `skip()` 方法，您可以实现在 MongoDB 中对查询结果进行分页处理，提高查询的灵活性和性能。


## `$type` operator

`db.collection.find ({ field: { $type: <type> } })`
- **field**：要检查类型的字段。
- **type**：指定的 BSON 类型，可以是类型的数字代码或类型名称的字符串。


> [!attention]+ ### BSON 类型
> 
以下是常见的 BSON 类型及其对应的数字代码和字符串名称：
>  
| 类型代码 | 类型名称                |
| ---- | ------------------- |
| 1    | double              |
| 2    | string              |
| 3    | object              |
| 4    | array               |
| 5    | binData             |
| 6    | undefined           |
| 7    | objectId            |
| 8    | bool                |
| 9    | date                |
| 10   | null                |
| 11   | regex               |
| 12   | dbPointer           |
| 13   | javascript          |
| 14   | symbol              |
| 15   | javascriptWithScope |
| 16   | int                 |
| 17   | timestamp           |
| 18   | long                |
| 19   | decimal             |
| 255  | minKey              |
| 127  | maxKey              |
> 
> 使用文字或者類型代碼都是可以的
>> [!example]+
>> ```jsx
>> // 查找字段類型為字符串的文檔
>> db.myCollection.find({fieldName: {$type: "string"}})
>> db.myCollection.find ({ fieldName: { $type: 2 } })
>> //查找字段類型為數字的文檔
>> db.myCollection.find ({ age: { $type: "int" } })
>> db.myCollection.find ({ age: { $type: 16 } })
>> ```
>> 
 


## `aggregate(AGGREGATE_OPERATION)` 聚合管道 Aggregation Pipelines
主要用於處理數據 (統計計算平均值，求和等)，並返回計算後的結果 類似與 `count(*)` 


**syntax:**
`db.COLLECTION_NAME.aggregate(AGGREGATE_OPERATION)`


> [!example]+ 
> ```jsx
> db.mycol.aggregate([{$group : {_id : "$by_user", num_tutorial : {$sum : 1}}}])
> ```
> 類似於sql語句： `select by_user, count (*) from mycol group by by_user`


> [!tip]+ 聚合的表達式：  
>    
|     表达式                                                                                                                                                                                                                                                                                                                |                     描述                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |                                            实例                                                  |
|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|:-----------------------------------------------------------------------------------------------|
|    `$sum`                                                                                                                                                                                                                                                                                                              |                    计算总和。                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |  ` db.mycol.aggregate([{$ group : {_id : "$by_user", num_tutorial : {$ sum : "$likes"}}}`])    |
|    `$avg`                                                                                                                                                                                                                                                                                                              |                    计算平均值                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |  ` db.mycol.aggregate([{$ group : {_id : "$by_user", num_tutorial : {$ avg : "$likes"}}}`])    |
|    `$min`                                                                                                                                                                                                                                                                                                              |              获取集合中所有文档对应值得最小值。                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |  ` db.mycol.aggregate([{$ group : {_id : "$by_user", num_tutorial : {$ min : "$likes"}}}`])    |
|    `$max`                                                                                                                                                                                                                                                                                                              |              获取集合中所有文档对应值得最大值。                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |  ` db.mycol.aggregate([{$ group : {_id : "$by_user", num_tutorial : {$ max : "$likes"}}}`])    |
|    `$push`                                                                                                                                                                                                                                                                                                             |           将值加入一个数组中，不会判断是否有重复的值。                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |       ` db.mycol.aggregate([{$ group : {_id : "$by_user", url : {$ push: "$url"}}`}])          |
|  `$addToSet`                                                                                                                                                                                                                                                                                                           |  将值加入一个数组中，会判断是否有重复的值，若相同的值在数组中已经存在了，则不加入。                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |     ` db.mycol.aggregate([{$ group : {_id : "$by_user", url : {$ addToSet : "$url"}}}]) `      |
|   `$first`                                                                                                                                                                                                                                                                                                             |             根据资源文档的排序获取第一个文档数据。                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |   ` db.mycol.aggregate([{$ group : {_id : "$by_user", first_url : {$ first : "$url"}}}]) `     |
|    `$last`                                                                                                                                                                                                                                                                                                             |             根据资源文档的排序获取最后一个文档数据                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |    ` db.mycol.aggregate([{$ group : {_id : "$by_user", last_url : {$ last : "$url"}}}]) `      |
| <font color="#ebdbb2" face="Candara, JetBrains Mono, Consolas, Monaco, 等距更纱黑体 SC, Source Han Mono, Microsoft Yahei Mono, Segoe UI Emoji, Microsoft YaHei, Source Code Pro, monospace"><span style="font-size: 16px; caret-color: rgb(210, 165, 0); background-color: rgba(17, 17, 17, 0.55);">`$project`</span></font> | <u style="font-family: WDMMCZAGJC, Bookerly, Inter, &quot;Segoe UI&quot;, &quot;霞鹜文楷 GB&quot;, &quot;LXGW WenKai&quot;, &quot;Microsoft YaHei&quot;, ui-sans-serif, -apple-system, BlinkMacSystemFont, &quot;Segoe UI&quot;, Roboto, Inter, &quot;Apple Color Emoji&quot;, &quot;Segoe UI Emoji&quot;, &quot;Segoe UI Symbol&quot;, &quot;Microsoft YaHei Light&quot;, sans-serif; font-size: 16px; caret-color: rgb(210, 165, 0); background-color: rgba(233, 151, 63, 0.1);">修改输入文档的结构</u><span style="font-family: WDMMCZAGJC, Bookerly, Inter, &quot;Segoe UI&quot;, &quot;霞鹜文楷 GB&quot;, &quot;LXGW WenKai&quot;, &quot;Microsoft YaHei&quot;, ui-sans-serif, -apple-system, BlinkMacSystemFont, &quot;Segoe UI&quot;, Roboto, Inter, &quot;Apple Color Emoji&quot;, &quot;Segoe UI Emoji&quot;, &quot;Segoe UI Symbol&quot;, &quot;Microsoft YaHei Light&quot;, sans-serif; font-size: 16px; caret-color: rgb(210, 165, 0); background-color: rgba(233, 151, 63, 0.1);">。可以用来重命名、增加或删除域，也可以用于创建计算结果以及嵌套文档</span>                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |                                                                                                |
| `$match`                                                                                                                                                                                                                                                                                                               | <u style="font-family: WDMMCZAGJC, Bookerly, Inter, &quot;Segoe UI&quot;, &quot;霞鹜文楷 GB&quot;, &quot;LXGW WenKai&quot;, &quot;Microsoft YaHei&quot;, ui-sans-serif, -apple-system, BlinkMacSystemFont, &quot;Segoe UI&quot;, Roboto, Inter, &quot;Apple Color Emoji&quot;, &quot;Segoe UI Emoji&quot;, &quot;Segoe UI Symbol&quot;, &quot;Microsoft YaHei Light&quot;, sans-serif; font-size: 16px; caret-color: rgb(210, 165, 0); background-color: rgba(233, 151, 63, 0.1);">用于过滤数据</u><span style="font-family: WDMMCZAGJC, Bookerly, Inter, &quot;Segoe UI&quot;, &quot;霞鹜文楷 GB&quot;, &quot;LXGW WenKai&quot;, &quot;Microsoft YaHei&quot;, ui-sans-serif, -apple-system, BlinkMacSystemFont, &quot;Segoe UI&quot;, Roboto, Inter, &quot;Apple Color Emoji&quot;, &quot;Segoe UI Emoji&quot;, &quot;Segoe UI Symbol&quot;, &quot;Microsoft YaHei Light&quot;, sans-serif; font-size: 16px; caret-color: rgb(210, 165, 0); background-color: rgba(233, 151, 63, 0.1);">，只输出符合条件的文档。$match使用MongoDB的标准查询操作。</span>                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |                                                                                                |
| `$limit`                                                                                                                                                                                                                                                                                                               | <span style="font-family: WDMMCZAGJC, Bookerly, Inter, &quot;Segoe UI&quot;, &quot;霞鹜文楷 GB&quot;, &quot;LXGW WenKai&quot;, &quot;Microsoft YaHei&quot;, ui-sans-serif, -apple-system, BlinkMacSystemFont, &quot;Segoe UI&quot;, Roboto, Inter, &quot;Apple Color Emoji&quot;, &quot;Segoe UI Emoji&quot;, &quot;Segoe UI Symbol&quot;, &quot;Microsoft YaHei Light&quot;, sans-serif; font-size: 16px; caret-color: rgb(210, 165, 0); background-color: rgba(233, 151, 63, 0.1);">用来限制MongoDB聚合管道</span><span style="font-style: var(--font-style-em); color: var(--accent-em); font-family: WDMMCZAGJC, Bookerly, Inter, &quot;Segoe UI&quot;, &quot;霞鹜文楷 GB&quot;, &quot;LXGW WenKai&quot;, &quot;Microsoft YaHei&quot;, ui-sans-serif, -apple-system, BlinkMacSystemFont, &quot;Segoe UI&quot;, Roboto, Inter, &quot;Apple Color Emoji&quot;, &quot;Segoe UI Emoji&quot;, &quot;Segoe UI Symbol&quot;, &quot;Microsoft YaHei Light&quot;, sans-serif; font-size: 16px; caret-color: rgb(210, 165, 0); background-color: rgba(233, 151, 63, 0.1);">返回的文档数</span>                                                                                                                                                                                                                                                                                                                                                                                                                                            |                                                                                                |
| `$skip`                                                                                                                                                                                                                                                                                                                | <span style="font-family: WDMMCZAGJC, Bookerly, Inter, &quot;Segoe UI&quot;, &quot;霞鹜文楷 GB&quot;, &quot;LXGW WenKai&quot;, &quot;Microsoft YaHei&quot;, ui-sans-serif, -apple-system, BlinkMacSystemFont, &quot;Segoe UI&quot;, Roboto, Inter, &quot;Apple Color Emoji&quot;, &quot;Segoe UI Emoji&quot;, &quot;Segoe UI Symbol&quot;, &quot;Microsoft YaHei Light&quot;, sans-serif; font-size: 16px; caret-color: rgb(210, 165, 0); background-color: rgba(233, 151, 63, 0.1);">在聚合管道中跳过指定数量的文档，并返回余下的文档。</span>                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |                                                                                                |
| `$unwind`                                                                                                                                                                                                                                                                                                              | <font color="#ffc000" style="font-family: WDMMCZAGJC, Bookerly, Inter, &quot;Segoe UI&quot;, &quot;霞鹜文楷 GB&quot;, &quot;LXGW WenKai&quot;, &quot;Microsoft YaHei&quot;, ui-sans-serif, -apple-system, BlinkMacSystemFont, &quot;Segoe UI&quot;, Roboto, Inter, &quot;Apple Color Emoji&quot;, &quot;Segoe UI Emoji&quot;, &quot;Segoe UI Symbol&quot;, &quot;Microsoft YaHei Light&quot;, sans-serif; font-size: 16px; caret-color: rgb(210, 165, 0); background-color: rgba(233, 151, 63, 0.1);">将文档中的某一个数组类型字段拆分成多条</font><span style="font-family: WDMMCZAGJC, Bookerly, Inter, &quot;Segoe UI&quot;, &quot;霞鹜文楷 GB&quot;, &quot;LXGW WenKai&quot;, &quot;Microsoft YaHei&quot;, ui-sans-serif, -apple-system, BlinkMacSystemFont, &quot;Segoe UI&quot;, Roboto, Inter, &quot;Apple Color Emoji&quot;, &quot;Segoe UI Emoji&quot;, &quot;Segoe UI Symbol&quot;, &quot;Microsoft YaHei Light&quot;, sans-serif; font-size: 16px; caret-color: rgb(210, 165, 0); background-color: rgba(233, 151, 63, 0.1);">，每条包含数组中的一个值。</span>                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |                                                                                                |
| `$group`                                                                                                                                                                                                                                                                                                               | <span style="font-family: WDMMCZAGJC, Bookerly, Inter, &quot;Segoe UI&quot;, &quot;霞鹜文楷 GB&quot;, &quot;LXGW WenKai&quot;, &quot;Microsoft YaHei&quot;, ui-sans-serif, -apple-system, BlinkMacSystemFont, &quot;Segoe UI&quot;, Roboto, Inter, &quot;Apple Color Emoji&quot;, &quot;Segoe UI Emoji&quot;, &quot;Segoe UI Symbol&quot;, &quot;Microsoft YaHei Light&quot;, sans-serif; font-size: 16px; caret-color: rgb(210, 165, 0); background-color: rgba(233, 151, 63, 0.1);">将集合中的文档</span><font color="#ffc000" style="font-family: WDMMCZAGJC, Bookerly, Inter, &quot;Segoe UI&quot;, &quot;霞鹜文楷 GB&quot;, &quot;LXGW WenKai&quot;, &quot;Microsoft YaHei&quot;, ui-sans-serif, -apple-system, BlinkMacSystemFont, &quot;Segoe UI&quot;, Roboto, Inter, &quot;Apple Color Emoji&quot;, &quot;Segoe UI Emoji&quot;, &quot;Segoe UI Symbol&quot;, &quot;Microsoft YaHei Light&quot;, sans-serif; font-size: 16px; caret-color: rgb(210, 165, 0); background-color: rgba(233, 151, 63, 0.1);">分组</font><span style="font-family: WDMMCZAGJC, Bookerly, Inter, &quot;Segoe UI&quot;, &quot;霞鹜文楷 GB&quot;, &quot;LXGW WenKai&quot;, &quot;Microsoft YaHei&quot;, ui-sans-serif, -apple-system, BlinkMacSystemFont, &quot;Segoe UI&quot;, Roboto, Inter, &quot;Apple Color Emoji&quot;, &quot;Segoe UI Emoji&quot;, &quot;Segoe UI Symbol&quot;, &quot;Microsoft YaHei Light&quot;, sans-serif; font-size: 16px; caret-color: rgb(210, 165, 0); background-color: rgba(233, 151, 63, 0.1);">，可用于统计结果。</span> |                                                                                                |
| `$sort`                                                                                                                                                                                                                                                                                                                | <span style="font-family: WDMMCZAGJC, Bookerly, Inter, &quot;Segoe UI&quot;, &quot;霞鹜文楷 GB&quot;, &quot;LXGW WenKai&quot;, &quot;Microsoft YaHei&quot;, ui-sans-serif, -apple-system, BlinkMacSystemFont, &quot;Segoe UI&quot;, Roboto, Inter, &quot;Apple Color Emoji&quot;, &quot;Segoe UI Emoji&quot;, &quot;Segoe UI Symbol&quot;, &quot;Microsoft YaHei Light&quot;, sans-serif; font-size: 16px; caret-color: rgb(210, 165, 0); background-color: rgba(233, 151, 63, 0.1);">将输入文档排序后输出。</span>                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |                                                                                                |
| `$geoNear`                                                                                                                                                                                                                                                                                                             | <span style="font-family: WDMMCZAGJC, Bookerly, Inter, &quot;Segoe UI&quot;, &quot;霞鹜文楷 GB&quot;, &quot;LXGW WenKai&quot;, &quot;Microsoft YaHei&quot;, ui-sans-serif, -apple-system, BlinkMacSystemFont, &quot;Segoe UI&quot;, Roboto, Inter, &quot;Apple Color Emoji&quot;, &quot;Segoe UI Emoji&quot;, &quot;Segoe UI Symbol&quot;, &quot;Microsoft YaHei Light&quot;, sans-serif; font-size: 16px; caret-color: rgb(210, 165, 0); background-color: rgba(233, 151, 63, 0.1);">输出接近某一地理位置的有序文档。</span>                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |                                                                                                |  


> [!attention]+ ## 管道概念：
MongoDB的聚合管道将MongoDB文档在一个管道处理完毕后将结果传递给下一个管道处理。管道操作是可以重复的。
> 
表达式：处理输入文档并输出。表达式是无状态的，只能用于计算当前聚合管道的文档，不能处理其它的文档
> 
> 聚合框架中常用的幾個操作：
> - `$project`：<u>修改输入文档的结构</u>。可以用来重命名、增加或删除域，也可以用于创建计算结果以及嵌套文档。
> - `$match`：<u>用于过滤数据</u>，只输出符合条件的文档。$match使用MongoDB的标准查询操作。
> - `$limit`：用来限制MongoDB聚合管道*返回的文档数*。
> - `$skip`：在聚合管道中跳过指定数量的文档，并返回余下的文档。
> - `$unwind`：<font color="#ffc000">将文档中的某一个数组类型字段拆分成多条</font>，每条包含数组中的一个值。
> - `$group`：将集合中的文档<font color="#ffc000">分组</font>，可用于统计结果。
> - `$sort`：将输入文档排序后输出。
> - `$geoNear`：输出接近某一地理位置的有序文档。
> 
>> [!example]+
>> ```jsx
>> db.articles.aggregate( [
>>                         { $match : { score : { $gt : 70, $lte : 90 } } },
>>                         { $group: { _id: null, count: { $sum: 1 } } }
>>                        ] );
>> ```
>> 
>>  `$match` 用于获取分数大于70小于或等于90记录，然后将符合条件的记录送到下一阶段$group管道操作符进行处理



## 覆盖索引查询

- 所有的查询字段是索引的一部分
- 所有的查询返回字段在同一个索引中

由于所有出现在查询中的字段是索引的一部分， MongoDB 无需在整个数据文档中检索匹配查询条件和返回使用相同索引的查询结果。

<font color="#ffc000">因为索引存在于RAM中，从索引中获取数据比通过扫描文档读取数据要快得多</font>


user集合：
```jsx
{
   "_id": ObjectId("53402597d852426020000002"),
   "contact": "987654321",
   "dob": "01-01-1991",
   "gender": "M",
   "name": "Tom Benzamin",
   "user_name": "tombenzamin"
}
```
在 users 集合中创建联合索引，字段为 gender 和 user_name :

```jsx
> db.users.createIndex({gender:1,user_name:1})
```

现在，该索引会覆盖以下查询：

```jsx
> db.users.find({gender:"M"},{user_name:1,_id:0})
```
于上述查询，MongoDB的不会去数据库文件中查找。相反，它会从索引中提取数据，这是非常快速的数据查询。

如果沒有排除索引就不會被覆蓋 因為我們設置的時候覆蓋的只有gender和user_name兩個字段
> [!error] 查詢不被覆蓋：
> ```jsx
> db.users.find ({gender: "M"},{user_name: 1})
> ```
> 
> 



**如果是以下的查询，不能使用覆盖索引查询：**

- 所有索引字段是一个数组
- 所有索引字段是一个子文档


## 查詢分析
https://www.runoob.com/mongodb/mongodb-analyzing-queries.html




## 原子操作
https://www.runoob.com/mongodb/mongodb-atomic-operations.html



## 高級索引

https://www.runoob.com/mongodb/mongodb-advanced-indexing.html


索引不能被以下的查询使用：
- 正则表达式及非操作符，如 $nin, $not, 等。
- 算术运算符，如 $mod, 等。
- $where 子句
检测你的语句是否使用索引，可以用explain来查看



## Map Reduce 聚合查詢
syntax：
```jsx
>db.collection.mapReduce(
   function() {emit(key,value);},  //map 函数
   function(key,values) {return reduceFunction},   //reduce 函数
   {
      out: collection,
      query: document,
      sort: document,
      limit: number
   }
)
```
使用 MapReduce 要实现两个函数 Map 函数和 Reduce 函数,Map 函数调用 emit(key, value), 遍历 collection 中所有的记录, 将 key 与 value 传递给 Reduce 函数进行处理。
Map 函数必须调用 `emit(key, value)` 返回键值对。

**参数说明:**
- **map** ：映射函数 (生成键值对序列,作为 reduce 函数参数)。
- **reduce** 统计函数，reduce函数的任务就是将key-values变成key-value，也就是把values数组变成一个单一的值value。。
- **out** 统计结果存放集合 (不指定则使用临时集合,在客户端断开后自动删除)。
- **query** 一个筛选条件，只有满足条件的文档才会调用map函数。（query。limit，sort可以随意组合）
- **sort** 和limit结合的sort排序参数（也是在发往map函数前给文档排序），可以优化分组机制
- **limit** 发往map函数的文档数量的上限（要是没有limit，单独使用sort的用处不大）


> [!example]+ 查詢的數據庫：
> 
> ```jsx
> >db.posts.insert ({
   "post_text": "菜鸟教程，最全的技术文档。",
   "user_name": "mark",
   "status": "active"
})
WriteResult ({ "nInserted" : 1 })
>db.posts.insert ({
   "post_text": "菜鸟教程，最全的技术文档。",
   "user_name": "mark",
   "status": "active"
})
WriteResult ({ "nInserted" : 1 })
>db.posts.insert ({
   "post_text": "菜鸟教程，最全的技术文档。",
   "user_name": "mark",
   "status": "active"
})
WriteResult ({ "nInserted" : 1 })
>db.posts.insert ({
   "post_text": "菜鸟教程，最全的技术文档。",
   "user_name": "mark",
   "status": "active"
})
WriteResult ({ "nInserted" : 1 })
>db.posts.insert ({
   "post_text": "菜鸟教程，最全的技术文档。",
   "user_name": "mark",
   "status": "disabled"
})
WriteResult ({ "nInserted" : 1 })
>db.posts.insert ({
   "post_text": "菜鸟教程，最全的技术文档。",
   "user_name": "runoob",
   "status": "disabled"
})
WriteResult ({ "nInserted" : 1 })
>db.posts.insert ({
   "post_text": "菜鸟教程，最全的技术文档。",
   "user_name": "runoob",
   "status": "disabled"
})
WriteResult ({ "nInserted" : 1 })
>db.posts.insert ({
   "post_text": "菜鸟教程，最全的技术文档。",
   "user_name": "runoob",
   "status": "active"
})
WriteResult ({ "nInserted" : 1 })
> 
> ```

使用mapReduce()將posts集合中的status為active的item通過user_name 分組，計算每個用戶的文檔數：

```jsx
>db.posts.mapReduce( 
   function() { emit(this.user_name,1); }, //用來分組的字段
   function(key, values) {return Array.sum(values)}, 
      {  
         query:{status:"active"},  //篩選item的條件
         out:"post_total" 
      }
)
```
> [!done] Output
> ```jsx
> {
>         "result" : "post_total",
>         "timeMillis" : 23,
>         "counts" : {
>                 "input" : 5,
>                 "emit" : 5,
>                 "reduce" : 1,
>                 "output" : 2
>         },
>         "ok" : 1
> }
> ```
> 
有五個item是active狀態的，其中分成了2組

**結果參數：**
- result：储存结果的collection的名字,这是个临时集合，MapReduce的连接关闭后自动就被删除了。
- timeMillis：执行花费的时间，毫秒为单位
- input：满足条件被发送到map函数的文档个数
- emit：在map函数中emit被调用的次数，也就是所有集合中的数据总量
- output：结果集合中的文档个数 **（count对调试非常有帮助）**
- ok：是否成功，成功为1
- err：如果失败，这里可以有失败原因，不过从经验上来看，原因比较模糊，作用不大


```jsx
> var map=function() { emit(this.user_name,1); }
> var reduce=function(key, values) {return Array.sum(values)}
> var options={query:{status:"active"},out:"post_total"}
> db.posts.mapReduce(map,reduce,options)
{ "result" : "post_total", "ok" : 1 }
> db.post_total.find();
```
> [!done] Output
> ```jsx
> { "_id" : "mark", "value" : 4 }
{ "_id" : "runoob", "value" : 1 }
> ```


#### 不希望創建集合可以使用參數 `output:{inline: 1}`
整个 **Map/Reduce** 的操作将会在内存中进行。
注意，这个选项只有在结果集单个文档大小在16MB限制范围内时才有效。
```jsx
 db.users.mapReduce(map,reduce,{out:{inline:1}});
```





## 全文檢索
https://www.runoob.com/mongodb/mongodb-text-search.html
全文检索对每一个词建立一个索引，<font color="#ffc000">指明该词在文章中出现的次数和位置</font>，当用户查询时，检索程序就根据事先建立的索引进行查找，并将查找的结果反馈给用户的检索方式。

这个过程类似于通过字典中的检索字表查字的过程。

目前支持15種語言的全文索引

```jsx
> db.adminCommand({setParameter:true,textSearchEnabled:true})
```
or
```bath
mongod --setParameter textSearchEnabled=true
```



## 正則表達式
使用正则表达式不需要做任何配置

```jsx
db.CollectionName.find({field:{$regex:""，$option:""}})
```
regex operator:
- `{<field>:{$regex:/pattern/，$options:’<options>’}}`
- `{<field>:{$regex:’pattern’，$options:’<options>’}}`
- `{<field>:{$regex:/pattern/<options>}}`

正则表达式对象:
- `{<field>: /pattern/<options>}`

$regex与正则表达式对象的区别:

- 在 ` $in` 操作符中只能使用正则表达式对象，例如: `{name:{$ in:[/^joe/i,/^jack/}}`
- 在使用隐式的 `$and` 操作符中，只能使用 `$regex`，例如: `{name:{$ regex:/^jo/i, $nin:['john']}}`
- 当option选项中包含X或S选项时，只能使用 `$regex`，例如: `{name:{$regex:/m.*line/,$ options: "si"}}`

**$regex操作符的使用**

$regex操作符中的option选项可以改变正则匹配的默认行为，它包括i, m, x以及S四个选项，其含义如下

- `i` 忽略大小写，`{<field>{$regex/pattern/i}}`，设置i选项后，模式中的字母会进行大小写不敏感匹配。
- `m` 多行匹配模式，`{<field>{$regex/pattern/,$options: 'm'}`，`m` 选项会更改 `^` 和$元字符的默认行为，分别使用与行的开头和结尾匹配，而不是与输入字符串的开头和结尾匹配。
- x 忽略非转义的空白字符，{<field>:{$regex:/pattern/,$options:'m'}，设置x选项后，正则表达式中的非转义的空白字符将被忽略，同时井号(#)被解释为注释的开头注，只能显式位于option选项中。
- s 单行匹配模式{<field>:{$regex:/pattern/,$options:'s'}，设置s选项后，会改变模式中的点号(.)元字符的默认行为，它会匹配所有字符，包括换行符(\n)，只能显式位于option选项中。

使用$regex操作符时，需要注意下面几个问题:

- i，m，x，s可以组合使用，例如:{name:{$regex:/j*k/,$options:"si"}}
- 在设置索弓}的字段上进行正则匹配可以提高查询速度，而且当正则表达式使用的是前缀表达式时，查询速度会进一步提高，例如:{name:{$regex: /^joe/}
















