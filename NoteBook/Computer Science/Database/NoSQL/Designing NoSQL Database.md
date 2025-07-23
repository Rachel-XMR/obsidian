---
LINK:
  - "[[Database]]"
  - "[[NoSQL]]"
  - "[[MongoDB]]"
---


# Indexes

A database index is similar to a book's index. instead of looking through the whole book, the database takes a <font color="#ffc000">shortcut</font> and looks at an <span style="background:#d4b106">ordered list</span> with reference to the content.
A query that does not use an index is called a <span style="background:#d4b106">collection scan</span>, which means that the server has to “<span style="background:#fdbfff">look through the whole documents in the collection</span>” to find a query’s results.


## 順序如何影響性能
MongoDB index就像一本字典的目錄
- 當索引字段在前面的字段匹配查詢條件時，MongoDB可以快速跳轉到關鍵記錄
- 但如果查詢忽略了前面的字段，索引就無法被有效的利用



## Collection Scan


> [!example]+ 
> 
> ```js
> for (i=0; i<100000; i++){
> 	db.users.insertOne(
> 		{
> 			"i",
> 			"username":"user"+i,
> 			"age": Math.floor(Math.random()*120),
> 			"created": newDate()
> 		}
> 	)
> }
> ```
> 
>> [!done] Output
>>  ```
>> {_id:Object("636e2e9d923019e356f6e354"),
>> i:0,
>> username:'user0',
>>  age:77,
>>  created:2022-11-11T11:14:37:548Z
>>  }
>> ```
> 


## Create an Index `createIndex()`
`Create Index(creates an ascednding index on the username field in the users collection)`

```
db.users.creatIndex({'username':1})
```

修改索引字段的寫入操作 (插入，更新，和刪除) 將花費更長的時間。 

## Compound Index 復合索引
`db.users.createIndex({"age":1,"username":1})`

> [!tip] 
> 這裡創建了一個基於age和name的復合索引，且按照升序排序 (1代表升序)
> 
> 索引的順序是{"age": 1,"username": 1}表示索引優先基於age的值排序，再基於name的值排序
> 
>>  使用復合索引的query：
>>  `db.users.find({"age":{"$gte":21,"$lt":30}}).sort({"username":1})`
>>  篩選條件： 21≤age＜30的文件
>>  排序條件：按照username升序排序
>>  使用我們剛創建的復合索引可以提高性能
> 
>> [!attention] 調整索引： 需要基於實際的業務場景
>> 索引的排序邏輯：第一個先排序然後再排第二個
>> 如例子針對age排序後再排序username，那麼在age相同時進一步按照username排序。
>> 適用場景： 基於age的範圍查詢
>> 1. 索引首先快速定位age在[21,30) 範圍內的記錄
>> 2. 由於數據已經按照age和username排序，因此MongoDB不需要額外排序操作
>> 
>> 如此如果查詢主要依賴age作為篩選條件，這種索引效率更高他優化了篩選和排序操作
> 但是如果查詢依賴username進行篩選，這種索引的效率不高，因為MongoDB需要掃描整個索引中所有age的值



## 優化的核心原理

1. 快速定位範圍 (fieldname) \[{"age": 1,"username": 1}為例子\]
	- 當使用復合索引時\[{"age": 1, "usernam":1}\]，MongoDB的索引數據結構會按照age作為首要順序存儲數據
	- 查詢條件 condition 會直接跳轉到索引中符合條件的第一個condition的位置，然後逐步掃描到field符合的最後一個的數據范圍\[{"age":{"$gte": 21,"$ lt": 30}}為condition 所以掃描索引符合的第一個age=21的位置一直到age=29的數據範圍\]
	- <span style="background:#fdbfff">這樣MongoDB無需遍歷整個集合的所有記錄，而是僅僅掃描滿足condition[age條件]的記錄</span>
2. 排序已經內置 \[{"age": 1,"username": 1}為例子\]
	- 索引中的數據在age相同的情況下，已經按照 `username` 升序排列
	- 因此在執行查詢 `sort({"username":1})` 時，MongoDB不需要再額外執行排序操作
	- 查詢引擎只需按照索引順序讀取數據，這樣可以顯著提高性能


### **避免遍歷所有記錄的原因**

1. **索引結構**： MongoDB 的索引是基於 **B樹結構**（B-Tree）實現的。這種結構允許高效地：
    
    - **定位範圍內的數據**：例如 `age >= 21 且 age < 30`。
    - **按索引順序掃描數據**：節省排序開銷。
