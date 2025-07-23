---
LINK:
  - "[[Computer Science/Database/NoSQL/NoSQL]]"
  - "[[Database]]"
---

##  What is NoSQL

NoSQL database are *no-tabular非數據表格* database that store data differently than relational tables 其數據的存儲方式與關係型表格不同

Database that provide a *mechanism機制* for data storage *<font color="#ffff00">retrieval</font> <font color="#ffff00">檢索</font>* that is **modelled** in means other than the tabular relations used in relational databases 提供數據存儲和檢索機制的數據庫，其建模方式與關係數據庫中的表格關係不同

	
> [!info] Who use NoSQL Systems?
> Google, Amazon, Twitter, Facebook

> [!summary]+ 
> NoSQL is a type of<u> database management system (DBMS) </u>that is designed to <u>handle</u> and <u>store</u> large volumes of *unstructured and semi-structured* data. Unlike traditional relational databases that use tables with *pre-defined schemas預定義模式* to store data, NoSQL databases use flexible data models that can adapt to changes in **data structures** and are capable of scaling **horizontally** to handle <u>growing</u> amounts of data.



NoSQL databases are often used in applications where there is a<u> high volume</u> of data that needs to be <font color="#ffc000">processed and analyzed in real-time</font> 需要即時處理和分析大量data的應用程序, such as *social media analytics*, *e-commerce*, and gaming. They can also be used for other applications, such as content management systems, document management, and customer relationship management.

<font color="#ffc000">But may not provide the same level of data consistency and transactional guarantees 相同層級的data的一致性和事務保證</font>



NoSQL systems are also sometimes called <font color="#ffc000">Not only SQL</font> to emphasize the fact that they <font color="#ffc000">may support SQL-like query languages 他們可以支持類似sql的查詢語句</font>. A NoSQL database includes *simplicity of design*, *simpler horizontal scaling to clusters of machines簡單的機器業集水平擴展*, **has** and *finer control over availability對可用性的更精確控制*. <font color="#ffc000">The data structures used by NoSQL databases are different from those used by default in relational databases which makes some operations faster in NoSQL</font>. The suitability of a given NoSQL database depends on the problem it should solve

許多NoSQL存儲會為了可用性、速度和分割區容錯性而犧牲一致性。更廣泛的採用NoSQL存儲的障礙包括使用低階查詢語言、缺乏標準化界面以及先前對現有的關係式數據庫的巨額投資



Most NoSQL stores lack true ACID(Atomicity, Consistency, Isolation, Durability) transactions but a few databases, such as MarkLogic, Aerospike, FairCom c-treeACE, Google Spanner (though technically a NewSQL database), Symas LMDB, and OrientDB have made them central to their designs



## Why NoSQL

![[PICTURE/Introduction to NoSQL Systems/97e31769f680e40e03d8c3479f7f75fc_MD5.jpeg]]


NoSQL databases are often used in applications where there is a<u> high volume</u> of data that needs to be <font color="#ffc000">processed and analyzed in real-time</font> 需要即時處理和分析大量data的應用程序, such as *social media analytics*, *e-commerce*, and gaming. They can also be used for other applications, such as content management systems, document management, and customer relationship management.

<font color="#ffc000">But may not provide the same level of data consistency and transactional guarantees 相同層級的data的一致性和事務保證</font>



NoSQL systems are also sometimes called <font color="#ffc000">Not only SQL</font> to emphasize the fact that they <font color="#ffc000">may support SQL-like query languages 他們可以支持類似sql的查詢語句</font>. A NoSQL database includes *simplicity of design*, *simpler horizontal scaling to clusters of machines簡單的機器業集水平擴展*, **has** and *finer control over availability對可用性的更精確控制*. <font color="#ffc000">The data structures used by NoSQL databases are different from those used by default in relational databases which makes some operations faster in NoSQL</font>. The suitability of a given NoSQL database depends on the problem it should solve

許多NoSQL存儲會為了可用性、速度和分割區容錯性而犧牲一致性。更廣泛的採用NoSQL存儲的障礙包括使用低階查詢語言、缺乏標準化界面以及先前對現有的關係式數據庫的巨額投資

NoSQL databases are different from those used by default in relational databases which makes some operations faster in NoSQL. The suitability of a given NoSQL database depends on the problem it should solve. NoSQL 資料庫使用的資料結構與關聯式資料庫中預設使用的資料結構不同，這使得 NoSQL 中的某些操作更快。給定 NoSQL 資料庫的適用性取決於它要解決的問題


Most NoSQL stores lack true <font color="#ffc000">ACID (Atomicity, Consistency, Isolation, Durability)</font> transactions but a few databases, such as <u>MarkLogic, Aerospike, FairCom c-treeACE, Google Spanner</u> (though technically a NewSQL database), Symas LMDB, and OrientDB have made them central to their designs



#### Key Features

