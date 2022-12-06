# elasticsearch


## 索引管理

我找到的最新的官方文档（英文）：[链接](https://www.elastic.co/guide/en/elasticsearch/reference/7.7/indices.html)

索引类似于 MySQL 中的表，

### 创建索引

#### 基本使用

语法：`PUT /<index>`

index 就是索引名，，对于索引名，有以下限制

- 只能使用小写字母
- 不能使用这些字符 ``\``/``*``?``"``<``>``|``,``#``
- 不能以 ` - ` ` + ` `_` 开头
- 长度不能超过255个字节
- 冒号 `:` 在`7.0` 版本之前可以使用，`7.0` 版本之后就不能使用了

#### 请求体

请求体内支持这些参数

`aliases`：（可选）索引别名，类似与 MySQL 中的视图，将单独一章来写别名

`mappings`：（可选）映射对象，就相当于 MySQL 中的定义表结构，索引中字段的映射。此映射可以包括：
-   字段名称
-   字段数据类型]
-   映射参数

`settings`：可选，索引设置）配置 索引的选项。




## 查询

### 查询所有


```json
GET /bank/_search
{
  "query": { "match_all": {} },
  "sort": [
    { "account_number": "asc" }
  ]
}
```

`match_all`  表示查询所有的数据，`sort`  即按照什么字段排序

`match_all`没有限制条件，直接等同于`search`查询，匹配的所有文档的`_score`为1.0

默认情况下，会返回符合条件搜索的前 10 个文档

查询结果

