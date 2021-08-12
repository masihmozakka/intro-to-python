<div dir="rtl">



# جلسه اول، روز ۱۴ مرداد



## معرفی کلاس

در این کلاس قصد داریم تا با زبان پایتون آشنا شویم. اگر می‌توانید این فایل را باز کنید پس احتمالا ادیتور شما به طور مناسبی کار می‌کند. در جلسه اول هدف ما آشنایی با ویژگی‌های اولیه زبان پایتون و انجام محاسبات ساده در آن است. معمولا برای یادگیری یک زبان برنامه‌نویسی جدید ابتدا برنامه موسوم به "Hello World" را در آن اجرا می‌کنند.

</div>


```python
print("Hello World")
```

<div dir="rtl">

تبریک! شما اولین برنامه پایتون خود را اجرا کردید. این برنامه بسیار به زبان محاوره‌ای نزدیک است و می‌توان کارکرد آن را راحت حدس زد. تابع print
یک رشته را دریافت کرده و آن را در کنسول چاپ می‌کند. در پایتون برخلاف زبان‌هایی مثل C
یا Java
نیازی به اضافه کردن ;
به آخر دستورات نیست. همچنین می‌توانید چند جمله را همزمان با هم چاپ کنید.
</div>


```python
print("hello world", "I live in Iran")
```

<div dir="rtl">

همانطور که در این مثال دیدید، در پایتون می‌توانیم با جداکننده ,
چندین پارامتر را همزمان به یک تابع بدهیم.
## متغیرها
در پایتون دو نوع متغیر بسیار متداول اعداد و رشته‌ها هستند. ابتدا با اعداد و اعمال اصلی آنها آشنا می‌شویم. یک متغیر در پایتون،‌ فارق از نوع، با استفاده از اپراتور =
تعریف می‌شود. همچنین، وقت خوبی است که با توضیحات یا comment
ها آشنا شویم. در پایتون هر خطی که با
\#
شروع شده باشد به عنوان یک comment
تفسیر شده و توسط برنامه اجرا نخواهد شد. این توضیحات به برنامه‌نویس کمک می‌کنند تا برنامه را برای خود و بقیه خواناتر کند و استفاده از آنها بسیار توصیه می‌شود. همچنین برای توضیحات بیشتر از یک خط می‌توان از سه کوتیشن پشت سر هم استفاده کرد.
</div>


```python
"""

This is a multiline comment, in this cell we will explore numerical types in python.

Proper comments can help make your code easier to read.

سلام، می توانید فارسی هم بنویسید ولی استاندارد برنامه نویسان همان انگلیسی است.

"""

# integer.

x = 5

# float.

y = 10.1

# floats can also be written as a * 10^b using a e b.

y = 1.01e1

# 0x defines a hexadecimal number. 0xff = (f=15)*16^1 + (f=15)*16^0 = 255.

z = 0xff

# 0b defines a binary number, 0b100010 = 2 + 2^5 = 34.

w = 0b100010

# in python we have j = sqrt(-1) and we can define complex numbers.

v = 1 + 2j

print(x, y, z, w, v)
```

    5 10.1 255 34 (1+2j)
    

<div dir="rtl">



دقت کنید که در پایتون، فضای خالی بین دستورات یا white space

معنای خاصی دارد و پایتون با استفاده از میزان تو رفتگی یا indentation

تعیین می‌کند که هر دستور زیر مجموعه کدام حلقه است. همچنین می‌توانید با استفاده از تابع type

نوع یک داده را مشاهده کنید.

</div>


```python
print(type(z), type(y), type(v))
```

    <class 'int'> <class 'float'> <class 'complex'>
    

<div dir="rtl">



در پایتون نام متغیرها می‌تواند از حروف انگلیسی، اعداد و _ تشکیل شود. همچنین نام یک متغیر نمی‌تواند با عدد شروع شود.

</div>


```python
correct_variable_1 = 1

_thisIsStillCorrect = 2

#but this is not correct: 1seconds = 1



#constant variables are written in all caps

CONSTANT_VARIABLE = 3



#python is case sensitive

Age = 4

age = 5
```

<div dir="rtl">

### نکته
در پایتون می‌توان با استفاده از `x-`
متغیر x را قرینه کرد.
</div>


```python
x = 5

print(-x)
```

    -5
    

<div dir="rtl">

تمامی اعمال متداول را می‌توان بر روی اعداد انجام داد. 
‍</div>


