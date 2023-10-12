Büyük veri kümelerini analiz etmek için MapReduce üzerinde bir soyutlama katmanı olarak kullanılan ve filtreleme, sıralama, yükleme ve birleştirme gibi işlevleri etkinleştiren bir araç.

![Pig](https://github.com/Teknoloji-Filozofu/Big_Data/blob/main/_media/Pig.PNG)

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

![Pig-operatör](https://github.com/Teknoloji-Filozofu/Big_Data/blob/main/_media/Pig-operat%C3%B6r.PNG)

![Pig-operatör-2](https://github.com/Teknoloji-Filozofu/Big_Data/blob/main/_media/Pig-operat%C3%B6r-2.PNG)

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

![Pig-operatör-3](https://github.com/Teknoloji-Filozofu/Big_Data/blob/main/_media/Pig-operat%C3%B6r-3.PNG)

### Pig Fonksiyonlar 

![pig-fonksiyon](https://github.com/Teknoloji-Filozofu/Big_Data/blob/main/_media/pig-fonksiyon.PNG)

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

![pig-fonksiyon-2](https://github.com/Teknoloji-Filozofu/Big_Data/blob/main/_media/pig-fonksiyon-2.PNG)

![pig-fonksiyon-3](https://github.com/Teknoloji-Filozofu/Big_Data/blob/main/_media/pig-fonksiyon-3.PNG)

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

![pig-fonkisyonu-4](https://github.com/Teknoloji-Filozofu/Big_Data/blob/main/_media/pig-fonksiyon-4.PNG)

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

![pig-fonksiyonu-5](https://github.com/Teknoloji-Filozofu/Big_Data/blob/main/_media/pig-fonksiyon-5.PNG)

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

![pig-join](https://github.com/Teknoloji-Filozofu/Big_Data/blob/main/_media/pig-join.PNG)

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

![pig-left-join](https://github.com/Teknoloji-Filozofu/Big_Data/blob/main/_media/pig-left-join.PNG)


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

![pig-right-join](https://github.com/Teknoloji-Filozofu/Big_Data/blob/main/_media/pig-right-join.PNG)

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

![pig-full-join](https://github.com/Teknoloji-Filozofu/Big_Data/blob/main/_media/pig-full-jo%C4%B1n.PNG)

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

![pig-unıon](https://github.com/Teknoloji-Filozofu/Big_Data/blob/main/_media/pig-un%C4%B1on.PNG)

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

