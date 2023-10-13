Apache Kafka  genellikle gerçek zamanlı projelerde kullanılır. Verilerin analizi için veriler kafka'ya ordan analiz aracına iletilir. Kafka bir kuyruk mekanizması kullanılır. Yani ilk giren ilk çıkar mantığı vardır.  Analiz bölümünün çökmesi ile gelen verilerin işlenmeden kaybolmaması için kafka kullanılır. Gelen verileri kafka depolar ve analiz kısmı ayağa kalkdığında, verlileri oradan çeker. 

![apache_kafka]()

Kafka da verileri gönderen ( Producer ) kısmı, verileri depolayan ( Topic ) kısmı ve verileri çeken ( Consumer ) kısmı yer almakta.

![kafka]()

Kafka da dağıtık veri depolama ve replication mevcuttur.

![kafka2]()

Veriler ( broker ) adlı yerde tutulurken her verinin kopyası diğer cihazda da yer almakta. Bu şeklde çökme durumunda veri kaybı yaşanmamakta.