2. **複合索引的設計**：
    
    - 索引 `{"age": 1, "username": 1}` 不僅按照 `age` 排序，還在 `age` 相同的情況下，按 `username` 排序。
    - 所以，查詢結果天然滿足 `age` 的篩選條件和 `username` 的排序條件。


# Aggregation Framework 聚合框架 `aggregate()`
Pipeline—(has)—Stage—(have)—Tunables
![](PICTURE/Designing%20NoSQL%20Database/bb6e654491f22e6d65a01f1956121e27_MD5.jpeg)
![](PICTURE/Designing%20NoSQL%20Database/12381069ecddea227b5e59508873b3d0_MD5.jpeg)

`[db].[myCollection].aggregate([{Aggregation stages},{},...,{}])`


```js
db.companies.aggregate([
//step1: 找到年份是2004年的item
{$match:{founded_year:2004}},
//step2：限制5個
{$limit:5},
//step3:格式化輸出結果，只保留名字
{$project:{
_id:0,
name:1
}}
])
```


# Schema Design


![](PICTURE/Designing%20NoSQL%20Database/a7b28b0a1b5affa16567415f897087b8_MD5.jpeg)

##  Considerations

- **Constraints限制**: Understand any **database** or **hardware** limitations
- **Access patterns訪問模式 of your queries and of your writes**: identify and quantify the workload of your application and of the wider system 識別並量化應用程序和更廣泛系統的工作負載
- **Relationship types**: consider which data is related in terms of your application’s needs  確定文檔和數據的相關方式後需要考慮關係的基數
- Cardinality: Once you have determined how your documents and your data are related, you should consider the cardinality of these relationships


## Patterns
MongoDB的幾種常見數據建模模式，用於應對不同類型的應用場景和查詢需求

![](PICTURE/Designing%20NoSQL%20Database/d8864ff74f6fa0b437916e5f516dbb01_MD5.jpeg)


- **Bucket pattern**：suitable for *time series* data where the data is captured as a stream over a period of time 
	- 例如IoT設備傳感器的數據，應用程序日誌，股票市場數據等
	- 將數據劃分為時間段 (one day，one hour...) 並將屬於同一個時間段的數據存儲在同一個文檔中
	- 優勢：減少文檔數量，降低數據查詢和存儲的開銷
```JSON
  
{ sensor_id: 12345, start_date: ISODate("2019-01-31T10:00:00.000Z"), end_date: ISODate("2019-01-31T10:59:59.000Z"), measurements: [ { timestamp: ISODate("2019-01-31T10:00:00.000Z"), temperature: 40 }, { timestamp: ISODate("2019-01-31T10:01:00.000Z"), temperature: 40 }, … { timestamp: ISODate("2019-01-31T10:42:00.000Z"), temperature: 42 } ], transaction_count: 42, sum_temperature: 2413 }
```
- **Outlier pattern**：addresses the rare instances where a few queries of documents fall outside the normal pattern for the application 某些文件異常的大或結構與其他文檔不同時
	- 用於應對少數數據記錄與常規數據模式不匹配的情況如異常值的存儲
	- 將異常值從主數據集中分離出來，單獨存儲以減少主數據集的複雜性並優化查詢性能
	- 場景：
		- - 某些文檔的字段數量過多或字段值過大，導致集合中的數據不均勻。
		- 文檔異常數據在常規查詢中很少用到，但對存儲和性能產生了不利影響。
		- 異常文檔可能會頻繁修改或讀取，影響整個集合的性能。
		- 例如電商評價系統， 某些熱門產品有極多的評論，導致單個商品文檔異常龐大。這樣的文檔會降低整個數據庫的性能。 這時候將該商品的信息進行分支 batch field 這樣子一次就不用展現所有的內容
	- 優勢：對數據集的查詢效率更高，且異常值可以單獨分析
- **Computed pattern**：This is used when data needs to be<span style="background:#b1ffff"> computed frequently</span>, and it can also be used when the data access pattern is ==<span style="background:#b1ffff">read-intensive</span>==
	- 當數據需要頻繁計算時，適用於存儲計算結果以避免重複計算
	- 預先計算好一些字段的結果 (例如平均值，總和等)，直接存儲在文檔中，而不是每次查詢時重新計算
	- 優勢：減少計算成本
