## سوال ۱ 
یک صف از سربازها را با رشته‌ای به طول دلخواه از کاراکتر‌های `>` و `<` نمایش می‌دهیم.
(استفاده از کاراکتر دیگری مجاز نیست!) این کاراکتر‌ها جهت هر سرباز 
 در صف را نشان می‌دهد که می‌تواند راست یا چپ باشد. بناست که هیچ دو نفری رو به روی هم
 نایستند. پس در هر مرحله افرادی که رو به روی هم باشند جهتشان را تغییر خواهند داد. 
 
*‌ تابع `update_queue(soldiers)` را بنویسید یه یک صف ورودی (از جنس `str`) دریافت می‌کند و 
 در خروجی حالت بعدی صف را بر‌می‌گرداند. 
 
 *‌ تابع `count_changes()` را بنویسید (در تعریف این تابع مجاز هستید از 
 قسمت قبلی استفاده کنید) که مجموع تمام حرکت هایی که در یک مرحله صورت گرفته را اعلام کند. مثلا برای ورودی (I) مرحله بعدی را (E) به دست میاوریم. مجموعا دو بار تغییر موقعیت داشته ایم(D): 
 
```
I: <<<<<<><<<<><<<<<
E: <<<<<<<><<<<><<<<
D:       ^^   ^^  
```

* پس از چند مرحله این صف دیگر تغییر نخواهد کحرد. به عبارتی هیچ دو نفری رو
به روی هم نخواهند بود. تابغی بنویسید که برای هر صف مراحل مورد نیاز برای همگرا شدن را return کند

*‌ تابعی بنویسید که مجموع تمام حرکت هایی که برای همگرا شدن یک صف ورودی لازم است را محاسبه کند 

*‌آیا می‌توان تابع های قسمت سوم و چهارم این سوال را به صورت بازگشتی نوشت؟ (در صورتی که جواب منفی است توضیخ دهید :)‌ ) 

## سوال ۲
تابعی بنویسید که متقارن بودن یک رشته را بررسی کند. خروجی از جنس `bool` باشد

## سوال ۳
تابعی بنویسید که رشته ای را در ورودی دریافت کن. سپس لیستی از تمام زیر-رشته 
های متقارن (با طول ۲ یا بیشتر) موجود در این رشته ورودی را return  کند 

*‌ تابعی بنویسید که بزرگترین زیر رشته متقارن را در یک رشته ورودی پیدا کند 


## سوال ۴
تابعی بنیویسید که برای هر رشته ورودی، بزرگترین زیر-رشته ای را پیدا کند 
که معکوس آن هم در خود رشته اصلی وجود داشته باشد. الزاما به صورت یک 
زیر رشته متقارن نخواهد بود. مثلا `abcde` و معکوسش یعنی `edcba` در رشته زیر 
وجود دارد و با وجود این‌که `xyz` و`zyx`  نیز در این رشته وجود دارد، به این دلیل که طولانی ترین
زیر رشته با شرایط گفته شده نیست، بنابرین جواب مساله `abcde` خواهد بود

```
uiabcdeioszyxjssqedcbadxyzops
  ^^^^^   ^^^    ^^^^^ ^^^ 
```

*‌ خروجی تابعی که نوشتید را برای متن ارایه شده در فایل `crypt.txt` را بررسی کنید.[crypt.txt](./crypt.txt)
