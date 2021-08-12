<div dir="rtl">

# جلسه دوم، روز ۱۵ مرداد
## ادامه مقدمات پایتون
در جلسه گذشته با مقدمات زبان پایتون آشنا شدیم. در این جلسه قصد داریم تا با بررسی ساختارهای تصمیم و داده، از پایتون بهره بیشتری ببریم.
</div>

<div dir="rtl">

## یادآوری
### مثال:
برنامه‌ای بنویسید که با گرفتن شعاع یک دایره، مساحت آن را محاسبه کند.
</div>


```python
# in python, libraries are imported using the import keyword
# math is a built-in library of python, meaning that all versions of python
# have it automatically. you can access the functions of a library using . 
# for example, to access the value of pi (=3.1415926535...) we need to use
# math.pi, since pi is a value and not a function, we use math.pi instead of
# math.pi(), to understand the "." operator, math.pi basically means
# get the variable pi from the library math.
import math

r = input("enter r")
r = float(r)

# the area of a circle is A = pi * r^2
A = math.pi * r**2

print(A)
```

    6361.725123519331
    

<div dir="rtl">

### مثال:
برنامه‌ای بنویسید که سینوس یک عدد را محاسبه و چاپ می‌کند.
</div>


```python
# we need the sin() function from the math library
import math

x = input("enter x in radians")
x = float(x)

print(math.sin(x))
```

<div dir="rtl">

### مثال:
برنامه‌ای بنویسید که یک عدد را دریافت کرده و توان دوم، سوم و چهارم آن را چاپ می‌کند.
</div>


```python
# approach number one

x = input("enter x")
x = float(x)
print(x**2, x**3, x**4)
```


```python
# approach number two
# get the pow function from the math library
import math

x = input("enter x")
x = float(x)
print(math.pow(x, 2), math.pow(x, 3), math.pow(x, 4))
```

<div dir="rtl">

## لیست‌ها
تا اینجای کار اگر می‌خواستیم با متغیرهای مختلف کار کنیم می‌بایست به هر کدام از آنها اسم مخصوصی نسبت داده و هر کدام را جدا استفاده کنیم. ولی فرض کنید می‌خواهید ۱۰۰ توان اول یک عدد را محاسبه و استفاده کنید، نمی‌توان از اول شروع کرد و ۱۰۰ متغیر جدا تعریف کرد. پس باید از ساختاری به نام لیست استفاده کنیم. لیست همانند بردارهای ریاضی است. کلکسیونی از چند متغیر که همه کنار هم مرتب شده‌اند. یک لیست به شکل زیر تعریف می‌شود:
</div>


```python
# l is a list

l = [1, 2, 3, 4]

# members are accessed using the [] operator:
# lists are indexed from 0, meaning l[2] is the third element in the list.
print(l[2])

# lists can contain anything
l = [2, "Hello", math.pi]

# you can print lists too
print(l)

# lists allow duplicates
l = [2, "Hello", math.pi, math.pi]
print(l)

# you can find out how many items are in a list using the len() function
print(len(l))

# lists are their own datatype, and don't depend on their values
print(type(l))

# you can also create lists using the list() constructor
# create an empty list
l_2 = list()
l_2 = []

# create a list with members, members can be lists too!
l_2 = list((l, "<- this element is a list inside of a list"))
print(l_2)
```

    3
    [2, 'Hello', 3.141592653589793]
    [2, 'Hello', 3.141592653589793, 3.141592653589793]
    4
    <class 'list'>
    [[2, 'Hello', 3.141592653589793, 3.141592653589793], '<- this element is a list inside of a list']
    




    'Hello'



<div dir="rtl">

## دسترسی به اعضای لیست‌ها
</div>


```python
# lists in python are also negative indexed, meaning
# the list [1, 2, 3, 4] can be accessed using
l = [1, 2, 3, 4]
print(l[0], l[1], l[2], l[3])

# but also, l[-1] refers to the last element, -2 refers to the second last and -3 refers to the third last element...
print(l[-4], l[-3], l[-2], l[-1])

# indices don't wrap around
# this will show an error:
# print(l[5])

# you can use the : operator to select a range of values
# l[1:3] means start from the element with index 1, then select elements until you reach the element with index 3. the last index is not included.
print(l[1:3])

# By leaving out the start value, the range will start at the first item
print(l[:3])

# By leaving out the end value, the range will go on to the end of the list:
print(l[1:])
```

    1 2 3 4
    1 2 3 4
    [2, 3]
    [1, 2, 3]
    [2, 3, 4]
    