- **Extended referencing pattern拓展引用模式**：used for scenarios where you have many <span style="background:#40a9ff">different logical entities or“things,”</span> each <span style="background:#affad1">with their own collection</span>, but you may want to <span style="background:#d4b106">gather these entities together for a specific function</span>
	- 用於涉及多集合並需要將他們合併查詢的場景，例如用戶和他們的訂單數據
	- 在某集合中存儲其他集合的引用。(類似於關係型數據庫的外鍵) 以實現誇集合查詢
	- <span style="background:#ff4d4f">優勢：靈活處理多對多關係</span>
- **Approximation pattern近似模式**：useful for situations where *resource-expensive* (time, memory, CPU cycles)<span style="background:#d3f8b6"> calculations are needed</span> but where <span style="background:#d3f8b6">exact precision is not absolutely required</span> 需要大量計算但是不追求精確度
	- 例如大數據統計分析
	- 與計算近似結果 (平均值，直方圖等) 以提升性能
	- 優勢：減少查詢時間和計算資源的消耗
- **Polymorphic pattern 多態模式**： used when documents have more similarities than they have differences. look at specific fields in the document or sub-document to be able to track differences. 通常用一個字段 (type) 來表示數據的類型，並根據類型來解釋其具結構和含義
	- 查詢需求以通用屬性為主：經常需要查詢通用字段，而具體字段的查詢需求較少
	- Example
		- Single View applications  单一视图应用程序
		- Content management  内容管理
	    - Mobile applications  移动应用
	    - A product catalog  产品目录
    - 這種模式可以幫助我們靈活地存儲結構不同但具有一定關聯性的數據
    - **降低開銷**：避免為每種數據類型創建單獨的集合，減少維護成本
- **Attribute Pattern**：解決屬性多樣化或動態屬性的場景。當需要存儲許多具有不同屬性的實體時，該模式能夠有效地組織數據並減少結構的複雜性
	- **動態屬性**：實體可能具有多種不同屬性，且這些屬性是動態的或用戶定義的。例如，電子商務網站中的商品屬性（顏色、尺寸、品牌等）各不相同。
	- **屬性數量多且稀疏**：大多數屬性只適用於少數文檔，且文檔之間屬性重疊很少
	- **頻繁查詢動態屬性**：需要靈活查詢和篩選特定屬性及其值的文檔
	- 
```JSON
{
  "_id": 1,
  "name": "Smartphone",
  "attributes": {
    "brand": "TechBrand",
    "warranty": "2 years",
    "screen_size": "6.5 inches"
  }
},
{
  "_id": 2,
  "name": "T-shirt",
  "attributes": {
    "size": "L",
    "color": "Blue",
    "material": "Cotton"
  }
}
```
	
- 優點
	- 屬性動態存儲，適應性強。
	- 無需為每個屬性設置單獨字段，減少結構冗餘
- **The Subset Pattern**：
	- ### **適用場景**
		- **超大文檔**：主文檔的字段過多，單個文檔非常龐大。
		- **字段頻率不均**：某些字段的查詢頻率非常低，但會占用存儲空間或影響性能。
		- **修改頻率不同**：某些字段頻繁更新，而其他字段則很少更新。



多態模式

| 優點                                  | 缺點                                                |
|-------------------------------------|---------------------------------------------------|
| 1. 簡化結構：只需要管理一個集合，減少數據庫的複雜性。        | 1. 字段過多：不同類型數據的字段可能非常多，會導致集合中文檔的結構變得複雜，甚至有許多字段為空。 |
| 2. 靈活性強：方便添加新的數據類型，無需修改數據結構或創建新集合。  | 2. 性能問題：由於存儲的數據類型不一致，可能會影響索引和查詢性能，尤其在集合非常大的情況下。   |
| 3. 查詢通用字段方便：可以輕鬆根據通用屬性進行查詢，無需跨集合操作。 | 3. 類型依賴高：業務邏輯需要依賴 type 或其他標識來判斷具體類型，增強了應用程序的複雜性。  |

attribute pattern