```python
x = 17

y = 6



# Output: x + y = 23

print("x + y =", x+y)



# Output: x - y = 11

print('x - y =',x-y)



# Output: x * y = 102

print('x * y =',x*y)



# Output: x / y = 2.833...

print('x / y =',x/y)



# Output: x // y = 2, floor division is essentially floor(x/y).

print('x // y =',x//y)



# Output: x ** y = 24137569

print('x ** y =',x**y)



# Output: x % y = 5

print('x % y =', x % y)
```

    x + y = 23
    x - y = 11
    x * y = 102
    x / y = 2.8333333333333335
    x // y = 2
    x ** y = 24137569
    x % y = 5
    

<div dir="rtl">

### نکته
هیچ اشکالی ندارد که موقع **فراخواندن**
یک تابع محاسبات انجام دهیم.
</div>


```python
x = 5

y = 10

print(2*x - x**y)
```

    -9765615
    

<div dir="rtl">



### نکته

در محاسبه عبارات ریاضی می‌توان اولویت را با استفاده از پرانتز مشخص کرد. در زبان پایتون اپراتورها (همانند قواعد ریاضی که ضرب اولویت بالاتری نسبت به جمع دارد) هر کدام با اولویت خاصی محاسبه می‌شوند، جدول زیر اولویت‌های اپراتورهایی که تا به حال با آنان آنشا شدیم را نشان می‌دهد. پرانتز بالاترین اولویت را دارد.

</div>


| Operator        | Description          |
| :-------------: |:-------------:|
| `()`      | 	Parentheses |
| `**`      | Exponentiation      |
| `+x, -x` | Sign of Number      |
|`*, /, %`  | Multiplication, division, remainder|
|`+, -`| Addition and Subtraction|

<div dir="rtl">

همچنین می‌توان با انواع اعداد مختلف کار کرد و پایتون در صورت امکان انجام آن عمل، جواب درست را خواهد داد.
</div>


```python
x = 1.23

y = 5

z = 1 + 2j



print(x*z, y**x, z - x)
```

    (1.23+2.46j) 7.239908964061694 (-0.22999999999999998+2j)
    

<div dir="rtl">

### نکته
می‌توانید یک مقدار را به دو یا چند متغیر به شکل همزمان دهید، به صورت زیر.
</div>


```python
x = y = z = 5

print(x, y, z)
```

    5 5 5
    

<div dir="rtl">

## ورودی کاربر

بسیاری از برنامه‌ها نیاز دارند تا با کاربر در ارتباط باشند. تا به حال یاد گرفتیم که چگونه با استفاده از تابع
print
از برنامه خروجی‌ها را نمایش دهیم، حال می‌بینیم که با تابع input
می‌توانیم از کاربر اطلاعات مورد نیاز را دریافت کنیم.
</div>


```python
# usage is x = input("optional user prompt").

n = input("please provide a number")

print(n)
```

    hello worldhello worldhello worldhello worldhello world
    

<div dir="rtl">

## Casting and Strings
اگر کد سلول قبلی را برداشته و سعی کنیم عبارت
</div>

$$2n$$
<div dir="rtl">

را محاسبه کنیم نتیجه مورد انتظار خود را نخواهیم گرفت. خواهیم دید که به جای محاسبه عبارت بالا، خود عدد دوبار پشت سر هم چاپ می‌شود. این به این دلیل است که تابع 
input
ورودی را به عنوان یک رشته یا
string
در n
ذخیره می‌کند. 

رشته‌ها عباراتی هستند که از **پشت سر هم چیدن** کاراکترها ساخته می‌شوند. در پایتون، رشته‌ها به صورت
"&lt;string&gt;"
 تعریف می‌شوند. همچنین می‌توان از '&lt;string&gt;' نیز برای تعریف کردن آنها استفاده کرد. دلیل اینکه ارقام n
