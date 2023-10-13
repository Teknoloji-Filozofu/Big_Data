Apache Kafka  genellikle gerçek zamanlı projelerde kullanılır. Verilerin analizi için veriler kafka'ya ordan analiz aracına iletilir. Kafka bir kuyruk mekanizması kullanılır. Yani ilk giren ilk çıkar mantığı vardır.  Analiz bölümünün çökmesi ile gelen verilerin işlenmeden kaybolmaması için kafka kullanılır. Gelen verileri kafka depolar ve analiz kısmı ayağa kalkdığında, verlileri oradan çeker. 

![apache_kafka](https://github.com/Teknoloji-Filozofu/Big_Data/blob/main/_media/apache_kafka.PNG)

Kafka da verileri gönderen ( Producer ) kısmı, verileri depolayan ( Topic ) kısmı ve verileri çeken ( Consumer ) kısmı yer almakta.

![kafka](https://github.com/Teknoloji-Filozofu/Big_Data/blob/main/_media/kafka.PNG)

Kafka da dağıtık veri depolama ve replication mevcuttur.

![kafka2](https://github.com/Teknoloji-Filozofu/Big_Data/blob/main/_media/kafka2.PNG)

Veriler ( broker ) adlı yerde tutulurken her verinin kopyası diğer cihazda da yer almakta. Bu şeklde çökme durumunda veri kaybı yaşanmamakta.