| 優點                           | 缺點                                               |
|------------------------------|--------------------------------------------------|
| 靈活性強：可以存儲任意屬性，無需修改數據庫結構。     | 查詢效率可能降低：屬性被嵌套在 attributes 字段中，可能需要額外的索引來提高查詢效率。 |
| 存儲效率高：稀疏字段問題被解決，只有需要的屬性才會存儲。 | 缺乏結構化驗證：動態屬性可能缺少類型驗證和標準化，容易導致數據不一致。              |
| 擴展性好：可以輕鬆添加新屬性，無需更改現有數據或結構。  | 難以支持複雜的聚合：對嵌套屬性的計算和分組操作比結構化字段更複雜。                |


outliers pattern

| 特性     | 未優化數據結構                   | 使用 Outlier Pattern           |
|--------|---------------------------|------------------------------|
| 查詢性能   | 查詢商品基本信息時需要加載所有評論數據，性能較低。 | 查詢商品基本信息時無需加載評論數據，性能更高。      |
| 存儲效率   | 文檔異常龐大，導致存儲空間浪費。          | 異常數據被拆分，存儲更加均勻高效。            |
| 修改靈活性  | 修改評論會更新整個商品文檔，影響性能。       | 修改評論只需操作評論集合，與商品文檔分離，操作靈活性高。 |
| 適配複雜查詢 | 在評論字段進行篩選和排序較複雜，且性能低。     | 可在評論集合中直接操作，支持更高效的篩選和聚合。     |







區別：

| Pattern               | 核心目的                                                                                            | 精度                                                                                                 | 適用場景                                                   | 例子                                       | 優點           | 缺點                              |
| --------------------- | ----------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------- | ------------------------------------------------------ | ---------------------------------------- | ------------ | ------------------------------- |
| Computed Pattern      | 預存<font color="#ffc000">精確</font>的計算結果，用於<font color="#ffc000">頻繁查詢</font>，避免每次都需要重新計算以提升性能。    | 結果需要<span style="background:rgba(205, 244, 105, 0.55)">精確計算</span>，如匯總的銷售額、商品庫存總數等。                | 當查詢需要頻繁地進行計算時（例如匯總值或平均值）可以提前計算並存儲結果，適用於對精度要求高的應用場景。    | 假設有一個電子商務應用需要經常查詢每個用戶的總消費金額              | 結果精確、適合頻繁查詢  | 如果數據變更頻繁，可能需要頻繁更新預存計算結果，增加維護成本。 |
| Approximation Pattern | 預存<font color="#ffc000">近似</font>結果，用於<font color="#ffc000">資源密集型計算場景</font>，優化性能，但不追求結果的完全精確性。 | 結果是<span style="background:rgba(205, 244, 105, 0.55)">近似值</span>，例如統計分析中的百分比、分佈、平均值等，對於場景來說不需要完全準確 | 當數據量非常龐大或計算需要大量資源（例如內存、CPU 時間）時，可以預存近似值來節省資源，適用於大數據分析。 | 假設需要分析用戶的行為數據，計算每個用戶點擊行為的平均值，但數據集有數十億條記錄 | 節省資源、適合大數據分析 | 結果不夠精確，可能不適用於對精度有嚴格要求的場景。       |


| 特性    | Polymorphic Pattern             | 分集合模式（每種類型單獨一個集合）      |
|-------|---------------------------------|------------------------|
| 結構靈活性 | 高，新增類型無需改變結構或添加集合。              | 較低，新增類型需要新建集合，且管理成本增加。 |
| 查詢性能  | 通用字段查詢方便，但數據類型不同可能導致查詢變慢。       | 每個集合內的數據結構一致，查詢性能更高。   |
| 維護成本  | 低，只需管理一個集合。                     | 高，需要維護多個集合，特別是數據類型多時。  |
| 數據隔離性 | 差，不同類型數據混合在一個集合中，數據隔離性低。        | 高，不同類型數據存儲在獨立集合中，隔離性好。 |
| 場景適配  | 適合數據類型數量多，但類型屬性較少、查詢多基於通用字段的場景。 | 適合數據類型固定且結構穩定的場景。      |


| 特性    | Attribute Pattern         | 嵌入式模式（Embedded Pattern） |
|-------|---------------------------|-------------------------|
| 靈活性   | 高，可以存儲動態屬性。               | 靈活性低，字段固定，適合結構穩定的數據。    |
| 結構複雜性 | 較高，屬性存儲在嵌套對象中，結構不如固定字段直觀。 | 較低，字段固定，結構更簡單。          |
| 查詢性能  | 嵌套屬性查詢性能較低，需索引支持。         | 固定字段查詢性能更高，索引更簡單。       |
| 維護成本  | 低，可以輕鬆添加或修改屬性。            | 高，新增字段需要改變數據結構。         |
| 場景適配  | 適合動態屬性或稀疏字段數據的場景。         | 適合結構穩定且屬性固定的場景。         |















