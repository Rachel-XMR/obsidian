---
LINK:
  - "[[MongoDB]]"
  - "[[NoSQL]]"
  - "[[Computer Science/Database/NoSQL/Designing NoSQL Database.md]]"
File: Computer Science/Database/NoSQL/MongoDB/Data Modelling in MongoDB.md
---


## RDBMS vs MongoDB

### RDBMS :
Modelling for RDBMS
- Step 1: Define Schema
- Step 3: Develop the applications and DB queries
Concerns 擔憂
- One correct solution 一種正確的解決方案
- Data dictates決定 how you develop your application – not usage
and application evolution演變
- Usage makes schema demoralized – performance dropping

### MongoDB
![](PICTURE/Data%20Modelling%20with%20MongoDB/34e64dc7ce843c587ae989d520dc0d7d_MD5.jpeg)
MongoDB 的 data model 具有High flexibility。 **靈活且可變的**

圖片描述的是一個資料價值創造週期，它強調資料模型是一個不斷演進的過程：

1. **Develop and define data model（開發和定義資料模型）：** 根據應用程式的需求，初步設計資料模型。這包括決定如何組織資料、使用哪些欄位、以及如何建立文檔之間的關聯。
2. **Re-define data model（重新定義資料模型）：** 隨著應用程式的發展和需求的變化，原有的資料模型可能不再適用。這時就需要重新評估和調整資料模型，以更好地滿足新的需求。
3. **Improve the application（改進應用程式）：** 根據重新定義的資料模型，相應地修改應用程式的程式碼，以確保應用程式能夠正確地讀取和寫入資料。
4. **Improve data model（改進資料模型）：** 根據應用程式的實際使用情況和效能表現，進一步優化資料模型，例如調整內嵌和參考的使用方式、優化索引等。
這個週期是一個持續的過程，隨著應用程式的不斷發展，資料模型也會不斷演進和改進。








- **Schema-less（無結構綱要）：** 集合（Collection，類似於關聯式資料庫的表）中的文檔不需要遵循固定的結構。不同的文檔可以有不同的欄位，這使得資料模型非常靈活，易於適應不斷變化的需求。這也是圖片中「Re-define data model」和「Improve data model」能夠不斷循環的原因。
- **內嵌式（Embedded）和參考式（Referencing）：** 相關的資料可以內嵌在同一個文檔中，也可以透過參考（類似於外鍵）連結到其他文檔。這提供了多種資料組織方式，可以根據不同的應用場景選擇最適合的方案。
- **動態性：** 您可以隨時新增、修改或刪除文檔中的欄位，而不需要像關聯式資料庫那樣進行結構變更（Schema Migration）










| 特性   | MongoDB            | 關聯式資料庫               |
| ---- | ------------------ | -------------------- |
| 資料模型 | 文檔導向               | 關係模型                 |
| 結構綱要 | 無結構綱要（Schema-less） | 基於結構綱要（Schema-based） |
| 資料組織 | 內嵌和參考              | 正規化表格和外鍵             |
| 靈活性  | 高，易於適應變化           | 低，需要結構變更             |
| 效能   | 讀取效能通常較高（尤其在使用內嵌時） | 寫入效能通常較高（尤其在高度正規化時）  |
| 適用場景 | 快速迭代開發、非結構化資料、高讀取量 | 資料一致性要求高、複雜關聯查詢      |
|      |                    |                      |

> [!example] 
> 
>> [!col] 
>> 
>>> [!code] RDBMS   
>>>   ```SQL
>>>   CREATE TABLE users(
>>>  	id INT PRIMARY KEY,
>>>   	name VARCHAR(255),
>>>   	email VARCHAR(255),
>>>   	phone VARCHAR(20)
>>>   );
>>>   ``` 
>>   
>>>[!code] MongoDB
>>>   ```JSON
>>>   {
>>>   "_id":ObjectId("..."),
>>>   "name":"zhangsan",
>>>   "email":"zhangsan@example.com",
>>>   "phone":"1380013800"
>>>   }
>>>  {
>>>   "_id": ObjectId ("..."),
>>>   "name": "zhangsan",
>>>   "email": " zhangsan@example.com ",
>>>   "address": {
>>>   	"street":"XX,XX",
>>>   	"city":"SHENZHEN"
>>> 	  }
>>>   }
>>>  ```
>>>  
>> 
> 

Advantages
◉ Multiple design options
◉ Design for usage patterns
◉ Data model evolution is easy and intuitive
◉ Data model evolution is possible without downtime

Considerations
◉ Data model is defined at the application level.
◉ Design is an integral part of each phase of the
application's lifetime
◉ Data models are affected by:
◉ Changes in the application’s data needs
◉ Application read and write usage of data


# Data Modelling method
![](PICTURE/Data%20Modelling%20with%20MongoDB/40f93eba5dd89086dc9f720353d45f7d_MD5.jpeg)

![](PICTURE/Data%20Modelling%20with%20MongoDB/ef2570a20e9366c14307a1e847ea2b00_MD5.jpeg)










