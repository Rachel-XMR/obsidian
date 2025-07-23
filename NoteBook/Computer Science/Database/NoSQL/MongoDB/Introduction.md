---
tags: []
LINK:
  - "[[Database]]"
  - "[[NoSQL]]"
  - "[[MongoDB]]"
---

## Document-Based NoSQL System 

- MongoDB is a general purpose 通用的, document-based, distributed database built for modern application developers and for the cloud era
- MongoDB is developed by MongoDB Inc and licensed under the <u>Server Side Public License (SSPL)</u>
- A record in MongoDB is a document, which is a data structure composed of key value pairs similar to the structure of JSON objects. 一條記錄就是一個文檔，它是由鍵值對組成的資料結構，類似JSON物件的結構

> [!code]+ Example
> ```jsx
> {
> title: "Post Title 1",
> body: "Body of post",
> category: "News",
> likes: 1,
> tags: ["news","events"],
> date: Date()
> }
> ```


> [!quote] 優點
> - Popularity 受歡迎
> - High performance 高性能
> - High availability 高可用性
> - Horizontal Scalability 橫向可拓展性
> - Rich query language 豐富的查詢語言
> - Support for Multiple 支持多個
> - Storage Engines 儲存引擎


**Terminology and Concept: SQL and MongoDB**

|    SQL Terms/ Concepts    |  MongoDB Terms/ Concepts  |
| :-----------------------: | :-----------------------: |
| <center>Database</center> | <center>Database</center> |
|           Table           |        Collection         |
|            Row            |         Document          |
|          Column           |           Field           |
|           Index           |           Index           |
|        Table joins        |          $lookup          |
|        Primary key        |        Primary key        |


> [!important]+ SQL vs Document database
> SQL databases are considered <font color="#ffc000">relational databases</font>. They store related data in <font color="#ffc000">separate tables單獨的表格</font>. When data is needed, it is <u>queried from multiple tables to join the data back together</u>.
> 
> MongoDB stores data in flexible documents. Instead of having multiple tables you can simply keep all of your related data together. This makes reading your data very fast.  MongoDB 將資料儲存在靈活的文件中。您可以簡單地將所有相關資料保存在一起，而不需要使用多個表。這使得讀取資料的速度非常快。
> 
> <font color="#ffc000">You can still have multiple groups of data too. In MongoDB, instead of tables these are called collections.  您仍然可以擁有多組資料。在 MongoDB 中，這些稱為集合，而不是表</font>


The core difference comes from the fact that relational databases define columns at the table level whereas a document-oriented database defines its fields at the document level. 
-> each document within a collection can have its own unique set of fields. 每個文件都可以有自己獨特的欄位集

a collection isn't strict about what goes in it (its schema is<u> flexible/dynamic</u>). 對於要放入的內容並不嚴格（模式是彈性的動態的）

> [!caution] Alternatives
> Every document must have a unique \_d field (ObjectId類型的value)
> By default, the \_id field is indexed. You can verify this through the `getIndexes` command 通過 `getIndexes` 指令來驗證
> ```JSON
> db.unicorns.getIndexes()
> ```
> 





### Collection and Document in MongoDB

Database:
- Database is a container for collections
- Each database gets its own set of files
- A single MongoDB server can has multiple databases

Collations:
- Collection is a group of documents
- Collection is equivalent to RDBMS table
- A collection consist inside a single database
- Collections do not enforce a schema
- A collection can have different fields within a documents




![[PICTURE/MongoDB/0f717daf75b7e593c906c122b94f2bba_MD5.jpeg|875]]

![[PICTURE/MongoDB/fed6159d9a45c7c18f01778d0ecf9261_MD5.jpeg|725]]


### Basic Datatypes

|      Datatype      |         Example         |
| :----------------: | :---------------------: |
|        Null        |       {"x": null}       |
|      Boolean       |       {"x": true}       |
|       Number       | {"x": 3.14}<br>{"x": 3} |
|       String       |     {"x": "foobar"}     |
|        Data        |    {"x": new Date()}    |
| Regular expression |     {"x": /foobar/}     |
|       Array        | {"x": ["a", "b", "c"]}  |
| Embedded Document  |  {"x": {"foo":"bar"}}   |
|     Object ID      |    {"x": Objectid()}    |


#### BSON and JSON