# Normalization

**Referencing Data Model**: Normalization
Referencing model enables normalisation of data by storing references between documents to indicate relationship between the data stored in each document 通過存儲文檔之間的引用來指示每個文檔匯總存儲的數據之間的關係 從而實現數據規範化

在一個文檔中存儲另一個文檔的ID來建立兩個文檔之間的關係。
Normalization：減少冗餘和提高數據一致性，避免數據更新時的不一致性問題

![](PICTURE/Designing%20NoSQL%20Database/da7fd2ee691a4323a536b3245c83b46b_MD5.jpeg)

better for:
- Fast writes
- Large subdocuments 如果文檔包含了大量的嵌套數據，使用引用可以避免文檔過大，提高查詢效率
- Volatile data 易變數據 無需修改相關文檔
- when immediate consistency necessary
- Documents that grow by a large amount
- Data that you’ll often exclude from the results


與引用文檔相對的是嵌入式數據模型 (Embedded Data Model) 

| 特性               | 引用式文檔（Referencing）                    | 嵌入式文檔（Embedding）                                 |
|------------------|---------------------------------------|--------------------------------------------------|
| 結構               | 將相關數據存儲在多個集合中，使用 _id 進行關聯。            | 將相關數據直接嵌套在同一個文檔中。                                |
| 查詢性能             | 查詢時可能需要多次查詢和聯合操作（$lookup）。            | 單次查詢即可獲得全部所需數據，查詢速度較快。                           |
| 數據冗餘             | 避免數據冗餘，相關數據只存儲一次。                     | 有數據冗餘的可能，特別是當嵌套結構重複出現時。                          |
| 一致性（Consistency） | 更新數據時容易保持一致性，因為數據分散存儲，不同文檔之間有明確關聯。    | 更新嵌套結構內的數據比較繁瑣，可能需要更新多個嵌套文檔，容易引發不一致性問題。          |
| 靈活性（Scalability） | 更適合處理多對多和一對多關係，尤其是數據結構經常變化時（適合分片和擴展）。 | 適合處理固定的一對多關係（例如：用戶和他們的地址）。如果數據嵌套層次過深，可能導致文檔大小過大。 |
| 數據讀寫性能           | 如果關聯數據量多或經常需要聯合查詢，性能可能較低。             | 嵌入式數據結構讀取速度快，因為不需要跨集合操作，但文檔過大可能影響性能。             |
| 數據更新成本           | 如果需要修改相關數據，僅需更新單個文檔，操作範圍小。            | 如果嵌套數據重複出現在多個文檔中，更新時需要對每個相關文檔進行修改，成本高。           |
| 存儲效率             | 因為沒有重複數據，存儲效率較高。                      | 可能會存儲大量重複數據，增加存儲需求。                              |
| 適用場景             | 適合數據之間關係複雜或需要跨集合查詢的場景，例如：用戶和訂單的多對多關係。 | 適合數據之間關係明確且固定的一對多關係，例如：博客文章及其評論。                 |


選擇：

| 考慮因素                                  | 推薦方案                                                                                 |
| ------------------------------------- | ------------------------------------------------------------------------------------ |
| 查詢性能是否重要？                             | 如果<span style="background:rgba(240, 200, 0, 0.2)">查詢速度</span>非常重要，建議使用**嵌入式文檔**。     |
| 數據是否需要重用？                             | 如果數據需要在<span style="background:rgba(240, 200, 0, 0.2)">多個集合中共享</span>，建議使用**引用式文檔**。 |
| 數據是否關聯性複雜？                            | 如果<span style="background:rgba(240, 200, 0, 0.2)">關聯性複雜</span>（多對多關係），建議使用**引用式文檔**。 |
| 數據是否經常變更？                             | 如果<span style="background:rgba(240, 200, 0, 0.2)">嵌套數據變更頻繁</span>，使用**引用式文檔**以降低更新成本。                                                       |
| <font color="#ffc000">文檔是否會過大？</font> | <font color="#ffc000">如果嵌入會導致文檔大小超過 MongoDB 的限制，應使用引用式文檔</font>。                     |

















