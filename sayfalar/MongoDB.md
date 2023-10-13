Belge  yönelimli (document-oriented) bir NoSQL veritabanıdır.
MOngoDB' de her kayıt bir dökümandır.
Dökümanlar JSON benzeri Binary JSON(BSN) formatında saklanır. 

![MongoDB-1]()

![MongoDB-2]()

## Neden MongoDB 

### Ölçeklenebilir (Scalable)
Veri boyutu arttığı durumlarda veya performans sıkıntısı yaşdığımız durumlarda manine ekleyebiliriz. 
Veriler document ( belge ) biçiminde saklanır. Burada JSON verilerini kullanabiliriz. 
Verilerin birden fazla kopyası saklanabilr ve veri kaybı yaşanmaz.  (Replication)

Id bilgisi 
MongoDB üzerinde bir kayıt insert edilirken otomatik olarak ( _id ) isimli bir alan eklenir. Bu alan kullanıcı tarafından girilmezse, tekil (unique) bir değer ile kaydedilir.


![MongoDB-3]()