> [!col]
> - In MongoDB, database holds collection of documents which are in *JSON-style* (**JavaScript Object Notation Style**) format  保存著 JSON 風格的文檔
> - **JSON** is an open, human and machine-readable standard to transmit data objects consisting of attributes-value pairs 開放的，人類和機器可讀的，用於傳輸由以下內容組成的數據對象的屬性和值對
> - MongoDB represents **JSON** documents in binary-encoded format called Binary JSON (BSON - [bee · sahn]) behind the scene 二進制編碼
>
> ![[PICTURE/MongoDB/0e93f528ce202e1065f3f1c7f54033e6_MD5.jpeg|300]]
>  JavaScript Object Notation Structure
> ![[PICTURE/MongoDB/dc5ff15e6c425efeb55f865f7d7400f3_MD5.jpeg|300]]


##### Binary JSON (BSON)
In BSON: Data is represented in field - value pairs <span style="background:rgba(240, 167, 216, 0.55)">[field - value]</span>

A field/value pair consists of a field name followed by a colon, followed by a value – example:
	name: "Joseph"
Fields are separated by commas – example:
	name: "Joseph", "course": "Databases", score:80
Curly braces hold objects (documents) – example: 括號表示對象
	{name: "Joseph", "course": "Database", score: 80}
Embedded document 嵌入文件 - example:
	{name: "Joseph", courses:{course1: "databases", course2: "python"}}
Any array is stored in brackets [] - example:
	{name: "Joseph", courses:["databases","programming"]}
An array of (one or more) embedded document contains documents embedded in the array - example:
	{name: "Joseph", courses:[{course1: "databases", courses2: "python"}]}


### The *_id Field
	
> [!note]+ Title
> - Each document in a collection requires a <span style="background:rgba(240, 167, 216, 0.55)">unique</span> <font color="#ffc000">\_id</font> field 集合中的每個文檔都需要一個<span style="background:rgba(240, 167, 216, 0.55)">唯一</span>的\_id 字段
> - The <font color="#ffc000">\_id</font> field acts as a primary key to the collection 作為集合的主鍵
> - If an inserted document omits忽略 the <font color="#ffc000">\_id</font> field, an **Objectid** is automatically generated for the <font color="#ffc000">\_id</font> field
> - The <font color="#ffc000">\_id</font> field is always the <u>first field</u> in the document
> - The <font color="#ffc000">\_id</font> field may <u>contain</u> **BSON data** type *except arrays*




---
## MongoDB CRUD Operations

### Query Operators 

> [!NOTE]+ Query Operators
> | Name | Description                                                   |
| :--- | :------------------------------------------------------------ |
| $eq  | Matches values that are equal to specified value              |
| $gt  | Matches values that are greater than a specified value        |
| $gte | Matches values that greater than or equal to specified value  |
| $in  | Matches any of the values specified in an array               |
| $lt  | Matches values that are less than a specified value           |
| $lte | Matches values that are less than or equal to specified value |
| $ne  | Matches all values that are not equal to a specified value    |
| $nin | Matches none of the values specified in an array              |



> [!example]+ Example
> ![[PICTURE/MongoDB/361fc7a3ebd759dc860be658b44222e9_MD5.jpeg|700]]
> 


### Create Operations

- Insert operations add new document to a collection 插入操作將新文檔添加到文檔集中
- If the collection does <u>not currently exist</u>, the insert operations create it 

用於將文檔插入到集和中
```JSON
db. collectionName. insertOne (<documents>)
db. collectionName. insertMany ([<documents>])
db. collectionName. insert (<documents>)
```
> [!example]+ Project collection example
> `db. movies. insertMany ([{"title": "Ghostbusters"},{"title": "Blade Runner"}]); `
> `db. movies. find ()`
>> [!done] Output
>>  `{"_id": ObjectId ("572630ba11722fac4b6b4996"), "title": "Ghostbusters"}`
>>  `{"_id":ObjectId("572630ba11722fac4b6b4997"),"title":"E.T"}`
>>  `{"_id":ObjectId("572630ba11722fac4b6b4998"),"title":"Blade Runner"}`
>> 


#### `insertOne` 
![[PICTURE/MongoDB/a007f249a27f8814d3f5c80047abac5f_MD5.jpeg|675]]


#### `insertMany ()`
![[PICTURE/MongoDB/0d7db61c75ccbc0499e75befec5f3aa2_MD5.jpeg|675]]


> [!code]
> `db.movies.find()`
> 