<div dir="rtl">

## تغییر اعضای لیست
</div>


```python
thislist = ["apple", "banana", "cherry"]
thislist[1] = "blackcurrant"
print(thislist)
```

    ['apple', 'blackcurrant', 'cherry']
    

<div dir="rtl">

## متدها چیستند؟
در زبان پایتون، بعضی از انواع داده دارای توابعی مخصوص خود هستند. همانطور که با استفاده از اپراتور نقطه توانستیم به توابع و متغیرهای داخل یک کتابخانه دسترسی پیدا کنیم، با همین اپراتور می‌توانیم به توابع داخل ساختارهای داده دسترسی پیدا کنیم.
</div>


```python
l = [1, 2, "horse"]
l.insert(1, 3)
print(l)

# other methods for lists:

# remove a value from list
l.pop(1)
print(l)

# add value to end of list
l.append(3)
print(l)

# find value and remove it
l.remove("horse")
print(l)

# reverse list
l.reverse()
print(l)
```

    [1, 3, 2, 'horse']
    [1, 2, 'horse']
    [1, 2, 'horse', 3]
    [1, 2, 3]
    [3, 2, 1]
    

<div dir="rtl">

## رشته یا لیست؟
با رشته‌ها هم می‌توان مانند لیست‌ها کار کرد
</div>


```python
s = "Hello World"

print(s[1])
print(s[-5])
print(s[0:7])
```

    e
    W
    Hello W
    98
    

<div dir="rtl">

## متدهای رشته‌ها
</div>


```python
# strings have many methods, for example:

s = "Hello World"
# all uppercase
print(s.upper())

# all lowercase
print(s.lower())

# all lowercase to uppercase and vice versa
print(s.swapcase())
```

    HELLO WORLD
    hello world
    hELLO wORLD
    


```python
# you can add strings as well:
print("hello" + " " + "world")
```

    hello world
    3hello
    

<div dir="rtl">

## ساختارهای تصمیم
فرض کنید که می‌خواهید برنامه‌ای بنویسید که تنها در صورتی که حرف اول اسم دانشجو با حرف میم شروع شده باشد، پیام خوش‌آمدگویی چاپ کند. با استفاده از ساختارهای تصمیم می‌توانیم این کار را انجام دهیم.
</div>


```python
name = input("enter name")

# if first letter of name is M, then print message
# == is the comparison operator, returns True if operands are equal, else False.
# if <chain of logical statements>:
#   <code>
if name[0] == "M":
    print("Hello Student")
    if name[1] == "N":
        print("Hello Again")
print("Global")
```

<div dir="rtl">

## منطق در پایتون
</div>


```python
#In the example above, python is checking to see if the comparison is correct (True) or not (False)
print(10 > 9) # True
print(10 == 9) # False
print(10 < 9) # False
print(10 != 9) # True
print(10 <= 9) # False
print(10 >= 10) # True
```

    True
    False
    False
    True
    False
    True
    


```python
# more logical operators
print(10 > 8 and 10 > 9)
print(10 > 11 or 10 > 7)
print(not 10 > 9)
```

    True
    True
    False
    

<div dir="rtl">

## If, else
فرض کنید بخواهیم پیام دیگری را در صورت شروع شدن اسم با N 
چاپ کنیم و اگر هیچ کدام از این دو حالت نبود، پیامی دیگر چاپ کنیم. از ساختار تکمیل شده زیر استفاده می‌کنیم.
</div>


```python
name = input("enter name")

# if first letter of name is M, then print message
# if first letter of name is N, the print another message
# if first letter of name is L, then print another message

if name[0] == "M":
    print("Hello Student")
elif name[0] == "N": #elif = else if
    print("Hello Special Student")
else:
    print("Hello Regular Student")
```


```python
x = 41

if x > 10:
  print("Above ten,")
  if x > 20:
    print("and also above 20!")
  else:
    print("but not above 20.")
```

    Above ten,
    and also above 20!
    

<div dir="rtl">

## حلقه‌ها در پایتون
در این جلسه با حلقه for آشنا می‌شویم. از حلقه‌ها برای تکرار دستورات استفاده می‌شود.
قبل از این کار باید با دستور in و تابع range آشنا شویم.

دستور in چک می‌کند که یک متغیر در یک کلکسیونی از متغیرها حضور داشته باشد.
</div>


