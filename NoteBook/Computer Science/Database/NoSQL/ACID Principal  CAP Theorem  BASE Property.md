---
aliases:
  - ACID Principal | CAP Theorem | BASE Property
LINK:
  - "[[Database]]"
  - "[[NoSQL]]"
  - "[[MongoDB]]"
tags: ""
---

## The ACID Principal

<font color="#ffc000">Atomicity, Consistency, Isolation, Durability </font>

![[PICTURE/ACID Principal  CAP Theorem  BASE Property/2aef421ff465df5415ca072618b1d207_MD5.jpeg]]






## The CAP Theorem

<font color="#ffc000">Consistency, Availability and Partition Tolerance</font>

![[PICTURE/ACID Principal  CAP Theorem  BASE Property/a9260b9586ba96124f4c3430df917fc7_MD5.jpeg]]

在计算机科学中, CAP定理（CAP theorem）, 又被称作 布鲁尔定理（Brewer's theorem）, 它指出对于一个分布式计算系统来说，不可能同时满足以下三点:

- **一致性(Consistency)** (所有节点在同一时间具有相同的数据)
- **可用性(Availability)** (保证每个请求不管成功或者失败都有响应)
- **分区容错性(Partition tolerance)** (系统中任意信息的丢失或失败不会影响系统的继续运作)

CAP理论的核心是：一个分布式系统不可能同时很好的满足一致性，可用性和分区容错性这三个需求，最多只能同时较好的满足两个。

因此，根据 CAP 原理将 NoSQL 数据库分成了满足 CA 原则、满足 CP 原则和满足 AP 原则三 大类：

- CA - 单点集群，满足一致性，可用性的系统，通常在可扩展性上不太强大。
- CP - 满足一致性，分区容忍性的系统，通常性能不是特别高。
- AP - 满足可用性，分区容忍性的系统，通常可能对一致性要求低一些。


## The BASE Property
<font color="#ffc000">Basically Available, Soft State, Eventual Consistency</font>

![[PICTURE/ACID Principal  CAP Theorem  BASE Property/13d208ac2375d3f6d5580937530a736e_MD5.jpeg]]

BASE：Basically Available, Soft-state, Eventually Consistent。 由 Eric Brewer 定义。

CAP理论的核心是：一个分布式系统不可能同时很好的满足一致性，可用性和分区容错性这三个需求，最多只能同时较好的满足两个。

BASE是NoSQL数据库通常对可用性及一致性的弱要求原则:

- Basically Available --基本可用
- Soft-state --软状态/柔性事务。 "Soft state" 可以理解为"无连接"的, 而 "Hard state" 是"面向连接"的
- Eventually Consistency -- 最终一致性， 也是 ACID 的最终目的。


## ACID vs BASE

| ACID                 | BASE                              |
| -------------------- | --------------------------------- |
| 原子性(**A**tomicity)   | 基本可用(**B**asically **A**vailable) |
| 一致性(**C**onsistency) | 软状态/柔性事务(**S**oft state)          |
| 隔离性(**I**solation)   | 最终一致性 (**E**ventual consistency)  |
| 持久性 (**D**urable)    |                                   |
