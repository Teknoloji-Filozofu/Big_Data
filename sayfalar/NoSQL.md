# NoSQL
NoSQL karamı, yıllardır bilişim dünyasında vazgeçilmez bir yere sahip olan ilişkisel veritabanı sistemlerine (RDBMS) alternatif olarak çıkan, aslen internetin gün geçtikçe artan verisini depolayabilmek ve yüksek trafiğe sahip sistemlerin ihtiyaçlarına cevap verebilmek amacıyla ortaya çıkmış ölçeklendirilebilen sistemlere verilen genel addır.

- Document 
- Wide Column 
- Key Value
- Graph DB

## Document 
Document store tipinde ise veriler document (belge) şeklinde kaydedilir. Mesela bir json verisi document olarak kabul edilir.  (MongoDB - Elasticsearch)

![mongoDB](https://github.com/Teknoloji-Filozofu/Big_Data/blob/main/_media/mongoDB.PNG)

![elasticsearc](https://github.com/Teknoloji-Filozofu/Big_Data/blob/main/_media/elasticsearch.PNG)

## Wide Column
Buradaki yapı klasik veritabanına benzer. Tablolar, kolonlar ve satırlar vardır. En büyük farkı ise yapıyı belirlerken süper column olacak alanları belirleriz ve bu alanların altına her kayıt için farklı bir kolon gelebilir.  (Hadoop - HBase - Cassandra)

![HBase](https://github.com/Teknoloji-Filozofu/Big_Data/blob/main/_media/HBase.PNG)

![Hadoop](https://github.com/Teknoloji-Filozofu/Big_Data/blob/main/_media/Hadoop.PNG)

## Key Value
Bu yapıda her bir key karşılığında bir array yada veri yapısı bulunur. Amacımız key'ler üzerinden hızlı bir şekilde verilerie ulaşabilmektir. (Redis - DynamoDB)

![Key-Value](https://github.com/Teknoloji-Filozofu/Big_Data/blob/main/_media/Key-Value.PNG)

## Graph DB
Bu yapının genel amacı veriler arasındaki ilişkileri saklayabilmektir. Her bir veri birer node olabilir ve buradaki  asıl amacımız node'lar arasında ilişkileri yönleriyle beraber  tanımlayabilmektir. (Neo4j)

![Graph-DB](https://github.com/Teknoloji-Filozofu/Big_Data/blob/main/_media/Graph-DB.PNG)