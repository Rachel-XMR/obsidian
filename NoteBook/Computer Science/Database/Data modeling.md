# **Data Models**

the concept of tools that are developed to summarize the description of the database为总结数据库描述而开发的工具的概念

数据模型为我们提供了透明的数据图片，帮助我们创建实际的数据库。它向我们展示了从数据的设计到数据的正确实现。

> 數據庫的類型是因為數據模型的不同

## Type of Relational Models

1. Conceptual Data Model 概念数据模型
2. Representational Data Model 代表性数据模型
3. Physical Data Model 物理数据模型

![](PICTURE/Data%20modeling/9d60585f4f83ba0892604bc9f78bc95c_MD5.jpeg)

### **Conceptual Data Model**

used in the requirement-gathering process. before the Database Designers start making a particular database. One such popular model is the [**entity/relationship model (ER model)**](https://www.geeksforgeeks.org/introduction-of-er-model/).

**Entity-Relationship Model:**

a high-level data model which is used to define the data and the relationships between them

1. [**Entity:**](https://www.geeksforgeeks.org/difference-between-entity-entity-set-and-entity-type/) An entity is referred to as a real-world object. It can be a name, place, object, class, etc. These are represented by a rectangle in an ER Diagram.实体被称为现实世界的对象。它可以是名称、地点、对象、类等。这些在 ER 图中用矩形表示。
2. [**Attributes:](https://www.geeksforgeeks.org/types-of-attributes-in-er-model/)** An attribute can be defined as the description of the entity. These are represented by Ellipse in an ER Diagram. It can be Age, Roll Number, or Marks for a Student.属性可以定义为实体的描述。这些在 ER 图中用椭圆表示。它可以是学生的年龄、学号或分数。
3. [**Relationship:](https://www.geeksforgeeks.org/relationships-in-er-model/)** Relationships are used to define relations among different entities. Diamonds and Rhombus are used to show Relationships.关系用于定义不同实体之间的关系。菱形和菱形用于表示关系。

![](PICTURE/Data%20modeling/87d77dd14092747bbb05ee7a26ba881b_MD5.jpeg)

![](PICTURE/Data%20modeling/4d95824eb9741e3a8fef982cd180509e_MD5.jpeg)

![](PICTURE/Data%20modeling/ca5fc324ee7e4b1e20e5b27fec4de29e_MD5.jpeg)

### Representational Data Model

This type of data model is used to represent only the **logical** part of the database and does not represent the physical structure of the database

Relational model is popular representational model

The relational Model consists of [**Relational Algebra**](https://www.geeksforgeeks.org/introduction-of-relational-algebra-in-dbms/) and [**Relational Calculus**](https://www.geeksforgeeks.org/tuple-relational-calculus-trc-in-dbms/).

### **Physical Data Model 物理數據模型**

The physical Data Model is used to practically implement Relational Data Model.

[**Structured Query Language (SQL)**](https://www.geeksforgeeks.org/structured-query-language/) is used to practically implement Relational Algebra.

该数据模型描述了**如何**使用特定的 DBMS 系统来实现系统。该模型通常由 DBA 和开发人员创建。目的是数据库的实际实现。

### **Terminologies**

- **Attribute 屬性:** Attributes are the properties that define an entity. e.g.; **ROLL_NO**, **NAME, ADDRES** 属性是定义实体的属性。例如;**卷号**、**名称、地址**
- **Relation Schema 關係模式:** A relation schema defines the structure of the relation and represents the name of the relation with its attributes. e.g.; STUDENT (ROLL_NO, NAME, ADDRESS, PHONE, and AGE) is the relation schema for STUDENT. If a schema has more than 1 relation, it is called Relational Schema.关系模式定义关系的结构并表示关系的名称及其属性。例如; STUDENT (ROLL_NO、NAME、ADDRESS、PHONE 和 AGE) 是 STUDENT 的关系模式。如果一个模式有超过 1 个关系，则称为关系模式。
- **Tuple 元組:** Each row in the relation is known as a tuple. The above relation contains 4 tuples, one of which is shown as: 关系中的每一行称为一个元组。上述关系包含4个元组

![](PICTURE/Data%20modeling/4e562de3980e95e0ea605bd3d65274f4_MD5.jpeg)

- **Relation Instance 關係實例:** The set of tuples of a relation at a particular instance of time is called a relation instance. Table 1 shows the relation instance of STUDENT at a particular time. It can change whenever there is an insertion, deletion, or update in the database.在特定时间实例的关系的元组集合称为关系实例。表1显示了特定时间STUDENT的关系实例。只要数据库中有插入、删除或更新，它就会发生变化。
- **Degree度:** The number of attributes in the relation is known as the degree of the relation. The **STUDENT** relation defined above has degree 5.关系中属性的数量称为关系的度。上面定义的**STUDENT**关系的阶数为 5。
- **Cardinality 基數:** The number of tuples in a relation is known as [**cardinality**](https://www.geeksforgeeks.org/cardinality-in-dbms/). The **STUDENT** relation defined above has cardinality 4. 关系中元组的数量称为[**基数**](https://www.geeksforgeeks.org/cardinality-in-dbms/)。上面定义的**STUDENT**关系的基数为 4。
- **Column:** The column represents the set of values for a particular attribute. The column **ROLL_NO** is extracted from the relation STUDENT.列表示特定属性的值集。 **ROLL_NO**列是从关系 STUDENT 中提取的。
- **NULL Values:** The value which is not known or unavailable is called a NULL value. It is represented by blank space. e.g.; PHONE of STUDENT having ROLL_NO 4 is NULL.未知或不可用的值称为 NULL 值。它由空格表示。例如; ROLL_NO 4 的学生的电话为 NULL。
- **Relation Key:** These are basically the keys that are used to identify the rows uniquely or also help in identifying tables. These are of the following types.这些基本上是用于唯一标识行或也有助于标识表的键。这些类型有以下几种。
    - [**Primary Key 主键**](https://www.geeksforgeeks.org/primary-key-constraint-in-sql/)
    - [**Candidate Key 候选键**](https://www.geeksforgeeks.org/difference-between-primary-and-candidate-key/)
    - [**Super Key 超级钥匙**](https://www.geeksforgeeks.org/difference-between-super-key-and-candidate-key/)
    - [**Foreign Key 外键**](https://www.geeksforgeeks.org/postgresql-foreign-key/)
    - [**Alternate Key 备用键**](https://www.geeksforgeeks.org/sql-alternate-key/)
    - [**Composite Key 复合键**](https://www.geeksforgeeks.org/composite-key-in-sql/)

### **Constraints in Relational Model**

在執行增刪操作之前會檢查約束，如果違反約束則會操作失敗

- **Domain Constraints 域约束**
    
    These are attribute-level constraints. An attribute can only take values that lie inside the domain range.這些是屬性級別的約束， 屬性只能採用域範圍內的值。
    
- **Key Integrity 关键完整性**
    
    Every relation in the database should have at least one set of attributes that defines a tuple uniquely. 数据库中的每个关系都应至少具有一组唯一定义元组的属性。这些属性集称为键。
    

## Con

- Data modeling is the process of developing data model for the data to be stored in a Database.数据建模是为要存储在数据库中的数据开发数据模型的过程。
- Data Models ensure consistency in naming conventions, default values, semantics, security while ensuring quality of the data.数据模型确保命名约定、默认值、语义、安全性的一致性，同时确保数据的质量。
- Data Model structure helps to define the relational tables, primary and foreign keys and stored procedures.数据模型结构有助于定义关系表、主键和外键以及存储过程。
- There are three types of conceptual, logical, and physical.可分为概念型、逻辑型和物理型三种。
- The main aim of conceptual model is to establish the entities, their attributes, and their relationships.概念模型的主要目的是建立实体、实体的属性及其关系。
- Logical data model defines the structure of the data elements and set the relationships between them.逻辑数据模型定义数据元素的结构并设置它们之间的关系。
- A Physical Data Model describes the database specific implementation of the data model.


![](PICTURE/Data%20modeling/47b16b86cbec4bda58ae719488bd2880_MD5.jpeg)