```python
# <variable> in <collection>
print(2 in [1, 2, 3, 4, 5])
print(6 in [1, 2])
print(1 not in [3, 3])
if 6 in [1, 2, 3]:
    print("Hello")
```

    True
    False
    True
    

<div dir="rtl">

از تابع range() برای تولید بازه اعداد استفاده می‌شود.
</div>


```python
# range(a, b, n) returns a sequence of numbers starting from a, going up to but not including b, in increments of n 
# a for loop is created as follows:
# for <variable> in <sequence>:
#   <code>

for i in range(1, 10):
    print(i)

# you can have any collection in place of a range:
print(20*"*")
for i in [1, 2, 3, 4, "banana"]:
    print(2*i)
```

    1
    2
    3
    4
    5
    6
    7
    8
    9
    ********************
    2
    4
    6
    8
    bananabanana
    


```python
# you can use else in for loops, the else block will be executed after the for loop finishes COMPLETELTY executing.
for x in range(6):
  print(x)
else:
  print("Finished!")
```

    0
    1
    2
    3
    4
    5
    Finished!
    


```python
# With the break statement you can stop the loop halfway through
for x in range(6):
  if x == 3: 
    break
  print(x)
else:
  print("Finished!")
```

    0
    1
    2
    


```python
# the continue statement can be used to skip one iteration of the loop

fruits = ["apple", "banana", "cherry"]
for x in fruits:
  if x == "banana":
    continue
  print(x)
```

    apple
    cherry
    


```python
# nested loops
for x in range(3): # x in [0, 1, 2]
  for y in range(2): # y in [0, 1]
    print(x, y)
```

    0 0
    0 1
    1 0
    1 1
    2 0
    2 1
    

<div dir="rtl">

## تمرینات
</div>

<div dir="rtl">

### مثال
برنامه‌ای بنویسید که با گرفتن شعاع یک کره، حجم آن را محاسبه کند.
</div>


```python
import math

r = input("enter the radius:")
r = float(r)

V = 4/3 * math.pi * r**3
print('The volume of the sphere is: ', V)
```

<div dir="rtl">

### مثال
برنامه‌ای بنویسید که یک عدد را منهای ۷ کند و اگر قدرمطلق این تفاضل بیشتر از ۱۳ بود دو برابر آن را چاپ کند. راهنمایی: برای قدر مطلق از تابع abs استفاده کنید.
</div>


```python
x = input("enter a number")
x = float(x)

diff = abs(x - 7)
if diff > 13:
    print(2*diff)
```

<div dir="rtl">

### مثال
برنامه‌ای بنویسید که عددی صحیح را دریافت کند و چک کند که آیا این عدد در فاصله ۱۰۰ واحدی عدد ۶۰۰ یا در فاصله ۵۰ واحدی عدد ۱۲۰۰ هست یا نه.
</div>


```python
x = input("enter a number")
x = int(x)

result = abs(600 - x) < 100 or abs(1200 - x) < 50
print(result)
```

<div dir="rtl">

### مثال
برنامه‌ای بنویسید که یک عدد صحیح از کاربر گرفته، اگر منفی بود پیامی منبی بر غلط بودن ورودی چاپ کرده و اگر مثبت بود زوج یا فرد بودن آن را مشخص کرده و اعلام کند.
</div>


```python
x = input("enter a number")
x = int(x)

if x >= 0:
    if x % 2 == 0:
        print(str(x) + " " + "is even")
    else:
        print(str(x) + " " + "is odd")
else:
    print("input is below zero, error")
```

<div dir="rtl">

### مثال
برنامه‌ای بنویسید که در ابتدا یک عدد n دریافت کرده
سپس n عدد صحیح را از ورودی خوانده و
  خروجی آن یک نمودار مستطیلی به شکل:
a : ####...### (a times)
است.
</div>

<div dir="rtl">

### نکته
با اضافه کردن = به اپراتور های ریاضی می‌توانید دو عملیات را با هم ترکیب کنید.
</div>


```python
x = 5

# this
x += 5

# is the same as this
x = x + 5

# this
x /= 5

# is the same as this
x = x / 5

# you can use similar operators like -= and *= for other mathematical operations.
```


```python
n = int(input("enter n"))

l = []

# read n numbers from input and put them in a list
for i in range(n):
    c = int(input("enter a number"))
    l.append(c)

# print hashtags
for i in l:
    temperory_string = i*"#"
    print(str(i) + " : " + temperory_string)
```
