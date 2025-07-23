---
LINK:
  - "[[Database]]"
  - "[[NoSQL]]"
  - "[[MongoDB]]"
tags:
---



`

<iframe width=80% height=500px src="https://docs.mongoing.com/mongo-introduction">MongoBD 官方文檔
</iframe>
[MongoDB 官方文檔](https://docs.mongoing.com/mongo-introduction)



| Function                                                                                                                          |   作用   |
| :-------------------------------------------------------------------------------------------------------------------------------- | :----: |
| [[Computer Science/Database/NoSQL/MongoDB/MongoDB Operation#`createCollection()` 創建集合\|createCollection()]]<br>                   |  創建集合  |
| [[Computer Science/Database/NoSQL/MongoDB/MongoDB Operation#`show collections` / `show tables`\|show collections/show tables]]    | 查看已有集合 |
| [[Computer Science/Database/NoSQL/MongoDB/MongoDB Operation#`adminCommand ()` 更改集合名\| adminCommand({renameCollection:"",to:""})]] | 更新集合名稱 |
| [[Computer Science/Database/NoSQL/MongoDB/MongoDB Operation#`drop` 刪除集合\| drop()]]                                                |  刪除集合  |




### `createCollection()`  創建集合

syntax:
`db.createCollection(name,options)`

> [!note]+ - options: 可選參數，指定有關內存大小及索引的選項  
|  參數名                  |  類型   |  描述                                                                                                                                |  實例值                          |
|:----------------------|:------|:-----------------------------------------------------------------------------------------------------------------------------------|:------------------------------|
|  `capped`             |  佈爾值  |  是否創建一個固定大小的集合                                                                                                                     |  true                         |
|  `size `              |  數值   |  集合的最大大小 (以字節為單位)。<font color="#ffc000">僅在capped為true時有效</font>                                                                    |  10485760 (10MB)              |
|  `max `               |  數值   |  集合中允許的最大文檔數。僅在capped為true時有效                                                                                                      |   5000                        |
|  `validator`          |  對象   |  用於文檔驗證的表達式                                                                                                                        |  {$jsonSchema:{...}}          |
|  `validationLevel`    |  字符串  |  指定文檔驗證的嚴格程度。<br>“`off`”：不進行驗證<br>“`strict`”：插入和更新操作都必須通過驗證 (默認)<br>"`moderate`": 僅現有文檔更新時必須通過驗證，插入新文檔時不需要                         |  "strict"                     |
|  `validationAction`   |  字符串  |  指定文檔驗證失敗時的操作。<br>“`error`”：阻止插入或更新 (默認)。<br>"`warn`"：允許插入或更新，但會發出警告                                                               |  "error"                      |
|  `storageEngine`      |  對象   |  為集合指定存儲引擎配置                                                                                                                       |  {wiredTiger:{....}}          |
|  `collation`          |  對象   |  指定集合的默認排序規則                                                                                                                       |  {locale: "en", strength: 2}  |     
>
 

在插入文檔時，MongoDB首先檢查固定集合的size字段，然後檢查max字段

> [!example]+  實例:
> 
>> [!note]+ 使用這些創建一個集合的實例:
>>  ``` jsx
>>  db.createCollection ("myComplexCollection", {
>>   capped: true,
>>  size: 10485760,
>>  max: 5000,
>> validator: { $jsonSchema: {
>>    bsonType: "object",
>>    required: ["name", "email"],
>>    properties: {
>>     name: {
>>        bsonType: "string",
>>        description: "必须为字符串且为必填项"
>>      },
>>      email: {
>>        bsonType: "string",
>>        pattern: "^.+@.+$",
>>       description: "必须为有效的电子邮件地址"
>>     }
>>   }
>>  }},
>>  validationLevel: "strict",
>> validationAction: "error",
>>  storageEngine: {
>>    wiredTiger: { configString: "block_compressor=zstd" }
>>  },
>>  collation: { locale: "en", strength: 2 }
>>  });
>>  ```
>>  
>> 這個例子創建一個集合，具有一下特性：
>>  - 固定大小，最大10MB，最多存儲5000個文檔
>>  - 文檔必須包含name和email字段，其中name必須是字符串，email必須是有效的電子郵件格式
>>  - 驗證級為嚴格，驗證失敗將阻止插入或更新
>>  - 使用WiredTiger存儲引擎，指定塊壓縮器為zstd
>>  - 默認使用英語排序規則
> 
>> [!note]+ 實例2：
>>  
>>  在test數據庫中創建runoob集合：
>>  ```jsx
>>  # switched to db test
>>  use test
>>  db.createCollection("runoob")
>>  ```
>>> [!done] Output
>>>   ```
>>>   {"ok": 1}
>>>   ```
> 
>> [!note]+ 實力3： 創建一個驗證器，要求文檔中必須有name和age字段，且name是字符串，age必須是非負數
>> ```jsx
>> db.createCollection ("myCollection", {
>>  validator: { $jsonSchema: {
>>      bsonType: "object",
>>     required: ["name", "age"],
>>     properties: {
>>       name: {
>>         bsonType: "string",
>>         description: "必须为字符串且为必填项"
>>       },
>>       age: {
>>         bsonType: "int",
>>         minimum: 0,
>>         description: "必须为整数且为必填项"
>>       }
>>     }
>>   }}
>>  });
>> ```
> 
> 



### `show collections` / `show tables`
查看已有集合

```jsx
show collections
```
> [!done] output 
> ```
> runoob
> ```



### `insert ()`  插入文档
有時候，可以不創建集合，當插入一些文檔時，MongoDB會自動創建集合

```jsx
db.mycol2.insert({"name":"insertitem"})
show collections
```
> [!done] output
> ```
> mycol2
> ```


#### `insertOne (document，options)`  
可以在insert过程中建立集合
parameter：
- document：要插入的單個文檔
- options：一個可選參數對象，可包含writeConcern 和bypassDocumentValidation 等
> [!example]+ 
> ```jsx
> db.posts.insertOne({
>   title: "Post Title 1",
>   body: "Body of post.",
>   category: "News",
>   likes: 1,
>   tags: ["news", "events"],
>   date: Date()
> })
> ```
>> [!done] Output
>> ```
>> {
>> 	"acknowledge": true, 
>> 	"insertedId": ObjectId("60c72b2f9b1d8b5a5f8e2b2d")
>> }
>> ```


> **Note:** If you try to insert documents into a collection that does not exist, MongoDB will <font color="#ffc000">create</font> the collection automatically.


#### `insertMany(documents, options)`
To insert multiple documents at once, use the `insertMany()` method
parameter:
- documents: 要插入的文檔數組
- options：一個可選參數對象，可以包含ordered，writeConcern和bypassDocumentValidation等

> [!example]+ 
> ```jsx
> db.posts.insertMany([  
 >  {
>     title: "Post Title 2",
>     body: "Body of post.",
>     category: "Event",
>     likes: 2,
>     tags: ["news", "events"],
>     date: Date()
>   },
>   {
>     title: "Post Title 3",
>     body: "Body of post.",
>     category: "Technology",
>     likes: 3,
>     tags: ["news", "events"],
>     date: Date()
>   },
>   {
>     title: "Post Title 4",
>     body: "Body of post.",
>     category: "Event",
>     likes: 4,
>     tags: ["news", "events"],
>     date: Date()
>   }
> ])
> ```



### `save(document, options)` 
類似於`insertOne ()`  如果文檔存在，則該文檔會被更新，如果文檔不存在，則會插入一個新的文檔

如果文档包含 \_id 字段且已存在，则该文档会被更新；如果文档不包含 \_id 字段或 \_id 不存在，则会插入一个新文档

parameter:
- document：要保存的文档。
- options（可选）：一个可选参数对象，可以包含 writeConcern 等。
	- ordered（<font color="#ffc000">仅适用于 insertMany</font>）：布尔值。如果为 true，则按顺序插入文档，<font color="#ffc000">在遇到错误时停止</font>；如果为 false，则尝试插入所有文档，即使遇到错误也继续。默认值为 true。
	- writeConcern：指定写操作的确认级别。
	- bypassDocumentValidation：布尔值。如果为 true，则忽略集合的文档验证规则。



> [!example] 
> ```jsx
> db.myCollection.save({
>     _id: ObjectId("60c72b2f9b1d8b5a5f8e2b2d"),
>     name: "David",
>     age: 40,
>     city: "San Francisco"
> });
> ```


save 同樣也可以用於更新文檔數據

> [!example]+ 
> ```jsx
> // 替換_id 為56064f89ade2f21f36b03136的文檔數據：
>db.col.save({
>     "_id" : ObjectId("56064f89ade2f21f36b03136"),
>     "title" : "MongoDB",
>     "description" : "MongoDB 是一个 Nosql 数据库",
>     "by" : "Runoob",
>     "url" : "http://www.runoob.com",
>     "tags" : [
>             "mongodb",
>             "NoSQL"
>     ],
>     "likes" : 110
> })
> // check 替換後的數據：
> db.col.find().pretty()
> ```
>
>> [!done]+ Output
>> ```
>> {
>>         "_id" : ObjectId("56064f89ade2f21f36b03136"),
>>         "title" : "MongoDB",
>>         "description" : "MongoDB 是一个 Nosql 数据库",
>>         "by" : "Runoob",
>>         "url" : "http://www.runoob.com",
>>         "tags" : [
>>                 "mongodb",
>>                 "NoSQL"
>>         ],
>>         "likes" : 110
>> }
>> ```
> 



### `adminCommand ()` 更改集合名
在 MongoDB 中，不能直接通过命令来重命名集合，可以使用 `renameCollection` 方法来来重命名集合。

在 MongoDB 的 admin 数据库中运行 `renameCollection` 方法，可以将一个集合重命名为另一个名称。
`renameCollection` 命令的语法：
```jsx
db.adminCommand({
  renameCollection: "sourceDb.sourceCollection",
  to: "targetDb.targetCollection",
  dropTarget: <boolean>
})
```
parameter:
- `renameCollection`：要重命名的集合的完全限定名称（包括数据库名）。
- `to`：目标集合的完全限定名称（包括数据库名）。
- `dropTarget`（可选）：布尔值。如果目标集合已经存在，是否删除目标集合。默认值为 ` false `。


可以將集合重命名到另一個數據庫：
```jsx
db.adminCommand({ 
  renameCollection: "test.oldCollection", 
  to: "production.newCollection" 
});
```
> [!attention] 注意事項：
> 
> - 權限要求： 執行renameCollection命令需要具有對源數據庫和目標數據庫的適當權限，通常需要 dbAdmin或dbOwner角色
> - 目標集合不存在：目標集合不能已經存在，如果目標集合存在，則會返回錯誤
> - 索引和數據：重命名集合會保留所有文檔和索引




#### 處理重命名失敗的情況
如果重命名過程中發生錯誤，你可以根據錯誤消息採取相應的措施。



### `find(, (projection))` 查找數據 (Query)
尋找和選擇資料

`projection` 參數 是一個 `object` 描述結果包含哪些欄位
>  **Note:** This parameter is optional. If omitted, all fields will be included in the results. 若不指定projection則默認返回所有鍵

> [!attention] 
使用0和1來表示排除和包含
0：排除
1：包含
>> **Note:** You cannot use both 0 and 1 in the same object. The only exception is the `_id` field. You should either specify the fields you would like to include or the fields you would like to exclude.
> 
> 兩種模式： 不可以混用 只有_id不一樣因為它默認返回
> 
> ```jsx
> db.collection.find(query,{title:1,by:1}) // inclusion 模式，指定返回的鍵，不返回其他鍵
> db.collection.find(query, {title:0, by:0}) //exclusion模式，指定不返回的鍵，返回其他鍵
> 
> ```
> 



> [!example] 
> ```jsx
> db.posts.find({}, {title: 1, date: 1})
> ```
>> [!done]+ Output
>>  ```
>>  [
>>    {
>>     _id: ObjectId("62c350dc07d768a33fdfe9b0"),
>>     title: 'Post Title 1',
>>     date: 'Mon Jul 04 2022 15:43:08 GMT-0500 (Central Daylight Time)'
>>   },
>>   {
>>     _id: ObjectId("62c3513907d768a33fdfe9b1"),
>>     title: 'Post Title 2',
>>     date: 'Mon Jul 04 2022 15:44:41 GMT-0500 (Central Daylight Time)'
>>   },
>>   {
>>     _id: ObjectId("62c3513907d768a33fdfe9b2"),
>>     title: 'Post Title 3',
>>     date: 'Mon Jul 04 2022 15:44:41 GMT-0500 (Central Daylight Time)'
>>   },
>>   {
>>     _id: ObjectId("62c3513907d768a33fdfe9b3"),
>>     title: 'Post Title 4',
>>      date: 'Mon Jul 04 2022 15:44:41 GMT-0500 (Central Daylight Time)'
>>    }
>> ]
>> Atlas atlas-8iy36m-shard-0 [primary] blog>
>>  ```
>>  
> 
> 
>>  Notice that the `_id` field is also included. This field is always included unless specifically excluded.
> 
>>  We use a `1` to include a field and `0` to exclude a field.
> ```jsx
> db.posts.find({}, {_id: 0, title: 1, date: 1})
> ```
>> [!done]+ Output
>> ```
>> [
>>   {
>>     title: 'Post Title 1',
>>     date: 'Mon Jul 04 2022 15:43:08 GMT-0500 (Central Daylight Time)'
>>   },
>>   {
>>     title: 'Post Title 2',
>>     date: 'Mon Jul 04 2022 15:44:41 GMT-0500 (Central Daylight Time)'
>>   },
>>   {
>>     title: 'Post Title 3',
>>     date: 'Mon Jul 04 2022 15:44:41 GMT-0500 (Central Daylight Time)'
>>   },
>>   {
>>     title: 'Post Title 4',
>>     date: 'Mon Jul 04 2022 15:44:41 GMT-0500 (Central Daylight Time)'
>>   }
>> ]
>> Atlas atlas-8iy36m-shard-0 [primary] blog>
>> ```
> 
> We will get an error if we try to specify both 0 and 1 in the same object
>> [!failure] Example
>> ```jsx
>> db. posts. find ({},{title: 1, date:0})
>> ```



#### `findOne (query, projection)`
只選擇一個文檔

This method accepts a query object. If left empty, it will return the first document it finds.

> **Note:** This method only returns the first match it finds.

**Parameter：**
- **query**：用于查找文档的查询条件。默认为 `{}`，即匹配所有文档。
- **projection**（可选）：指定返回结果中包含或排除的字段。



### `drop` 刪除集合
`drop()` 方法可以永久地从数据库中删除指定的集合及其所有文档，这是一个不可逆的操作，因此需要谨慎使用。


```jsx
db.collection.drop()
```

**返回值**
如果成功删除选定集合，则 `drop()` 方法返回 `true`，否则返回 `false`。


#### `deleteOne(filter, options)` 刪除匹配過濾器的單個文檔

syntax：
```jsx
db.collection.deleteOne(filter, options)
```
**parameters:**
- **filter**：用于查找要删除的文档的查询条件。
- **options**（可选）：一个可选参数对象



#### `deleteMany(filter, options)` 刪除所有匹配過濾器的文檔
**Parameters：**
- **filter**：用于查找要删除的文档的查询条件。
- **options**（可选）：一个可选参数对象。

`deleteOne()` 和 `deleteMany()` 的區別在於 一個是對應的全部都刪掉一個只刪掉查到的第一個

#### `findOneAndDelete(filter, options)` 查找並刪除單個文檔，可以選擇返回刪除的文檔

**Parameters：**
- **filter**：用于查找要删除的文档的查询条件。
- **options**：可选参数对象，如 `projection`、`sort` 等。
	- **writeConcern**：指定写操作的确认级别。
	- **collation**：指定比较字符串时使用的排序规则。
	- **projection**（仅适用于 `findOneAndDelete`）：指定返回的字段。
	- **sort**（仅适用于 `findOneAndDelete`）：指定排序顺序以确定要删除的文档


```jsx
db.myCollection.findOneAndDelete(
    { name: "Charlie" },
    { projection: { name: 1, age: 1 } }
);
```
`findOneAndDelete` 返回被删除的文档，如果找不到匹配的文档，则返回 null。







### update 方法

> [!example]+ 
> ## 更多实例
> 
> 只更新第一条记录：
> ``` 
db.col.update( { "count" : { $gt : 1 } } , { $set : { "test2" : "OK"} } );
> ```
> 
全部更新：
> ```
db.col.update( { "count" : { $gt : 3 } } , { $set : { "test2" : "OK"} } , false,true );
> ```
> 
只添加第一条：
> ```
db.col.update( { "count" : { $gt : 4 } } , { $set : { "test5" : "OK"} } , true , false );
> ```
> 
全部添加进去:
> ```
db.col.update( { "count" : { $gt : 5 } } , { $set : { "test5" : "OK"} } , true , true );
> ```
> 
全部更新：
> ```
db.col.update( { "count" : { $gt : 15 } } , { $inc : { "count" : 1} } , false , true );
> ``` 
只更新第一条记录：
> ```
db.col.update( { "count" : { $gt : 10 } } , { $inc : { "count" : 1} } , false , false );
> ```



> [!attention] Update Operators
> 
| operator                                                                                                                                                                                                         | 功能                                                                                                                                                                                                                                                                                                                               |
|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|
| <span style="color: rgb(255, 153, 153); font-family: Consolas, Menlo, &quot;courier new&quot;, monospace; font-size: 15.75px; text-align: left; background-color: rgba(222, 222, 222, 0.1);">$currentDate</span> | <span style="color: rgb(221, 221, 221); font-family: Verdana, sans-serif; text-align: left; background-color: rgb(29, 42, 53);">Sets the field value to the current date</span><span style="color: rgb(221, 221, 221); font-family: Verdana, sans-serif; text-align: left; background-color: rgb(29, 42, 53);">將欄位值設為目前日期</span> |
| <span style="color: rgb(255, 153, 153); font-family: Consolas, Menlo, &quot;courier new&quot;, monospace; font-size: 15.75px; text-align: left; background-color: rgba(222, 222, 222, 0.1);">$inc</span>         | <span style="color: rgb(221, 221, 221); font-family: Verdana, sans-serif; text-align: left; background-color: rgb(29, 42, 53);">Increments the field value 增加欄位值</span>                                                                                                                                                          |
| <span style="color: rgb(255, 153, 153); font-family: Consolas, Menlo, &quot;courier new&quot;, monospace; font-size: 15.75px; text-align: left; background-color: rgba(222, 222, 222, 0.1);">$rename</span>      | <span style="color: rgb(221, 221, 221); font-family: Verdana, sans-serif; text-align: left; background-color: rgb(29, 42, 53);">Renames the field 重命名字段</span>                                                                                                                                                                   |
| <span style="color: rgb(255, 153, 153); font-family: Consolas, Menlo, &quot;courier new&quot;, monospace; font-size: 15.75px; text-align: left; background-color: rgba(222, 222, 222, 0.1);">$set</span>         | <span style="color: rgb(221, 221, 221); font-family: Verdana, sans-serif; text-align: left; background-color: rgb(29, 42, 53);">Sets the value of a field</span><span style="color: rgb(221, 221, 221); font-family: Verdana, sans-serif; text-align: left; background-color: rgb(29, 42, 53);">設定欄位的值</span>                    |
| <span style="color: rgb(255, 153, 153); font-family: Consolas, Menlo, &quot;courier new&quot;, monospace; font-size: 15.75px; text-align: left; background-color: rgba(222, 222, 222, 0.1);">$unset</span>       | <span style="color: rgb(221, 221, 221); font-family: Verdana, sans-serif; text-align: left; background-color: rgb(29, 42, 53);">Removes the field from the document 從文件中刪除字段</span>                                                                                                                                              |  
> 
> 


> [!danger] Update Array
> 
> 
|                                                                                                                                                                                      operator                                                                                                                                                                                      |                                                                                                                                                                          功能                                                                                                                                                                           |     |
| :--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------: | :---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------: | --- |
|                                                                                   <span style="color: rgb(255, 153, 153); font-family: Consolas, Menlo, &quot;courier new&quot;, monospace; font-size: 15.75px; text-align: left; background-color: rgba(222, 222, 222, 0.1);">$addToSet</span>                                                                                    |           <span style="color: rgb(221, 221, 221); font-family: Verdana, sans-serif; text-align: left; background-color: rgb(29, 42, 53);">&nbsp; Adds distinct elements to an array</span><span style="color: rgb(221, 221, 221); font-family: Verdana, sans-serif; text-align: left; background-color: rgb(29, 42, 53);">將不同的元素加入陣列中</span>           |     |
|                                                                                      <span style="color: rgb(255, 153, 153); font-family: Consolas, Menlo, &quot;courier new&quot;, monospace; font-size: 15.75px; text-align: left; background-color: rgba(222, 222, 222, 0.1);">$pop</span>                                                                                      |      <span style="color: rgb(221, 221, 221); font-family: Verdana, sans-serif; text-align: left; background-color: rgb(29, 42, 53);">Removes the first or last element of an array</span><span style="color: rgb(221, 221, 221); font-family: Verdana, sans-serif; text-align: left; background-color: rgb(29, 42, 53);">刪除陣列的第一個或最後一個元素</span>       |     |
| <code class="w3-codespan" data-immersive-translate-walked="8e4effa2-0368-4173-bbb0-990b444b6f81" style="box-sizing: inherit; font-family: Consolas, Menlo, &quot;courier new&quot;, monospace; font-size: 15.75px; color: rgb(255, 153, 153); background-color: rgba(222, 222, 222, 0.1); padding-left: 4px; padding-right: 4px; font-weight: 400; text-align: left;">$pull</code> | <span style="color: rgb(221, 221, 221); font-family: Verdana, sans-serif; text-align: left; background-color: rgb(29, 42, 53);">Removes all elements from an array that match the query</span><span style="color: rgb(221, 221, 221); font-family: Verdana, sans-serif; text-align: left; background-color: rgb(29, 42, 53);">從陣列中刪除與查詢相符的所有元素</span> |     |
|                                                                                     <span style="color: rgb(255, 153, 153); font-family: Consolas, Menlo, &quot;courier new&quot;, monospace; font-size: 15.75px; text-align: left; background-color: rgba(222, 222, 222, 0.1);">$push</span>                                                                                      |                  <span style="color: rgb(221, 221, 221); font-family: Verdana, sans-serif; text-align: left; background-color: rgb(29, 42, 53);">Adds an element to an array</span><span style="color: rgb(221, 221, 221); font-family: Verdana, sans-serif; text-align: left; background-color: rgb(29, 42, 53);">為陣列新增一個元素</span>                   |     |
> 





#### `updateOne(filter,update,options)` 更新匹配過濾器的單個文檔

parameter:
- **filter**：用于查找文档的查询条件。
- **update**：指定更新操作的文档或更新操作符。
- **options**：可选参数对象，如 `upsert`、`arrayFilters` 等

> [!example] 
> ```jsx
> db.myCollection.updateOne(
>     { name: "Alice" },                // 过滤条件
>     { $set: { age: 26 } },            // 更新操作
>     { upsert: false }                 // 可选参数
> );
> ```


#### `updateMany(filter,update,options)` 更新所有匹配過濾的文檔

parameter:
- **filter**：用于查找文档的查询条件。
- **update**：指定更新操作的文档或更新操作符。
- **options**：可选参数对象，如 `upsert`、`arrayFilters` 等。


> [!example]
> ```jsx
> db.myCollection.updateMany (
>     { age: { $lt: 30 } },             // 过滤条件
>     { $set: { status: "active" } },   // 更新操作
>     { upsert: false }                  // 可选参数
> );
> ```


#### `replaceOne(filter, replacement, options)` 替換匹配過濾器的單個文檔，新的文檔完全替換舊的文檔
parameters:
- **filter**：用于查找文档的查询条件。
- **replacement**：新的文档，将替换旧的文档。
- **options**：可选参数对象，如 `upsert` 等。

> [!example] 
> ```jsx
> db.myCollection.replaceOne (
>     { name: "Bob" },                  // 过滤条件
>     { name: "Bob", age: 31 }          // 新文档
> );
> ```


#### `findOneAndUpdate(filter, update, options)` 查找並更新單個文檔，可以選擇返回更新前或更新後的文檔

parameters:
- **filter**：用于查找文档的查询条件。
- **update**：指定更新操作的文档或更新操作符。
- **options**：可选参数对象，如 `projection`、`sort`、`upsert`、`returnDocument` 等

> [!example] 
> ```jsx
> db.myCollection.findOneAndUpdate (
>     { name: "Charlie" },              // 过滤条件
>     { $set: { age: 36 } },            // 更新操作
>     { returnDocument: "after" }       // 可选参数，返回更新后的文档
> );
> ```

parameters:
- **upsert**：如果没有匹配的文档，是否插入一个新文档。
- **arrayFilters**：当更新嵌套数组时，指定应更新的数组元素的条件。
- **collation**：指定比较字符串时使用的排序规则。
- **returnDocument**：在 findOneAndUpdate 中使用，指定返回更新前 ("before") 或更新后 ("after") 的文档。





### `pretty()` 以格式化的方式來顯示所有的文檔

`.pretty()` 來顯示結果



### 索引
索引可以極大的提高查詢的效率

在 MongoDB 中，常见的索引类型包括：

- **单字段索引**：基于单个字段的索引。
- **复合索引**：基于多个字段组合的索引。
- **文本索引**：用于支持全文搜索。
- **地理空间索引**：用于地理空间数据的查询。
- **哈希索引**：用于对字段值进行哈希处理的索引。

> [!attention]+     
> ### 索引策略
> 
在创建索引时，需要考虑以下因素：
> 
> - **查询频率**：优先考虑那些经常用于查询的字段。
> - **字段基数**：字段值的基数越高（即唯一值越多），索引的效果越好。
> - **索引大小**：索引的大小会影响数据库的内存占用和查询性能。
> 
> ### 索引优化
> 
在对索引进行优化时，可以考虑以下方法：
> 
> - **选择合适的索引类型**：根据查询需求选择合适的索引类型。
> - **创建复合索引**：对于经常一起使用的字段，考虑创建复合索引以提高查询效率。
> - **监控索引性能**：定期监控索引的使用情况，根据实际需求调整索引。
> 
> ### 注意事项
> 
> - 索引虽然可以提高查询性能，但也会增加写操作的开销。因此，在创建索引时需要权衡查询性能和写入性能。
> - 索引会占用额外的存储空间，特别是对于大型数据集，需要考虑索引的存储成本。
> 
通过合理地设计和使用索引，可以大大提高 MongoDB 数据库的查询性能和响应速度，从而更好地支持应用程序的需求。 
> 


#### `createIndex( keys, options)` 創建索引

- `keys`：一个对象，指定了字段名和索引的排序方向（1 表示升序，-1 表示降序）。
- `options`：一个可选参数，可以包含索引的额外选项。

> [!attention]+ options 参数是一个对象，可以包含多种配置选项，以下是一些常用的选项：
> 
> - `unique`：如果设置为 `true`，则创建唯一索引，确保索引字段的值在集合中是唯一的。
> - `background`：如果设置为 `true`，则索引创建过程在后台运行，不影响其他数据库操作。
> - `name`：指定索引的名称，如果不指定，MongoDB 会根据索引的字段自动生成一个名称。
> - `sparse`：如果设置为 `true`，创建稀疏索引，只索引那些包含索引字段的文档。
> - `expireAfterSeconds`：设置索引字段的过期时间，MongoDB 将自动删除过期的文档。
> - `v`：索引版本，通常不需要手动设置。
> - `weights`：为文本索引指定权重。
> 
> Example:
> 创建地理空间索引  
对于存储地理位置数据的字段，可以使用 2dsphere 或 2d 索引类型来创建地理空间索引。
> ```jsx
> // 2dsphere 索引，适用于球形地理数据  
> db.collection.createIndex( { location: "2dsphere" } )  
> // 2d 索引，适用于平面地理数据  
> db.collection.createIndex( { location: "2d" } )
> ```
> 


##### 創建哈希索引
`db.collection.createIndex ( { field: "hashed" } )`


#### `getIndexes()` 查看索引
`db.collection.getIndexes()`


#### `dropIndex()` or `dropIndexes()` 刪除索引
```jsx
// 删除指定的索引
db.collection.dropIndex( "indexName" )

