# ClickHouse Intro

![ClickHouse Logo](https://clickhouse.yandex/docs/en/single/_static/logo.svg) **ClickHouse一款性能强大的列式数据库**

+++

<a href="http://clickhouse.yandex" target="_blank">Yandex</a>
Catboost

---

# 为OLAP而生
在通常的面向行的数据库中，数据是按照这样的顺序存储：
<pre> 
5123456789123456789     1       Eurobasket - Greece - Bosnia and Herzegovina - example.com      1       2011-09-01 01:03:02     6274717   1294101174      11409   612345678912345678      0       33      6       http://www.example.com/basketball/team/123/match/456789.html http://www.example.com/basketball/team/123/match/987654.html       0       1366    768     32      10      3183      0       0       13      0\0     1       1       0       0                       2011142 -1      0               0       01321     613     660     2011-09-01 08:01:17     0       0       0       0       utf-8   1466    0       0       0       5678901234567890123               277789954       0       0       0       0       0
5234985259563631958     0       Consulting, Tax assessment, Accounting, Law       1       2011-09-01 01:03:02     6320881   2111222333      213     6458937489576391093     0       3       2       http://www.example.ru/         0       800     600       16      10      2       153.1   0       0       10      63      1       1       0       0                       2111678 000       0       588     368     240     2011-09-01 01:03:17     4       0       60310   0       windows-1251    1466    0       000               778899001       0       0       0       0       0
...
</pre>
MySQL，Postgres,SQL Server等都是典型的行式数据库。
在列式数据库中，数据是这样存储的：
<pre class="text-example" style="white-space: pre; ">
<b>WatchID:</b>    5385521489354350662     5385521490329509958     5385521489953706054     5385521490476781638     5385521490583269446     5385521490218868806     5385521491437850694   5385521491090174022      5385521490792669254     5385521490420695110     5385521491532181574     5385521491559694406     5385521491459625030     5385521492275175494   5385521492781318214      5385521492710027334     5385521492955615302     5385521493708759110     5385521494506434630     5385521493104611398
<b>JavaEnable:</b> 1       0       1       0       0       0       1       0       1       1       1       1       1       1       0       1       0       0       1       1
<b>Title:</b>      Yandex  Announcements - Investor Relations - Yandex     Yandex — Contact us — Moscow    Yandex — Mission        Ru      Yandex — History — History of Yandex    Yandex Financial Releases - Investor Relations - Yandex Yandex — Locations      Yandex Board of Directors - Corporate Governance - Yandex       Yandex — Technologies
<b>GoodEvent:</b>  1       1       1       1       1       1       1       1       1       1       1       1       1       1       1       1       1       1       1       1
<b>EventTime:</b>  2016-05-18 05:19:20     2016-05-18 08:10:20     2016-05-18 07:38:00     2016-05-18 01:13:08     2016-05-18 00:04:06     2016-05-18 04:21:30     2016-05-18 00:34:16     2016-05-18 07:35:49     2016-05-18 11:41:59     2016-05-18 01:13:32
...
</pre>

这些例子仅仅是用来展示数据是怎样排布的。
+++
典型的列式数据库有： **Vertica**, Paraccel (Actian Matrix) (Amazon Redshift), Sybase IQ, Exasol, Infobright, InfiniDB, MonetDB (VectorWise) (Actian Vector), LucidDB, SAP HANA, Google Dremel, Google PowerDrill, **Druid**, kdb+ 等。

+++

+++
## OLAP数据库的对比

Druid    ClickHouse    ElasticSearch


---
## 数据库的3个层面
DBMS, 可以将DBMS分解为下面三部分：

- 一种数据库查询语言SQL
- 一系列数据库范式 |
- 存储引擎 |


## 简洁, 开箱即用

No Deps
---

## 高效率
不同的存储方式会适应不同的场景。数据获取的场景是指请求如何发出，频率如何，比例如何。每种请求有多少数据被读出，包括按行，按列，按字节数；读取和更新数据之间的关系如何，活跃的数据有多大以及本地性如何；是否使用了事务，以及是否独立；对于数据持久性的要求如何，每种请求的延迟和吞吐量的要求如何等等。
+++


## 高性能
- MPP 数据库

- Erlang运行时在CPU中的所有核心都在开动。当像Parallel这种技术变得更容易获取且成本更低廉时，你很难忽视Erlang VM所能提供的强大能力。未来Erlang VM将会被用来搭建能永久运行、能自我修复和扩展的系统。 |

- 效率很难测量，能高效开发桌面应用的编程语言却可能在数学运算领域捉襟见肘，它与你期望从事的领域、生态圈中的可用工具，以及是否能方便地创造和扩展这些工具有关。 |

---
## 可扩展
- 分布式系统，以一种很直接的方式表达的情况下才合理。

- 基于简洁的语言核心，开发者可以构建和扩展针对自己领域的语言。 

+++
# ClickHouse Adhoc

- JSON Line importer

- 管理
  - property testing

- 数据类型
  -  Array Join

- 自动分区

---
# ClickHouse Ecosys

- tabiX(http://adhochouse.creditx.cc:3080)
- Superset
- altinity(public cloud)
   - ops(prometheus, graphana)
   - data ingestion

+++

---
# 如何选择

对于稳定的数据(cleaned data)
- sql;
- web/app analytics;
- client tool

---
