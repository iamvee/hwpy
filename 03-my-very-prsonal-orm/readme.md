# HW 4

`TOPIC: OOP, DB, Patterns`

# معرفی `sqlite3`


برای دسترسی به پایگاه داده sqlite در پایتون می‌توانیم از کتابخانه `sqlite3` استفاده کنیم. دستورات اصلی این کتابخانه به صورت خلاصه توضیح داده شده است: 

### `sqlite3.connect(database [,timeout ,other optional arguments])`

*  برای اتصال به دیتابیس
*  اگر به جای متغیر database از عبارت ":memory:" استفاده کنید، دیتابیس به جای هرد دیسک روی رم ذخیره سازی خواهد کرد.
*  اگر بدون اشکال بتواند به دیتابیس connect شود، شی connection را return می‌کند.
اگر دیتابیس توسط چند connection و به صورت هم‌زمان باز شده باشد: در صورتی که یکی از پروسه ها تغییراتی را اعمال کند، دیتابیس تا زمانی که transaction مربوطه کامیت نشود، دیتابیس lock می‌شود. 
*  timeout  مشخص می‌کند کاربر چه مدت زمانی را باید در حالت lock صبر کند 
*  اگر اسم دیتابیس وجود نداشته باشد، sqlite پایگاه داده مورد نظر را ایجاد می‌کند.


### `connection.execute(sql [, optional parameters])`

*  دستورات sql را اجرا می‌کند
*  می توان با پارامتر هایی که جداگانه تعریف می‌شوند، بخش هایی از رشته sql را کامل کرد. 

```python
cursor.execute("insert into people values (?, ?)", (who, age))
```

### `connection.executemany(sql[, parameters])`

*  چند دستور sql را هم‌زمان اجرا می‌کند. دستور ها با علامت `;`از هم جدا می‌شوند. 


### `connection.commit()`

* تغییرات را کامیت می‌کند.
* اگر از آخرین کامیت تا الان تغییراتی را بر روی دیتابیس اعمال کرده باشید، این تغییرات برای connection های دیگر قابل مشاهده نخواهد بود (تا زمانی که مجددا کامیت کنید) 

### `connection.close()`

*  ارتباط با دیتابیس را قطع می‌کند


# use it in python

## ایجاد کردن `TABLE`

دستور زیر را به وسیله `connection.execute`در پایتون اجرا می‌کنیم .

```sql
CREATE TABLE COMPANY
  (ID INT PRIMARY KEY     NOT NULL,
   NAME           TEXT    NOT NULL,
   AGE            INT     NOT NULL,
   ADDRESS        CHAR(50),
   SALARY         REAL);
```

```python
import sqlite3


conn = sqlite3.connect('test.db')
conn.execute('''CREATE TABLE COMPANY
         (ID INT PRIMARY KEY     NOT NULL,
         NAME           TEXT    NOT NULL,
         AGE            INT     NOT NULL,
         ADDRESS        CHAR(50),
         SALARY         REAL);''')
conn.close()
```

## افزودن رکورد جدید


```python
import sqlite3

conn = sqlite3.connect('test.db')
sql = "INSERT INTO COMPANY (ID,NAME,AGE,ADDRESS,SALARY) VALUES (?, ?, ?, ?, ?)"

conn.execute(sql, (1, 'Paul', 32, 'California', 20000.00 ))
conn.execute(sql, (2, 'Allen', 25, 'Texas', 15000.00 ))
conn.execute(sql, (3, 'Teddy', 23, 'Norway', 20000.00 ))
conn.execute(sql, (4, 'Mark', 25, 'Rich-Mond ', 65000.00 ))

conn.commit()
conn.close()
```


# سوالات!

### سوال ۱

*  کلاس DB را از طریق الکوی singleton بسازید به گونه ای که برای هر تعداد ورودی که `filename` یکسانی دارند، یک `connection‍‍` یکسان در اختیار داشته باشند. 

### سوال ۲

* هر کلاسی که از DB ارث‌بری می‌کند، به معنای یک جدول در دیتابیس است، بنابرین در صورتی که جدول قبلا ساخته نشده باید ایجاد شود. 

```python
class DB:
    def __new__(cls):
        pass

    def __init__(self, *args, **kw):
        pass
```

### سوال ۳

* هر کلاس تعدادی متغیر به صورت `class variable` تعریف می‌کند که نشان دهنده ستون‌های دیتابیس است. مقداد هر یک از این متغیر ها `data type` ستون نظیر در دیتا بیس خواهد بود. فرض کنید این مقدار به صورت رشته تعیین شود. 

هر کلاس به صورت پیش فرض یک ستون `id` در دیتابیس خواهد ساخت. 

راهنمایی: از `__dict__` کلاس استفاده کنید


```python

class Company(DB):
    name = "CHAR(40)"
    age = "INT"
    address = "CHAR(60)"
    salary = "REAL"
```

### سوال ۴

* هر کلاسی که از DB ارث بری کند، باید بتواند با همان `class variable` ها instantiate شود. ممکن است ترجیح دهید `__init__` را برای هر مورد جداگانه تعریف کنید یا کلاسی ایجاد کنید که `__init__` در آنجا پیاده سازی شده باشد و بتواند همه حالت ها را پوشش دهد . توجه کنید که instantiation باید به ایجاد ردیف جدیدی در دیتابیس نیز منجر شود. 


* اگر attributeی از یک instance تغییر کند، انتظار داریم دیتابیس فیلد مربوطه را آپدیت کند


* برای کلاس اصلی `DB` تابع `browse` تعریف کنید که در ورودی یک لیست از اعداد دریافت کند . این اعداد معرف `id` است. خروجی اجرای این متد(بستگی دارد که از کدام کلاس child) مورد استفاده قرار گیرد) شی‌هایی از همان کلاس خواهد بود که با مقادیر مشخص شده در رکورد نظیر خودشان در پایگاه داده instantiate شده‌اند. 