را دو بار پشت سر هم می‌بینیم این است که اپراتور *
که برای اعداد مفهوم ضرب را داشت، برای رشته‌ها نیز مفهوم خاص خودش را دارد. هر وقت که یک عدد را در یک رشته ‍‍«ضرب» کنیم در واقع آن رشته را به تعداد آن عدد پشت سر هم تکرار کرده‌ایم. این یکی از ویژگی‌های مهم زبان سطح بالایی مانند پایتون را نشان می‌دهد. به جای اینکه برای مفهوم چند بار نوشتن یک رشته یک اپراتور جدید تعریف کنیم، از یک اپراتور موجود استفاده می‌کنیم و برنامه خود با استفاده از تعاریفی که در اختیار دارد تشخیص می‌دهد که باید از کدام مفهوم ضرب استفاده کند. اگر دو عدد را ببیند به سراغ ضرب اعداد خواهد رفت و اگر یک رشته و یک عدد را ببیند از مفهوم چند بار تکرار کردن استفاده خواهد کرد.
تکنیک casting
برای تبدیل انواع داده به یکدیگر استفاده می‌شود. هر نوع داده در پایتون یک تابع خاص دارد که به سازنده یا
constructor
معروف است. این تابع ورودی خود را تبدیل به داده‌ای از نوع دیگر می‌کند. این تکنیک بسیار کاربردی‌ای است و برای مشاهده استفاده آن مثال بالا را تصحیح می‌کنیم:
</div>



```python
n = input("please provide a number")



#this will not work as intended

print(2*n)



#we will cast n from a string to an integer

n = int(n)



#now this should work as planned

print(2*n)
```

    55
    10
    

<div dir="rtl">

### نکته
مثال‌های متداول دیگری از کستینگ استفاده از 
()str
برای تبدیل داده به نوع رشته و
()float
برای تبدیل داده به عدد اعشاری می‌باشند.
</div>


```python
#also notice that as we explained, throughout this code the meaning of the * operator changes depending on the context,

#this is an example of the property of "polymorphism" which we will learn more about later.

n = 5



#as int

print(2*n)



#as string

print(2*str(n))



#an answer of 10.0 instead of 10 reminds us that the resulting number is a float and not an int

print(2*float(n))
```

    10
    55
    10.0
    

<div dir="rtl">

### نکته
دقت کنید که موقع cast
از یک عدد اعشاری به یک عدد صحیح، قسمت اعشاری عدد از دست می‌رود. موقع cast
کردن باید دقت کنید که نوع داده هدف شما چه اطلاعاتی را می‌تواند نگه دارد و آیا این تغییر مناسب برنامه
شما می‌باشد.
</div>


```python
n = 15.4

print(int(n))
```

    15
    

<div dir="rtl">





### نکته

اگر تلاش کنید از یک رشته‌ای که به صورت عدد اعشاری است به یک عدد صحیح بروید برنامه خطا خواهد داد چون تابع 
```()int```
یا ورودی 
```float```
قبول خواهد کرد یا
یک عدد صحیح به فرم رشته مانند
"56".
دانستن اینکه تابع شما چه مقادیری را قبول می‌کند و خروجی آن به چه صورتی خواهد بود بسیار مهم است و در خیلی از مواقع نیاز دارید تا با مراجعه به منابع موجود، اطلاعات مربوط به کدی که می‌نویسید را پیدا کنید. به عنوان مثال اینجانب موقع تدوین تمارین این درس بعد از خوردن به همین مشکل با سرچ در اینترنت و پیدا کردن
[این جواب](https://stackoverflow.com/questions/27048627/how-to-convert-a-float-string-to-an-integer-in-python-3)
متوجه خطای کد زیر شدم. سایت استک اوورفلو یکی از کاربردی ترین سایت‌های مورد استفاده یک برنامه نویس می‌باشد.


</div>


```python
n = "1.2"

n = float(n)

print(int(n))
```

    1
    

<div dir="rtl">

### مثال
با اطلاعاتی که تا الان یاد گرفتیم می‌توانیم یک برنامه بسیار ساده بنویسیم، این برنامه ابتدا سه عدد 
n, a, b
را دریافت کرده و سپس عبارت زیر را محاسبه و چاپ می‌کند:
</div>

<a href="https://www.codecogs.com/eqnedit.php?latex=\huge&space;x&space;=&space;a^b\bmod&space;n" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\huge&space;x&space;=&space;a^b\bmod&space;n" title="\huge x = a^b\bmod n" /></a>

<div dir="rtl">

محاسبه عباراتی ازین دست در رمزنگاری بسیار کاربرد دارد.
</div>


```python
n = int(input("please enter n:"))

a = int(input("now enter a:"))

b = int(input("now enter b:"))



x = a**b % n

print("a, b, and n in order:")

print(a, b, n)

print("this is a to the power of b:")

print(a**b)

print("this is the result:")

print(x)
```

    a, b, and n in order:
    7 9 11
    this is a to the power of b:
    40353607
    this is the result:
    8
    