1. <font color="#ffc000">Dynamic schema動態模式</font>:  NoSQL databases do not have a <font color="#ffc000">fixed schema</font> and can accommodate changing data structures without the need for migrations or schema alterations.可以適應不斷變化的資料結構，而無需遷移或模式變更
2. <font color="#ffc000">Horizontal scalability水平可拓展性</font>：NoSQL databases are designed to scale out by adding more nodes to a database cluster, making them well-suited for handling large amounts of data and high levels of traffic.  NoSQL 資料庫旨在透過向資料庫叢集添加更多節點來進行橫向擴展，使其非常適合處理大量資料和高流量
3. <font color="#ffc000">Document-based基於文件</font>: Some NoSQL databases, such as MongoDB, use a document-based data model, where data is stored in a schema-less semi-structured format, such as JSON or BSON. 用基於文件的資料模型，其中資料以無模式的半結構化格式存儲，例如 JSON 或 BSON
4. <font color="#ffc000">Key-value-based基於鍵值</font>: Other NoSQL databases, such as Redis, use a key-value data model, where data is stored as a collection of key-value pairs. 使用鍵值資料模型，其中資料儲存為鍵值對的集合
5. <font color="#ffc000">Column-based基於列</font>: Some NoSQL databases, such as Cassandra, use a column-based data model, where data is organized into columns instead of rows. 使用基於列的資料模型，其中資料被組織為列而不是行
6. <font color="#ffc000">Distributed 分算式and high availablity高可用性</font>：NoSQL databases are often designed to be highly available and to automatically handle node failures and data replication across multiple nodes in a database cluster.自動處理資料庫叢集中多個節點的節點故障和資料複製
7. <font color="#ffc000">Flexibility靈活性</font>： NoSQL databases allow developers to store and retrieve data in a flexible and dynamic manner, with support for multiple data types and changing data structures. NoSQL 資料庫允許開發人員以靈活、動態的方式儲存和檢索數據，並支援多種資料類型和不斷變化的資料結構
8. <font color="#ffc000">Performance效能</font>：NoSQL databases are optimized for high performance and can handle a high volume of reads and writes, making them suitable for big data and real-time applications. 可以處理大量讀寫，適合大數據和即時應用程式


- Advantages of NoSQL： There are many advantages of working with NoSQL databases such as MongoDB and Cassandra. The main advantages are <font color="#ffc000">high scalability</font> and <font color="#ffc000">high availability</font>.
	1. <font color="#92d050">High scalability高可拓展性</font>: NoSQL databases use sharding for <font color="#d99694">horizontal scaling 水平拓展</font>. Partitioning區分 of data and placing it on multiple machines in such a way that the order of the data is preserved is sharding. Vertical scaling means adding more resources to the existing machine whereas horizontal scaling means adding more machines to handle the data. Vertical scaling is not that easy to implement but horizontal scaling is easy to implement. Examples of horizontal scaling databases are MongoDB, Cassandra, etc. NoSQL can handle a huge amount of data because of scalability, as the data grows NoSQL scales The auto itself to handle that data in an efficient manner.
	2. <font color="#92d050">Flexibility靈活性</font>：NoSQL databases are designed to handle unstructured or semi-structured data, which means that they can accommodate dynamic changes to the data model. This makes NoSQL databases a good fit for applications that need to handle changing data requirements.
	3. <font color="#92d050">High availability高可用性</font>：The auto, replication feature in NoSQL databases makes it highly available because in case of any failure data replicates itself to the previous consistent state.
	4. <font color="#92d050">Scalability可拓展性</font>：NoSQL databases are highly scalable, which means that they can handle large amounts of data and traffic with ease. This makes them a good fit for applications that need to handle large amounts of data or traffic
	5. <font color="#92d050">Performance效能</font>：NoSQL databases are designed to handle large amounts of data and traffic, which means that they can offer improved performance compared to traditional relational databases.
	6. <font color="#92d050">Cost-effectiveness成本效益</font>: NoSQL databases are often more cost-effective than traditional relational databases, as they are typically less complex and do not require expensive hardware or software.
	7. <font color="#92d050">Agility敏捷性</font>： Ideal for agile development.