// 删除所有索引
db.collection.dropIndexes()
```



###  复制（副本集）
MongoDB复制是将数据同步在多个服务器的过程。

复制提供了数据的冗余备份，并在多个服务器上存储数据副本，提高了数据的可用性， 并可以保证数据的安全性。

复制还允许您从硬件故障和服务中断中恢复数据。

#### 什么是复制?
- 保障数据的安全性
- 数据高可用性 (24\*7)
- 灾难恢复
- 无需停机维护（如备份，重建索引，压缩）
- 分布式读取数据


#### MongoDB复制原理

mongodb的复制<font color="#ffc000">至少需要两个节点</font>。其中一个是<font color="#ffc000">主节点</font>，<font color="#ffc000">负责处理客户端请求</font>，其余的都是<font color="#00b0f0">从节点</font>，<font color="#00b0f0">负责复制主节点上的数据</font>。

mongodb各个节点常见的搭配方式为：<font color="#ffc000">一主一从</font>、<font color="#ffc000">一主多从</font>。

主节点记录在其上的所有操作oplog，从节点定期轮询主节点获取这些操作，然后对自己的数据副本执行这些操作，从而保证从节点的数据与主节点一致。

MongoDB复制结构图如下所示：
![[PICTURE/Mongo Operation/1e35b696ebecd87e5f1fe39fdb446ec0_MD5.jpeg|475]]


**副本集特征：**
- N 个节点的集群
- 任何节点可作为主节点
- 所有写入操作都在主节点上
- 自动故障转移
- 自动恢复


##### MongoDB副本集设置
1. 关闭正在运行的MongoDB服务器。
现在我们通过指定 --replSet 选项来启动mongoDB。--replSet 基本语法格式如下：
```jsx
mongod --port "PORT" --dbpath "YOUR_DB_DATA_PATH" --replSet "REPLICA_SET_INSTANCE_NAME"
mongod --port 27017 --dbpath "D:\set up\mongodb\data" --replSet rs0
```
以上实例会启动一个名为rs0的MongoDB实例，其端口号为27017。
启动后打开命令提示框并连接上mongoDB服务。
在Mongo客户端使用命令`rs.initiate()`来启动一个新的副本集。
我们可以使用rs.conf()来查看副本集的配置
查看副本集状态使用 `rs.status()` 命令


###### 副本集添加成员
添加副本集的成员，我们需要使用多台服务器来启动mongo服务。进入Mongo客户端，并使用rs.add()方法来添加副本集的成员
```jsx
> rs.add(HOST_NAME:PORT)
```

MongoDB的副本集与我们常见的主从有所不同，主从在主机宕机后所有服务将停止，而副本集在主机宕机后，副本会接管主节点成为主节点，不会出现宕机的情况。


### 分片
在Mongodb里面存在另一种集群，就是分片技术,可以满足MongoDB数据量大量增长的需求。

当MongoDB存储海量的数据时，一台机器可能不足以存储数据，也可能不足以提供可接受的读写吞吐量。这时，我们就可以通过在多台机器上分割数据，使得数据库系统能存储和处理更多的数据。


#### 为什么使用分片
- 复制所有的写入操作到主节点
- 延迟的敏感数据会在主节点查询
- 单个副本集限制在12个节点
- 当请求量巨大时会出现内存不足。
- 本地磁盘不足
- 垂直扩展价格昂贵

![[PICTURE/Mongo Operation/d9be58ed1474c25e2fc970a20d135b7b_MD5.jpeg|475]]
上图中主要有如下所述三个主要组件：
- **Shard:**
    用于存储实际的数据块，实际生产环境中一个shard server角色可由几台机器组个一个replica set承担，防止主机单点故障
- **Config Server:**
    mongod实例，存储了整个 ClusterMetadata，其中包括 chunk信息。
- **Query Routers:**
    前端路由，客户端由此接入，且让整个集群看上去像单一数据库，前端应用可以透明使用。



> [!example]+ #### 分片實例
> 分片結構端口分佈如下：
> ```jsx
> Shard Server 1：27020
> Shard Server 2：27021
> Shard Server 3：27022
> Shard Server 4：27023
> Config Server ：27100
> Route Process：40000
> ```
> Step 1: 啟動Shard Server
> ```jsx
> [ root@100 /]# mkdir -p /www/mongoDB/shard/s0
[ root@100 /]# mkdir -p /www/mongoDB/shard/s1
[ root@100 /]# mkdir -p /www/mongoDB/shard/s2
[ root@100 /]# mkdir -p /www/mongoDB/shard/s3
[ root@100 /]# mkdir -p /www/mongoDB/shard/log
[ root@100 /]# /usr/local/mongoDB/bin/mongod --port 27020 --dbpath=/www/mongoDB/shard/s0 --logpath=/www/mongoDB/shard/log/s0.log --logappend --fork
....
[ root@100 /]# /usr/local/mongoDB/bin/mongod --port 27023 --dbpath=/www/mongoDB/shard/s3 --logpath=/www/mongoDB/shard/log/s3.log --logappend --fork
> ```
> Step 2: 啟動 Config Server
> ```
> [root@100 /]# mkdir -p /www/mongoDB/shard/config
[root@100 /]# /usr/local/mongoDB/bin/mongod --port 27100 --dbpath=/www/mongoDB/shard/config --logpath=/www/mongoDB/shard/log/config.log --logappend --fork
> ```
>> **注意：** 这里我们完全可以像启动普通mongodb服务一样启动，不需要添加—shardsvr和configsvr参数。因为<font color="#ffc000">这两个参数的作用就是改变启动端口</font>的，所以我们自行指定了端口就可以。
> 
>Step 3: 啟動Router Process 
> ```jsx
> /usr/local/mongoDB/bin/mongos --port 40000 --configdb localhost: 27100 --fork --logpath=/www/mongoDB/shard/log/route.log --chunkSize 500
> ```
> mongos启动参数中，chunkSize这一项是用来指定chunk的大小的，单位是MB，默认大小为200MB.
> 
> Step 4: 配置Sharding 
> 使用MongoDB Shell登录到mongos，添加Shard节点
> ```jsx
> [ root@100 shard]# /usr/local/mongoDB/bin/mongo admin --port 40000
MongoDB shell version: 2.0.7
connecting to: 127.0.0.1:40000/admin
mongos> db.runCommand ({ addshard: "localhost: 27020" })
{ "shardAdded" : "shard0000", "ok" : 1 }
......
mongos> db.runCommand ({ addshard: "localhost: 27029" })
{ "shardAdded" : "shard0009", "ok" : 1 }
mongos> db.runCommand ({ enablesharding: "test" }) #设置分片存储的数据库
{ "ok" : 1 }
mongos> db.runCommand ({ shardcollection: "test. log", key: { id: 1, time: 1}})
{ "collectionsharded" : "test. log", "ok" : 1 }
> ```
>
> Step 5: 程序代码内无需太大更改，直接按照连接普通的mongo数据库那样，将数据库连接接入接口40000




### mongodump備份與mongorestore 恢復

#### 備份
命令腳本語法：
```jsx
mongodump -h dbhost -d dbname -o dbdirectory
```
- **-h：**
    MongoDB 所在服务器地址，例如：127.0.0.1，当然也可以指定端口号：127.0.0.1:27017
- **-d：**
    需要备份的数据库实例，例如：test
- **-o：**
    备份的数据存放位置，例如：c:\data\dump，当然该目录需要提前建立，在备份完成后，系统自动在dump目录下建立一个test目录，这个目录里面存放该数据库实例的备份数据。


| 语法                                                | 描述                | 实例                                               |
|---------------------------------------------------|-------------------|--------------------------------------------------|
| mongodump --host HOST_NAME --port PORT_NUMBER     | 该命令将备份所有MongoDB数据 | mongodump --host runoob.com --port 27017         |
| mongodump --dbpath DB_PATH --out BACKUP_DIRECTORY |                   | mongodump --dbpath /data/db/ --out /data/backup/ |
| mongodump --collection COLLECTION --db DB_NAME    | 该命令将备份指定数据库的集合。   | mongodump --collection mycol --db test           |


#### 恢復
命令腳本語法：
```jsx
mongorestore -h <hostname><:port> -d dbname <path>
```

- **--host <:port>, -h <:port>：**
    MongoDB所在服务器地址，默认为： localhost:27017
- **--db , -d ：**
    需要恢复的数据库实例，例如：test，当然这个名称也可以和备份时候的不一样，比如test2
- **--drop：**
    恢复的时候，先删除当前数据，然后恢复备份的数据。就是说，恢复后，备份后添加修改的数据都会被删除，慎用哦！
- `<path>`：
	mongorestore 最后的一个参数，设置备份数据所在位置，例如：c:\data\dump\test。
	你不能同时指定 `<path>` 和 `--dir` 选项，--dir也可以设置备份目录。
-  `--dir`：
    指定备份的目录
    你不能同时指定 `<path>` 和 `--dir` 选项。





