> [!done]+ output
> ``` JSON
> {_id:ObjectId("61a403fe076beaa055febc15"),title:'Ghostbusters'}
> {_id: ObjectId ("61a403fe076beaa055febc15"), title: 'E.T'}
> {_id: ObjectId ("61a403fe076beaa055febc15"), title: 'Blade Runner'}
> ```

##### ordered operations
![[PICTURE/MongoDB/608e8867a967455117d21e696b9a19eb_MD5.jpeg|475]]

>  Automaticity is at the level of document 自動性指的是文件層面的

![[PICTURE/MongoDB/22ddca90473f0b3d0fc133c71a92c94a_MD5.jpeg|475]]
















### Read Operations
- Read operation retrieves檢索 documents from a collection – queries a collection for documents 
- The following methods are used to read document in a collection

> [!cite]+ Summary 
> 
>> [!col] 
>>>[!important] 
>>>  query specifies selection criteria using query operators, projection specifies fields to be returned 
>>>   ``` JSON
>>>   db.collectionName.find(<(query)><(projection))
>>>   ```
>>>  
>>>>[!example] 
>>>>   Displays all staff and supervisors who work on or supervise projects over the last 3 years
>>>>   ``` JSON
>>>>   db.projectCollection.find( {"pyears": { $gte:3 } }, { staff:1, supervisors:1 })
>>>>   ```
>>>  
>>>>[!done] Output
>>>>   ```JSON
>>>>  { "\_id" : ObjectId("5dabb758d16c90c5b6007ac4"), staff: [
>>>>   
>>>>   {fname: "John", lname: "Smith", hours: 28.4}, {fname: "Joyce", lname: "Marry", hours: 23.4}], supervisors:["James Brown", "Louis Lampard"],
>>>>    ```
>>>   
>> 
>>> [!code]  
>>>  ```JSON
>>>  {
>>>  pname: "ProjectX",
>>>  plocation: "Frankfurt",
>>> pyears: 3,
>>>  staff:[
>>>  {fname: "John", Iname: "Smith", hours: 28.4},
>>>  {fname;"Jocye", Iname:: Marry, hours: 23.4}
>>>  ],
>>>  supervisors:["James Brown", "Louis Lampard"],
>>>  status:{finished: 1, ongoing: 0, comment: "none"}
>>>  })
>>>```
>> 
> 

#### Querying Document: using "`find`"
![[PICTURE/MongoDB/b4986be66e8c57687a7597e82a951476_MD5.jpeg|475]]

#### Querying Document using "`find`"+<(projection)>
![[PICTURE/MongoDB/a53fba8ebf93cb33d3bdb122dbf67e5d_MD5.jpeg|475]]
![[PICTURE/MongoDB/452f37ccab9349af6b226a58ae10d9b5_MD5.jpeg|475]]

![[PICTURE/MongoDB/a9a9c690850662a8ad3f6c29246039c9_MD5.jpeg|475]]

##### Querying on Embedded/Nested Document
![[PICTURE/MongoDB/bf27dad5a29f61684c04539f6b0d39c6_MD5.jpeg|475]]


##### Querying on Array
![[PICTURE/MongoDB/79369a3803a7ff9c44905f104bf7f28f_MD5.jpeg|475]]


##### Querying an Array of Embedded Documents
![[PICTURE/MongoDB/7068218faa4420ee558c3583b09fae61_MD5.jpeg|475]]






### Update Operations
- Modify existing document in collection 
- The following method are used to update documents in a collection


> [!quote]+ Summary
> 
>>[!info] filter denotes the selection criteria for the update action implies the modification to apply, and options implies additional al actions that can be assigned to the operation
>> `db.collectionName.updateMany(<filter>,<update action>,<options>)`
> 
>>[!col]
>>>[!code] 
>>> ```JSON
>>> {
>>>   pname: "ProjectX",
>>>   plocation: "Frankfurt",
>>>  pyears: 3,
>>>   staff:[
>>>   {fname: "John", Iname: "Smith", hours: 28.4},
>>>   {fname;"Jocye", Iname:: Marry, hours: 23.4}
>>>  ],
>>>  supervisors:["James Brown", "Louis Lampard"],
>>>  status:{finished: 1, ongoing: 0, comment: "none"}
>>>   })
>>> ```
>> 
>>> [!done] Updates  Updates the finished and ongoing status of all projects whose number of years is >= 5 to 1 and 0, respectively
>>> ``` JSON
>>> db.pojectCollection.updateMany(
>>> {"pyears":{$gte:5}},
>>> {$set:{"status.finished":1}}
>>> )
>>> ```


