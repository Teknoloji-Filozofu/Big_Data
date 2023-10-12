Büyük veri kümelerini analiz etmek için MapReduce üzerinde bir soyutlama katmanı olarak kullanılan ve filtreleme, sıralama, yükleme ve birleştirme gibi işlevleri etkinleştiren bir araç.

![Pig]()

Apache Pig Avantajları ; 

- Öğrenmesi ve geliştirmesi basittir
- Büyük veriler üzerinde kolaylıkla analizler yapılabilir
- Yazdığınız kodları optimize eder 
- Veri üzerinde analizler yapabileceğimiz metodlar sunar (filter, join vs)
- İhtiyaç halinde javascript, java , python ile kütüphaneler yazıp apache pig içeriside kullanabiliriz.


### Pig Örnek Kodlar
Elimizdeki datanın yolunu ve biçimini belirterek (Data) içerisine atama gerçekleştirip, göstermek istediğimiz başlaıklar altında yazdırıyoruz.


```pig
Data = LOAD '/data/*' USING PigStorage(',') AS
(
userId : int,
movieId : int,
rating : double,
date : int
);
DUMP Data;
```
Örnek filtreleme işlemi gerçekleştirip farklı bir data ya atıp yazdırıyoruz

```pig
First = LOAD '/data/*' USING PigStorage(',') AS
(
userId : int,
movieId : int,
rating : double,
date : int
);
New_Data = FILTER First BY rating>3.0;
DUMP New_Data;
```
userId  200 eşit olan veriyi yazdırıyoruz

```pig
First = LOAD '/data/*' USING PigStorage(',') AS
(
userId : int,
movieId : int,
rating : double,
date : int
);
New_Data = FILTER First BY userId==200;
DUMP New_Data;
```

### Pig Operatörleri

![Pig-operatör]()

![Pig-operatör-2]()

veri içinde koltuk geçen veriyi alıyoruz.


```pig
Data = LOAD '/operatorexam/*' USING PigStorage(',') AS
(
userId : int,
country : chararray,
duration : int,
search : chararray
);
New_Data = FILTER Data BY(search matches '.*Koltuk.*');
DUMP New_Data;
```

3 saniyeden büyük Türkiye olan veriyi çekiyoruz

```pig
Data = LOAD '/operatorexam/*' USING PigStorage(',') AS
(
userId : int,
country : chararray,
duration : int,
search : chararray
);
New_Data = FILTER Data BY(country=='TR') AND (duration>3000);
DUMP New_Data;
```

![Pig-operatör-3]()

### Pig Fonksiyonlar 

![pig-fonksiyon]()

```pig
First = LOAD '/operatorexam/disteticaretlog' USING PigStorage(',') AS
(
userId : int,
country : chararray,
duration : int,
search : chararray
);
New_Data = DISTINCT First;
DUMP New_Data;
```

![pig-fonksiyon-2]()

![pig-fonksiyon-3]()

```pig
Data = LOAD '/operatorexam/eticaretlog' USING PigStorage(',') AS
(
userId : int,
country : chararray,
duration : int,
search : chararray
);
New_Data = GROUP Data BY country;
DUMP New_Data;
```

![pig-fonkisyonu-4]()

```pig
Data = LOAD '/operatorexam/eticaretlog' USING PigStorage(',') AS
(
userId : int,
country : chararray,
duration : int,
search : chararray
);
Gr_Data = GROUP Data BY country;

Result_Data = FOREACH Gr_Data{
	Generate
	group,
	AVG(Data.duration);
}
DUMP Result_Data;
```

![pig-fonksiyonu-5]()

```pig
Data = LOAD '/operatorexam/eticaretlog' USING PigStorage(',') AS
(
userId : int,
country : chararray,
duration : int,
search : chararray
);
Gr_Data = GROUP Data BY country;

New_Data = FOREACH Gr_Data{
	Generate
	group,
	MAX(Data.duration) as maxDurTime;
}
DUMP New_Data;
```

![pig-join]()

```pig
Personal = LOAD '/joinexam/Per' USING PigStorage(',') AS
(
name : chararray,
age : int,
dept_id : int
);
Departman = LOAD '/joinexam/Dept' USING PigStorage(',') AS
(
dept_id : int,
dept_name : chararray
);
New_Data = JOIN Personal BY dept_id,Departman BY dept_id;
DUMP New_Data;
```

![pig-left-join]()


```pig
Personal = LOAD '/joinexam/Per' USING PigStorage(',') AS
(
name : chararray,
age : int,
dept_id : int
);
Pay = LOAD '/joinexam/Pay' USING PigStorage(',') AS
(
name : chararray,
pay : int
);
New_Data = JOIN Personal BY name LEFT OUTER,Pay BY name;
DUMP New_Data;
```

![pig-right-join]()

```pig
Personal = LOAD '/joinexam/Per' USING PigStorage(',') AS
(
name : chararray,
age : int,
dept_id : int
);
Pay = LOAD '/joinexam/Pay' USING PigStorage(',') AS
(
name : chararray,
pay : int
);
New_Data = JOIN Personal BY name RIGHT OUTER,Pay BY name;
DUMP New_Data;
```

![pig-full-join]()

```pig
Personal = LOAD '/joinexam/Per' USING PigStorage(',') AS
(
name : chararray,
age : int,
dept_id : int
);
Pay = LOAD '/joinexam/Pay' USING PigStorage(',') AS
(
name : chararray,
pay : int
);
New_Data = JOIN Personal BY name FULL OUTER,Pay BY name;
DUMP New_Data;
```

![pig-unıon]()

```pig
Personal = LOAD '/joinexam/Per' USING PigStorage(',') AS
(
name : chararray,
age : int,
dept_id : int
);
New_Per = LOAD '/joinexam/New_Per' USING PigStorage(',') AS
(
name : chararray,
age : int
);
New_Data = UNION Personal,New_Per;
DUMP New_Data;
```
## Pig Depolama işlemleri

```pig
Personal = LOAD '/joinexam/Per' USING PigStorage(',') AS
(
name : chararray,
age : int,
dept_id : int
);
Departman = LOAD '/joinexam/Dept' USING PigStorage(',') AS
(
dept_id : int,
dept_name : chararray
);
New_Data = JOIN Personal BY dept_id,Departman BY dept_id;
DUMP New_Data;

STORE New_Data INTO '/joinexam/joinooutput' USING PigStorage(',');
```

