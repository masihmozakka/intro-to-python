<div dir="rtl">

# جلسه چهارم، ۲۲ مرداد
در این جلسه، قصد داریم تا مطالب مقدماتی پایتون را کامل کرده و آماده شویم تا در هفته‌های دیگر،‌ به مباحث پیشرفته بپردازیم.
</div>

<div dir="rtl">

## مجموعه‌ها
تا اینجای کار، ۳ روش درست کردن کلکسیونی از متغیرها را دیدیم. لیست‌ها، دیکشنری‌ها و تاپل‌ها. حال قصد داریم تا با مجموعه‌ها آشنا شویم. مجموعه‌ها در پایتون، همانند مجموعه‌ها در ریاضیات هستند. کلکسیونی **بدون ترتیب** از داده‌ها که **عضوهای تکراری نمی‌پذیرد** و نمی‌توان آن را تغییر داد.
</div>


```python
# sets are written like dictionaries, but we don't have key-value pairs.

myset = {"abc", 34, True, 40, "male"}
print(myset)
```


```python
# you cannot access the members of a set directly, you should use a for loop instead
thisset = {"apple", "banana", "cherry"}

for x in thisset:
  print(x)
```


```python
# you cannot change members of sets, you can only add more or delete some.

thisset = {"apple", "banana", "cherry"}

thisset.add("orange")

print(thisset)

thisset.discard("banana")
thisset.add("orange")
print(thisset)
```

<div dir="rtl">

مجموعه‌ها توابعی که دارند بسیار به اعمال مجموعه‌ای متداول در ریاضیات شبیه هستند. به عنوان مثال تابع 
```difference```
عبارت $A-B$ که در ریاضیات آن را به عنوان تفاضل دو تابع می‌شناسیم برمی‌گرداند
یا تابع 
``symmetric_difference``
مقدار $A\Delta B$
یا تفاضل متقارن را برمی‌گرداند.
</div>



<div dir="rtl">

## چرا مجموعه‌ها؟‌ بهینه‌سازی در برنامه‌نویسی
به عنوان یک برنامه‌نویس شما باید سعی کنید تا بهترین و سریع‌ترین کد ممکن را بنویسید.

بدین منظور، از یک معیار به نام اُو بزرگ استفاده می‌شود. این معیار به ما کمک می‌کند تا زمان اجرای برنامه خود را تخمین بزنیم. به طور عامیانه، یک برنامه
$O(N)$
است اگر همیشه (همیشه به معنای متغیر بودن بر روی تعداد داده‌های ورودی به برنامه) به حدودا $N$
مرحله محاسبه نیاز باشد. این مقدار متغیر هم می‌تواند باشد. به عنوان مثال، یک حلقه فور که $n$
بار تکرار دارد، حدودا مرحله اجرا نیاز خواهد داشت. ولی، یک تابع که صرفا یک عدد را دو برابر کرده و بر می‌گرداند $O(1)$
است چون یک مرحله محاسبه بیشتر ندارد.

برای درک بهتر،‌ به مثال رو به رو دقت کنید:‌ این برنامه $n$
عدد گرفته و بیشترین آنها را برمی‌گرداند.
</div>


```python
n = input()
l = []

for i in range(0, n):
    l.append(float(input()))

# max checks every element and then returns the maximum, so, it takes O(n) steps
print(max(l))
```

<div dir="rtl">

### مثال
برنامه‌ای بنویسید که جمع n عدد طبیعی اول را بدست آورد.
</div>


```python
# method 1, O(n)

n = 1000000000
sum_of_n = 0
for i in range(1, n+1):
    sum_of_n += i

print(sum_of_n)
```


    ---------------------------------------------------------------------------

    KeyboardInterrupt                         Traceback (most recent call last)

    ~\AppData\Local\Temp/ipykernel_9544/2626985158.py in <module>
          4 sum_of_n = 0
          5 for i in range(1, n+1):
    ----> 6     sum_of_n += i
          7 
          8 print(sum_of_n)
    

    KeyboardInterrupt: 



```python
# method 2, O(1)

def sum_of_n(x):
    return int(x*(x+1)/2)
n = 1000000000
print(sum_of_n(n))
```

    500000000500000000
    

<div dir="rtl">

## توابع لاندا
با معلوماتی که داریم، اگر بخواهیم یک تابعی بنویسیم که یک عدد را گرفته و دوبرابر آن بعلاوه ۳ را برگرداند، باید بنویسیم:
</div>


```python
def func(x):
    return 2*x + 3
print(func(5))
```

    13
    

<div dir="rtl">

ولی یک راه سریع تر هم هست، در پایتون، هر جا نیاز داشتیم تا صرفا یک خط کد را تبدیل به یک تابع کوچک کنیم، می‌توانیم از توابع لاندا استفاده کنیم.
</div>


