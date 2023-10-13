Belge  yönelimli (document-oriented) bir NoSQL veritabanıdır.
MOngoDB' de her kayıt bir dökümandır.
Dökümanlar JSON benzeri Binary JSON(BSN) formatında saklanır. 

![MongoDB-1](https://github.com/Teknoloji-Filozofu/Big_Data/blob/main/_media/MongoDB-1.PNG)

![MongoDB-2](https://github.com/Teknoloji-Filozofu/Big_Data/blob/main/_media/MongoDB-2.PNG)

## Neden MongoDB 

### Ölçeklenebilir (Scalable)
Veri boyutu arttığı durumlarda veya performans sıkıntısı yaşdığımız durumlarda manine ekleyebiliriz. 
Veriler document ( belge ) biçiminde saklanır. Burada JSON verilerini kullanabiliriz. 
Verilerin birden fazla kopyası saklanabilr ve veri kaybı yaşanmaz.  (Replication)

Id bilgisi 
MongoDB üzerinde bir kayıt insert edilirken otomatik olarak ( _id ) isimli bir alan eklenir. Bu alan kullanıcı tarafından girilmezse, tekil (unique) bir değer ile kaydedilir.


![MongoDB-3](https://github.com/Teknoloji-Filozofu/Big_Data/blob/main/_media/MongoDB-3.PNG)