#### `updateOne`
![[PICTURE/MongoDB/f2689b04657ca13b31220b58899bc599_MD5.jpeg|475]]

##### `updateOne` : “`$set`” Operator
![[PICTURE/MongoDB/56248e7ddf7c9b70ad180f4db8f60bf1_MD5.jpeg|475]]
>   Note: "`$set`" <u>sets the value of a field</u>. If the field does not yet exist, it will be *created*. If the user decides that he enjoys a different book, "$ set" can be used again to **change the value**

![[PICTURE/MongoDB/3c4de0bd9f0e16bf6f82b89f232bce1c_MD5.jpeg|475]]
>   "`$set`" can change the type of the key it modifies (in above example from a value to an array) 更改鍵的類型


##### `$unset` operator
![[PICTURE/MongoDB/f779c19e6b90cebad2ea699b1e4e5f0a_MD5.jpeg|475]]


##### `$inc` Operator
![[PICTURE/MongoDB/07d088953cfe18a65862c0ca127302c3_MD5.jpeg|475]]
>  "`$inc`" will create the field “pageview” if it does not exist and assign value “1” to it




##### `$push` operator for Array - Adding Element with 
![[PICTURE/MongoDB/08d4dfc0b3b75b19f670a39a986bcd88_MD5.jpeg|475]]
>  `$push` will create an array “comments” if it does not exist
![[PICTURE/MongoDB/467cd4510753cc668ffe15f508b77707_MD5.jpeg|475]]

##### `$addToSet` Array Operators - Adding Element
![[PICTURE/MongoDB/75f88687fada704afc4de86f5cf343c5_MD5.jpeg|475]]
避免添加重複的array elements 因為如果遇到重複的會被跳過，重複的值不會被成功加入進去
![[PICTURE/MongoDB/e01fd00ab68f9451e75f2e8101d2469d_MD5.jpeg|475]]


##### `$pull` Array Operators - remove element
![[PICTURE/MongoDB/dd257ab8824dc54cb50d55d7bae059c2_MD5.jpeg|475]]


> [!attention] 
> `{"$pop" : {"key" : 1}}` removes an element from the end of the array. 
> `{"$ pop" : {"key" : -1}}` removes it from the beginning. 


##### Positional Array Modification
![[PICTURE/MongoDB/513dd5a10a5d9164a0bd00117e589589_MD5.jpeg|475]]


##### `upsert` Operator
![[PICTURE/MongoDB/1c17c47e4341675054376cfaadc6bb61_MD5.jpeg|475]]

- An `upsert` is a special type of update. If no document is found that matches the filter, a new document will be <u>created by combining</u> the criteria and updated documents
- If a matching document is found, it will be updated normally



#### updating Multiple Documents 
![[PICTURE/MongoDB/4242cab5b3ac7719a09ec10915aaeb32_MD5.jpeg|475]]

##### `insertMany()` 
##### 












### Delete Operation
- Delete operations remove documents from a collection
- The following methods are used to remove documents from a collection 

> [!hint] Filter specifies deletion criteria標準 using query operators, and options specifies additional optional actions that can be assigned to the operation 使用查詢運算符指定刪除標准 options則指定額外的可選操作
> `db.collectionName.deleteMany(<filter>,<options>)`

> [!example] Deletes all projects whoes finished status is 1 and ongoing status is 0
> ```JSON
> db.projectCollection.deleteMany(
> {"status.finished":1, "status.ongoing":0}
> )
> ```


#### `deleteOne` 
![[PICTURE/MongoDB/b6015748c2052e5df740ecad6b79fb25_MD5.jpeg|475]]



#### `deleteMany ()` 
![[PICTURE/MongoDB/c80e3457f1895887527fb120039de9d7_MD5.jpeg|475]]



#### `drop()`
![[PICTURE/MongoDB/a2d1bf51d9973d09e43af3c7cee5bb70_MD5.jpeg|475]]



### index on any attribute:
Indexing in MongoDB allows for faster data retrieval by creating a searchable structure on selected attributes, optimizing query performance.




**Replication and high availability****: MongoDB’s replica sets ensure data redundancy by maintaining multiple copies of the data, providing fault tolerance and continuous availability even in case of server failures.  
***复制和高可用性****：MongoDB 的副本集通过维护数据的多个副本来确保数据冗余，即使在服务器发生故障的情况下也能提供容错和持续可用性。























































