- Disadvantages of NoSQL：
	1. <font color="#92d050">Lack of standardization缺乏標準化</font>：There are many different types of NoSQL databases, each with its own unique strengths and weaknesses. This lack of standardization can make it <font color="#ffc000">difficult to choose the right database for a specific application 很難為特定應用程序選擇正確的資料庫</font>. 
	2. <font color="#92d050">Lack of ACID compliance缺乏ACID合規性</font>：NoSQL databases are not fully ACID-compliant, which means that *they do not guarantee the consistency一致性, integrity完整性, and durability持久性 of data*. This can be a drawback for applications that require strong data consistency guarantees.
	3. <font color="#92d050">Narrow focus關注範圍狹窄</font>：NoSQL databases have a very narrow focus as it is mainly<font color="#ffc000"> designed for storage</font> but it provides very little functionality. Relational databases are a better choice in the field of Transaction Management than NoSQL.
	4. <font color="#92d050">Open-source</font>： NoSQL is an database open-source database. There is no reliable standard for NoSQL yet. In other words, two database systems are likely to be unequal.
	5. <font color="#92d050">Lack of support for complex queries缺乏對複雜查詢的支援</font>： *NoSQL databases are not designed to handle complex queries不是為複雜查詢而設計的*, which means that they are not a good fit for applications that require complex data analysis or reporting.
	6. <font color="#92d050">Lack of maturity缺少成熟度</font>： NoSQL databases are relatively new and lack the maturity of traditional relational databases. This can make them <u>less <font color="#ffc000">reliable</font> and less <font color="#ffc000">secure</font></u> than traditional databases.
	7. <font color="#92d050">Management challenge</font>： The purpose of big data tools is to make the management of a large amount of data as simple as possible. But it is not so easy. Data management in NoSQL is much more complex than in a relational database. NoSQL, in particular, has a reputation for being challenging to install and even more hectic to manage on a daily basis.
	8. <font color="#92d050">GUI is not available</font>： GUI mode tools to access the database are not flexibly available in the market.
	9. <font color="#92d050">Backup</font>： Backup is a great weak point for some NoSQL databases like MongoDB. MongoDB has no approach for the backup of data in a consistent manner.
	10. <font color="#92d050">Large document size</font>： Some database systems like MongoDB and CouchDB store data in JSON format. This means that documents are quite large (BigData, network bandwidth, speed), and having descriptive key names actually hurts since they increase the document size. 文件會非常大，並且具有描述性的鍵名稱實際上會造成傷害，因為它們會增加文件大小





### when choose NoSQL

1. When a huge amount of data needs to be stored and retrieved.  
    當需要儲存和檢索大量資料時。
2. The relationship between the data you store is not that important  
    你儲存的資料之間的關係就沒那麼重要
3. The data changes over time and is not structured.  
    數據隨著時間的推移而變化，並且不是結構化的。
4. Support of Constraints and Joins is not required at the database level  
    資料庫層級不需要支援約束和聯接
5. The data is growing continuously and you need to scale the database regularly to handle the data. 數據不斷增長，您需要定期擴展資料庫來處理數據





### RDBMS vs NoSQL
**RDBMS**  
- 高度组织化结构化数据  
- 结构化查询语言（SQL） (SQL)  
- 数据和关系都存储在单独的表中。  
- 数据操纵语言，数据定义语言  
- 严格的一致性  
- 基础事务

**NoSQL**  
- 代表着不仅仅是SQL  
- 没有声明性查询语言  
- 没有预定义的模式  
-键 - 值对存储，列存储，文档存储，图形数据库  
- 最终一致性，而非ACID属性  
- 非结构化和不可预知的数据  
- CAP定理  
- 高性能，高可用性和可伸缩性

![[PICTURE/Introduction to NoSQL Systems/1c323e8753b39fb6aa4688ac9b4564be_MD5.jpeg]]







### Emergence of NoSQL Systems

- The need by organizations to store vast amount of data, for example, emails, tweets, posts, updates, pictures, etc. 企業需要儲存大量數據
- SQL service *overload* <font color="#ffff00">服務超載</font>, such as powerful <font color="#ffc000">query language查詢</font>, <font color="#ffc000">concurrency control 並發控製</font>, which most of these applications do not need.
- Some of these organizations <font color="#ffc000">developed their own systems</font> referred to as NoSQL systems to <u>effectively manage</u> these vast amount of data.
	![[PICTURE/Introduction to NoSQL Systems/bbeba838249c000814fcf2775187106a_MD5.jpeg]]



## Categories of NoSQL Systems

![[PICTURE/Introduction to NoSQL Systems/cd690faeab5826937a50cf5e717314a3_MD5.jpeg]]
















### Key-value based NoSQL
<font color="#ffc000">These databases store data as key-value pairs, and are optimized for simple and fast read/write operations.</font> 針對快速的讀取/寫入操作進行了最佳化

> [!info] Examples
> Memcached, Redis, Coherence



### Document-based NoSQL
<font color="#ffc000">These databases store data as <i>semi-structured documents</i>, such as JSON or XML, and can be queried using document-oriented query languages.</font>

> [!info] Examples
> MongoDB, CouchDB, Cloudant




### Column-based NoSQL
These databases store data as <font color="#ffc000">column families</font>, which are sets of <u>columns that are treated as a single entity</u>. They are optimized for fast and efficient querying of large amounts of data.  他們針對快速有效低查詢大量資料進行了優化

> [!info] Examples
> Hbase, Big Table, Accumulo


### Graph-base NoSQL
These databases store data as *nodes and edges*, and are designed to <font color="#ffc000">handle complex relationships between data</font>.  旨在處理data之間的複雜關係

> [!info] Examples
> Amazon Neptune, Neo4j










