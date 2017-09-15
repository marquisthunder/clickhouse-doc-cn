# ClickHouse

![ClickHouse Logo](https://clickhouse.yandex/docs/en/single/_static/logo.svg) **ClickHouse一款性能强大的列式数据库**

+++

## ClickHouse. Just makes you think faster.
- <a href="http://clickhouse.yandex" target="_blank">Yandex</a>
- CERN
- Cloudflare

---

## 为OLAP而生
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

+++
典型的列式数据库有： **Vertica**, Paraccel (Actian Matrix) (Amazon Redshift), Sybase IQ, Exasol, Infobright, InfiniDB, MonetDB, LucidDB, SAP HANA, Google Dremel, Google PowerDrill, **Druid**, kdb+ 等。

---
## 数据库的3个层面
DBMS, 可以将DBMS分解为下面三部分：
- 数据库查询语言SQL
- 数据库范式 |
- 存储引擎 |

---
## OLAP数据库的对比
| |Druid | ElasticSearch | ClickHouse | Spark |
|--|--|--|--|--|
|query| json | sql like\n(no join) | sql\n(extended) | hive |
|schema| column\ninverted index | document\ninverted index | column\nindex | column |
|Data storage format|  segment | Internal storage, compressed | standalone | Parquet |
+++

![benchmark](https://www.percona.com/blog/wp-content/uploads/2017/02/spark_vs_clickhouse-1024x624.png)

---

## 高效率
**Real-Time Analytics: Immutable Past, Append-Only Future**

- 数据获取的场景是指请求如何发出，频率如何，比例如何。
- 每种请求有多少数据被读出，包括按行，按列，按字节数；
- 读取和更新数据之间的关系如何，活跃的数据有多大以及本地性如何；
- 是否使用了事务，以及是否独立；
- 对于数据持久性的要求如何，每种请求的延迟和吞吐量的要求如何等等。

---
## 高性能
**Partial Aggregates + In-Memory + Indexes => Fast Queries**
- MPP 数据库

- 基于主键的索引以及基于hash的sharding |

- partition,压缩,传输优化 |

---
## 可扩展
**Distributed Data + Parallelizable Queries => Horizontal Scalability**
- 分布式系统，针对小数据查询优化(hash join)

- sharding

- zookeeper for replication(replication/deduplication)

---
## 简洁, 开箱即用

- No Deps

- 安装扩容简单

- 已有工具

---

+++
# ClickHouse Adhoc

- JSONLine importer(jq)

- 自动分区

- 数据类型
  -  Array Join

---
难点:
- 数据管理

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

对于稳定的数据(normalized data)
- sql;
- web/app analytics;
- client tool