```json
{
  "took": 1,
  "timed_out": false,
  "_shards": {
    "total": 1,
    "successful": 1,
    "skipped": 0,
    "failed": 0
  },
  "hits": {
    "total": {
      "value": 2000,
      "relation": "eq"
    },
    "max_score": null,
    "hits": [
      {
        "_index": "bank",
        "_id": "EuFjqYQBllHqfEttX2E-",
        "_score": null,
        "_source": {
          "account_number": 0,
          "balance": 16623,
          "firstname": "Bradshaw",
          "lastname": "Mckenzie",
          "age": 29,
          "gender": "F",
          "address": "244 Columbus Place",
          "employer": "Euron",
          "email": "bradshawmckenzie@euron.com",
          "city": "Hobucken",
          "state": "CO"
        },
        "sort": [
          0
        ]
      },
      {
        "_index": "bank",
        "_id": "YuFjqYQBllHqfEttX1w7",
        "_score": null,
        "_source": {
          "account_number": 1,
          "balance": 39225,
          "firstname": "Amber",
          "lastname": "Duke",
          "age": 32,
          "gender": "M",
          "address": "880 Holmes Lane",
          "employer": "Pyrami",
          "email": "amberduke@pyrami.com",
          "city": "Brogan",
          "state": "IL"
        },
        "sort": [
          1
        ]
      },
      {
        "_index": "bank",
        "_id": "8uFjqYQBllHqfEttX108",
        "_score": null,
        "_source": {
          "account_number": 2,
          "balance": 28838,
          "firstname": "Roberta",
          "lastname": "Bender",
          "age": 22,
          "gender": "F",
          "address": "560 Kingsway Place",
          "employer": "Chillium",
          "email": "robertabender@chillium.com",
          "city": "Bennett",
          "state": "LA"
        },
        "sort": [
          2
        ]
      },
      {
        "_index": "bank",
        "_id": "ouFjqYQBllHqfEttX2I-",
        "_score": null,
        "_source": {
          "account_number": 3,
          "balance": 44947,
          "firstname": "Levine",
          "lastname": "Burks",
          "age": 26,
          "gender": "F",
          "address": "328 Wilson Avenue",
          "employer": "Amtap",
          "email": "levineburks@amtap.com",
          "city": "Cochranville",
          "state": "HI"
        },
        "sort": [
          3
        ]
      },
      {
        "_index": "bank",
        "_id": "guFjqYQBllHqfEttX189",
        "_score": null,
        "_source": {
          "account_number": 4,
          "balance": 27658,
          "firstname": "Rodriquez",
          "lastname": "Flores",
          "age": 31,
          "gender": "F",
          "address": "986 Wyckoff Avenue",
          "employer": "Tourmania",
          "email": "rodriquezflores@tourmania.com",
          "city": "Eastvale",
          "state": "HI"
        },
        "sort": [
          4
        ]
      },
      {
        "_index": "bank",
        "_id": "FOFjqYQBllHqfEttX2E-",
        "_score": null,
        "_source": {
          "account_number": 5,
          "balance": 29342,
          "firstname": "Leola",
          "lastname": "Stewart",
          "age": 30,
          "gender": "F",
          "address": "311 Elm Place",
          "employer": "Diginetic",
          "email": "leolastewart@diginetic.com",
          "city": "Fairview",
          "state": "NJ"
        },
        "sort": [
          5
        ]
      },
      {
        "_index": "bank",
        "_id": "ZOFjqYQBllHqfEttX1w7",
        "_score": null,
        "_source": {
          "account_number": 6,
          "balance": 5686,
          "firstname": "Hattie",
          "lastname": "Bond",
          "age": 36,
          "gender": "M",
          "address": "671 Bristol Street",
          "employer": "Netagy",
          "email": "hattiebond@netagy.com",
          "city": "Dante",
          "state": "TN"
        },
        "sort": [
          6
        ]
      },
      {
        "_index": "bank",
        "_id": "9OFjqYQBllHqfEttX108",
        "_score": null,
        "_source": {
          "account_number": 7,
          "balance": 39121,
          "firstname": "Levy",
          "lastname": "Richard",
          "age": 22,
          "gender": "M",
          "address": "820 Logan Street",
          "employer": "Teraprene",
          "email": "levyrichard@teraprene.com",
          "city": "Shrewsbury",
          "state": "MO"
        },
        "sort": [
          7
        ]
      },
      {
        "_index": "bank",
        "_id": "pOFjqYQBllHqfEttX2I-",
        "_score": null,
        "_source": {
          "account_number": 8,
          "balance": 48868,
          "firstname": "Jan",
          "lastname": "Burns",
          "age": 35,
          "gender": "M",
          "address": "699 Visitation Place",
          "employer": "Glasstep",
          "email": "janburns@glasstep.com",
          "city": "Wakulla",
          "state": "AZ"
        },
        "sort": [
          8
        ]
      },
      {
        "_index": "bank",
        "_id": "hOFjqYQBllHqfEttX189",
        "_score": null,
        "_source": {
          "account_number": 9,
          "balance": 24776,
          "firstname": "Opal",
          "lastname": "Meadows",
          "age": 39,
          "gender": "M",
          "address": "963 Neptune Avenue",
          "employer": "Cedward",
          "email": "opalmeadows@cedward.com",
          "city": "Olney",
          "state": "OH"
        },
        "sort": [
          9
        ]
      }
    ]
  }
}
```

相关字段解释

-   `took` – Elasticsearch 运行查询所花费的时间（以毫秒为单位）
-   `timed_out` – 搜索请求是否超时
-   `_shards` - 搜索了多少分片，成功、失败或者跳过了多个分片（明细）
-   `max_score` – 找到的最相关文档的分数
-   `hits.total.value` - 找到的文档总数
-   `hits.sort` - 文档排序方式（如没有则按相关性分数排序）
-   `hits._score` - 文档的相关性得分（使用match_all时不适用）

可以使用 `boost` 参数来改变查询结果的加权数值（`_score`）

```json
GET /_search
{
    "query": {
        "match_all": { "boost" : 0.5 }
    }
}
```

还可以使用 `match_none`  来反选，`match_all` 是查询所有文档，`match_none`  就是匹配任何文档

### 全文查询

https://www.elastic.co/guide/en/elasticsearch/reference/6.0/full-text-queries.html

基于倒排索引算法，对text类型的字段进行分词检索

#### match

匹配查询接受文本/数字/日期，分析它们，并构建一个查询。



### 分页查询

```json
GET /bank/_search
{
  "query": { "match_all": {} },
  "from": 10,
  "size": 10
}
```

搜索第 10 到 19 的数据（从0开始），其中 `form` 是偏移量，`size` 是返回数据的条数

转换为 SQL 就是

`Select * From bank limit 10,10`