```python
x = lambda a,b : 2*a*b + 3
print(x(5, 6))
```

    63
    

<div dir="rtl">

یک مثال از کاربرد توابع لاندا وقتی است که بخواهید یک عبارت ریاضی را چند بار استفاده کنید. مثلا اگر بخواهید تابعی داشته باشید که یک عدد را چند برابر کند، ولی نمی‌خواهید که هر دفعه یک تابع جدید بنویسید یا پارامتر جدیدی را وارد مسئله کنید. به جای کد
</div>


```python
def my_doubler(x):
    return 2*x

def my_tripler(x):
    return 3*x
```

<div dir="rtl">

از کد زیر استفاده می‌کنیم، حال می‌توانیم بسیاری توابع مختلف بسازیم.
</div>


```python
def func(n):
    return lambda a : n * a

m = func(5)
# m = lambda a : 2 * a
print(m(3))
```

    15
    


```python
# you can use this to create a list of functions

def func(n):
    return lambda a : n * a

l = []
n = 4
for i in range(0, n):
    l.append(func(i))

for i in l:
    print(i(4))
```

    0
    4
    8
    12
    

<div dir="rtl">

## String formatting
در پایتون می‌توان با استفاده از تابع
``format``
نحوه نمایش رشته‌ها را تغییر داد.
</div>


```python
txt = "For only {:.2f} dollars!"
print(txt.format(49.565))
```

    For only 49.56 dollars!
    


```python
txt1 = "My name is {fname}, I'm {age}".format(fname = "John", age = 36)
txt2 = "My name is {0}, I'm {1}".format("John",36)
txt3 = "My name is {}, I'm {}".format("John",36)
print(txt1)
print(txt2)
print(txt3)

```

    My name is John, I'm 36
    My name is John, I'm 36
    My name is John, I'm 36
    


```python
txt = "lets convert 241231 to hexadecimal! here it is: {:X}"
print(txt.format(241231))

# another cool one
txt = "2312413236 is kinda hard to read no? here is a better version: {:,}"
print(txt.format(2312413236))

```

    lets convert 241231 to hexadecimal! here it is: 3AE4F
    2312413236 is kinda hard to read no? here is a better version: 2,312,413,236
    

<div dir="rtl">

# Escaping strings
فرض کنید بخواهیم کاراکتر 
``"``
را چاپ کنیم اما برنامه برای این کاراکتر معنای خاصی قرار داده است و خواهیم داشت:
</div>


```python
txt = "now " doesn't mean anything special"
print(txt)
```


      File "C:\Users\98937\AppData\Local\Temp/ipykernel_9544/3008024286.py", line 1
        txt = "now " doesn't mean anything special"
                     ^
    SyntaxError: invalid syntax
    


<div dir="rtl">

 از ``\``
استفاده می‌کنیم.
</div>


```python
txt = "now \" doesn't mean anything special"
print(txt)
```

    now 
     doesn't mean anything special
    

<div dir="rtl">

## تمرین
برنامه‌ای بنویسید که با گرفتن ثانیه، مقدار زمان به صورت روز:ساعت:دقیقه:ثانیه را برگرداند.
</div>


```python
time = float(input("Input time in seconds: "))
day = time // (24 * 3600)
time = time % (24 * 3600)
hour = time // 3600
time %= 3600
minutes = time // 60
time %= 60
seconds = time
print("d:h:m:s -> %d days :%d hours :%d minutes :%d seconds" % (day, hour, minutes, seconds))
```

<div dir="rtl">

## تمرین
برنامه‌ای بنویسید که n و m را گرفته و n عدد دریافت کند و بررسی کند که چند عدد بزرگتر از m هستند و آنها را چاپ کند.
</div>


```python
n = int(input())
m = float(input())

l = []
for i in range(0, n):
    c = float(input("enter a number"))
    if c > m:
        l.append(c)

l.sort()
print(l, len(l))

```

<div dir="rtl">

## تمرین
تابعی بنویسید که یک عدد n دریافت کند و سپس n تابع تولید کند که هر کدام یک عدد را n برابر می‌کنند. سپس نتیجه را برای عدد دیگری که در ورودی می‌گیرد محاسبه کند.
</div>


```python
def fun_func(n, m):

    def func(n):
        return lambda a : n * a

    l = []
    for i in range(0, n):
        l.append(func(i))

    for i in l:
        print(i(m))

fun_func(5, 10)
print(20*"=")
fun_func(15, 2)

```

<div dir="rtl">

## تمرین
برنامه‌ای بنویسید که اول یک عدد n دریافت کرده، سپس n اقلام را دریافت کرده و در آخر قیمت هر کدام را بگیرد و یک لیست فرمت شده چاپ کند. به عنوان مثال:

bread
40

خروجی:

bread: $40.00
</div>


```python

```
