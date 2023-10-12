Hadoop, büyük veri kümeleri ile birden fazla makinada paralel olarak işlem yapmamızı sağlayan Java ile geliştirilmiş açık kaynak kodlu kütüphanedir.

Hadoop 4 modülden oluşur ;

- Hadoop Comman 
- HDFS ( Hadoop Distributed File System )                             
- Hadoop YARN
- Hadoop MapReduce    

![Hadoop-2](https://github.com/Teknoloji-Filozofu/Big_Data/blob/main/_media/Hadoop-2.PNG)

### Hadoop Comman 
Bazı modüllerin Hadoop'a erişebilmesi için gerekli olan bir kütüphane. Apache Pig veya Apache Hive ile HDFS'e veri yazıp okuma işlemleri yapmak için Hadoop Common kullanılır. 


### Hadoop YARN
Hadoop üzerinde çalışan uygulamaların kaynak yönetim platformu. Planlamayı ve kaynak yönetimini gerçekleştirir.

![Hadoop-5](https://github.com/Teknoloji-Filozofu/Big_Data/blob/main/_media/Hadoop-5.PNG)

### HDFS 
Hadoop ekosisteminin birincil bileşeni olan HDFS, bireysel Hadoop düğümlerinin kendi yerel depolarında bulunan veriler üzerinde çalıştığı dağıtılmış bir dosya sistemidir. Bu, uygulama verilerine yüksek verimli erişim sağlayarak ağ gecikmesini ortadan kaldırır. Ayrıca, yöneticilerin önceden şema tanımlamasına gerek yoktur.

![Hadoop-3](https://github.com/Teknoloji-Filozofu/Big_Data/blob/main/_media/Hadoop-3.PNG)

### Hadoop MapReduce 
MapReduce, büyük ölçekli veri işleme için bir programlama modelidir. MapReduce modelinde, daha büyük veri kümelerinin alt kümeleri ve alt kümeleri işlemeye yönelik talimatlar, birden çok farklı düğüme gönderilir; burada her bir alt küme, diğer işleme işleriyle paralel olarak bir düğüm tarafından işlenir. Sonuçları işledikten sonra, bireysel alt kümeler daha küçük, daha yönetilebilir bir veri kümesinde birleştirilir.

![Hadoop-4](https://github.com/Teknoloji-Filozofu/Big_Data/blob/main/_media/Hadoop-4.PNG)

## Hadoop Kurulum Modları 
Hadoop 3 farklı mod ile çalıştırılabilir. 

![Hadoop-6](https://github.com/Teknoloji-Filozofu/Big_Data/blob/main/_media/Hadoop-6.PNG)

## Hadoop Araçları 
Hadoop, çekirdek modülün yeteneklerini artırabilen ve genişletebilen geniş bir açık kaynak araçları ekosistemine sahiptir. Hadoop ile kullanılan ana yazılım araçlarından bazıları şunlardır:

### Apache Hive 
Hive ile büyük veriler üzerinde sql sorguları ile basit analizler yapmak için kullanılır.

Apache Hive kodlama adımları ; 

- Logları HDFS'e at 
> hdfs dfs -CopyFromLocal /Kaynak /Hedef

- Veritabanını oluştur 
```sql 
CREATE database My_Db;
```

- Tablo Oluştur 
```sql
CREATE EXTERNAL TABLE IF NOT EXISTS TableName(ColumnName : ColumnType,)
ROW FORMAT DELIMITED
FIELDS TERMINATED BY ','
LINES TERMİNATED BY '\n'
STORED AS TEXTFILE;
```

-  SQL Sorgusu Yaz 


- ### Apache HBase
Genellikle Hadoop ile eşleştirilmiş, açık kaynaklı, ilişkisel olmayan dağıtılmış bir veritabanı

### [Apache Pig](https://github.com/Teknoloji-Filozofu/Big_Data/blob/main/sayfalar/ApachePig.md)


### Apache Impala
Genellikle Hadoop ile kullanılan açık kaynak, büyük ölçüde paralel işleme SQL sorgu motoru*

### Apache Sqoop
Toplu verileri ilişkisel veritabanları ve Hadoop arasında verimli bir şekilde aktarmak için bir komut satırı arabirimi uygulaması

### Apache ZooKeeper
Hadoop'ta güvenilir dağıtılmış koordinasyon sağlayan açık kaynaklı bir sunucu; "yapılandırma bilgilerini koruma, adlandırma, dağıtılmış senkronizasyon sağlama ve grup hizmetleri sağlama" için bir hizmet

### Apache Oozie
Hadoop işleri için bir iş akışı zamanlayıcıs

## Hadoop Ekosistemi

![Hadoop-Ekosistem](https://github.com/Teknoloji-Filozofu/Big_Data/blob/main/_media/Hadoop-Ekosistem.png)