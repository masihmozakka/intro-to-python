<div dir="rtl">



# جلسه سوم، ۲۱ مرداد



در دو جلسه گذشته مقدماتی از زبان پایتون را یاد گرفتیم. در این جلسه قصد داریم تا ضمن یادآوری مطالب جلسات گذشته، کمی اطلاعات خود از مفاهیم اولیه پایتون را تکمیل کنیم. در ابتدا با یک حلقه تکرار جدید شروع می‌کنیم. سپس مروری کلی از مطالب گذشته خواهیم داشت و در ادامه با چندین مطلب جدید کار را به پایان خواهیم رساند.

</div>

## While loops

<div dir="rtl">



در جلسه گذشته با حلقه‌های for
آشنا شدیم. در این حلقه‌ها ما در ابتدای کار مشخص می‌کنیم که انتظار داریم حلقه چند بار تکرار شود، و بعد اگر نیاز شد با break
و continue
تعداد تکرار شدن را تغییر می‌دهیم. یک حقله دیگر داریم که بر خلاف for،
به جای استفاده از یک شرط تکرار به فرم range
از یک شرط منطقی استغاده می‌کند.

</div>


```python
# a while loop is written as follows:

# while (condition):

#   <code>



x = 5

while x <= 10:

    print(x)

    x += 1 # x = x + 1

print("Hello students")
```

    5
    6
    7
    8
    9
    10
    Hello students
    


```python
# you can also have else blocks



n = 2

while 2**n <= 32:

    print(n)

    n += 1

else:

    print('done')
```

    2
    3
    4
    5
    done
    


```python
# you can also use break and continue like you did with for loops

# also note how the else block isnt executed because we exited the while loop

# using a break, instead of exiting because of a logical condition



n = 2

while 2**n <= 32:

    print(n)

    n += 1

    if n == 4:

        break

else:

    print('done')
```

    2
    3
    


```python
while True:

    print("Hello world")
```

    False
    

<div dir="rtl">



## مرور مطالب گذشته

</div>

<div dir="rtl">



### تمرین

با حل دو تمرین مطالب گذشته را مرور می‌کنیم. در تمرین اول از شما خواسته شده است تا برنامه‌ای بنویسید که بازی حدس اعداد را پیاده سازی کند.
عدد صحیح n را داریم
و کاربر می‌خواهد آن را حدس بزند. اگر عددی که وارد کرد کمتر از n 
بود، چاپ کند lower
و اگر بیشتر بود چاپ کند higher.
برنامه تا زمانی ادامه دارد که کاربر حدس درست بزند و سپس یک متن کوتاه برای تبریک گفتن چاپ می‌شود.

</div>

<div dir="rtl">



### تمرین

برنامه‌ای بنویسید که با گرفتن n عدد
میانگین، عضو مینیمم، ماکزیمم و ۲ عضو بزرگ و کوچک لیست را چاپ کند. راهنمایی: از توابع min() و
max()
و sort()
و sum()
می‌توانید استفاده کنید.



n لزوما از ۵ بزرگتر است.

</div>


```python
# min and max return minimum and maximum values



l = [5, 6, 6, 2, 1, 3, 4]

print(min(l), max(l))



# sum returns sum of a list, sort sorts it in ascending order

l.sort()

print(sum(l), l)
```

    1 6
    21 [1, 2, 3, 4, 5, 6]
    

<div dir="rtl">



## دیکشنری‌ها

ما تا به حال، با لیست‌ها آشنا شدیم. لیست‌ها مجموعه‌ای از داده‌ها هستند که هم می‌توان از آن‌ها حذف کرد و یا در صورت به آنها اضافه کرد، در صورت نیاز داده‌ای را تفییر داد همچنین، این داده‌ها ترتیبی خاص را رعایت می‌کنند و می‌توان به آن‌ها با استفاده از اندیس دسترسی پیدا کرد.



اگر دقت کنیم، ۲ ویژگی را نام بردیم،

+ قابلیت حذف و اضافه داده‌ها

+ ترتیب داشتن داده‌ها



در پایتون، بسته به وجود یا عدم وجود هر کدام از این ۲ شرط، ساختارهای جدیدی وجود دارد.



- لیست‌ها: تغییرپذیر و دارای ترتیب

- تاپل‌ها: تغییرناپذیر و دارای ترتیب

- مجموعه‌ها: تغییرناپذیر و بدون ترتیب

- دیکشنری‌ها: تغییرپذیر و دارای ترتیب (بدون عضوهای تکراری) 





</div>

<div dir="rtl">



یک دیکشنری تقریبا با تعریف عامیانه ما از آن، همخوانی دارد. در دیکشنری‌های زبان، یک سری **کلید**
به صورت *نام کلمه*
داریم و برای دسترسی به
**مقدار**
آن کلید که در واقع *معنی کلمه* است در دیکشنری با استفاده از کلید جست و جو می‌کنیم.

</div>


```python
# a dictionary is defined as follows:

# dict = { "key" : value ...}



python_teachers = {"name" : "masih", "surname" : "mozakka"}



thisdict = {

  "brand": "Ford",

  "model": "Mustang",

  "year": 1964

}

print(thisdict)
```


```python
# dictionary members are accessed like:



thisdict = {

  "brand": "Ford",

  "model": "Mustang",

  "year": 1964

}



print(thisdict["brand"])
```

    Ford
    


```python
# duplicates are not allowed



thisdict = {

  "brand": "Ford",

  "model": "Mustang",

  "built_year": 1964,

  "year": 2021

}

print(thisdict)
```

    {'brand': 'Ford', 'model': 'Mustang', 'built_year': 1964, 'year': 2021}
    


```python
thisdict = {

  "brand": "Ford",

  "model": "Mustang",

  "year": 1964,

  "year": 2020

}

print(type(thisdict), len(thisdict))


```

    <class 'dict'> 3
    


```python
# we create new dict items by assigning a new key, if the key isnt in the dictionary

# a new key is added to the dict. if it is, duplicates are not allowed and the key gets

# an updated value instead



car = {

"brand": "Ford",

"model": "Mustang",

"year": 1964

}



print(car)



car["color"] = "white"

car["model"] = "Daytona"

print(car)
```

    {'brand': 'Ford', 'model': 'Mustang', 'year': 1964}
    {'brand': 'Ford', 'model': 'Daytona', 'year': 1964, 'color': 'white'}
    


```python
# some useful dictionary methods

# the get() method works like []:



car = {

"brand": "Ford",

"model": "Mustang",

"year": 1964

}



print(car.get("color"))



# the keys method returns a list of the keys in the dict

# x is automatically updated to reflect changes in the dictionary



x = car.keys()



print(x) #before the change



car["color"] = "white"



print(x) #after the change
```

    None
    dict_keys(['brand', 'model', 'year'])
    dict_keys(['brand', 'model', 'year', 'color'])
    


```python
# the values() method returns values instead of keys (like get()):

# like get, if we change the dictionary x will be updated automatically

car = {

"brand": "Ford",

"model": "Mustang",

"year": 1964

}



x = car.values()



print(x) #before the change



car["color"] = "white"



print(x) #after the change
```

    dict_values(['Ford', 'Mustang', 1964])
    dict_values(['Ford', 'Mustang', 1964, 'white'])
    


```python
# we usually check if keys exist like this:



thisdict = {

  "brand": "Ford",

  "model": "Mustang",

  "year": 1964

}

if "model" in thisdict:

  print("Yes, 'model' is one of the keys in the thisdict dictionary")
```

    Yes, 'model' is one of the keys in the thisdict dictionary
    


```python
# with the update method you can merge two dictionaries



thisdict = {

  "transmission": "Auto",

  "gearbox": "Six speed",

  "units": ["A", "B", "C"],

  "year": 1964

}



cars_list = {

"brand": "Chevrolet",

"model": "Tahoe",

"year": 2015

}



cars_list.update(thisdict)

print(cars_list)
```

    {'brand': 'Chevrolet', 'model': 'Tahoe', 'year': 1964, 'transmission': 'Auto', 'gearbox': 'Six speed', 'units': ['A', 'B', 'C']}
    


```python
# we remove items using the pop() method

car = {

"brand": "Ford",

"model": "Mustang",

"year": 1964

}



car.pop("year")



print(car)



# pop item removes last item added to the dictionary



car.update({"year" : 2021})

print(car)



# clear removes all items from the dict



car.clear()

print(car)
```

    {'brand': 'Ford', 'model': 'Mustang'}
    {'brand': 'Ford', 'model': 'Mustang', 'year': 2021}
    {}
    

<div dir="rtl">



## تاپل‌ها

دیکشنری‌ها استفاده‌های خود را دارند. اما دیکشنری‌ها و لیست‌ها قابلیت تغییرپذیری را دارند که کار با آنها را کمی ریسکی می‌کند. تاپل‌ها تغییرپذیر نیستند و به این دلیل می‌توان از آنها با اطمینان بیشتری استفاده کرد.

</div>


```python
# a tuple is created like tuple = (<value1>, <value2>...)



thistuple = ("apple", "banana", "cherry")

print(thistuple)
```


```python
# tuples are ordered and you can access their items by []:



thistuple = ("apple", "banana", "cherry")

print(thistuple[0])
```

    apple
    


```python
# you cant add to tuples, or change their elements



thistuple = ("apple", "banana", "cherry")

thistuple[0] = "wood"

print(thistuple)
```


    ---------------------------------------------------------------------------

    TypeError                                 Traceback (most recent call last)

    ~\AppData\Local\Temp/ipykernel_13288/3205643463.py in <module>
          2 
          3 thistuple = ("apple", "banana", "cherry")
    ----> 4 thistuple[0] = "wood"
          5 print(thistuple)
    

    TypeError: 'tuple' object does not support item assignment



```python
# tuples allow duplicates



thistuple = ("apple", "banana", "cherry", "apple", "cherry")

print(thistuple)
```

    ('apple', 'banana', 'cherry', 'apple', 'cherry')
    


```python
# when creating a tuple with one element, remember to add a comma



thistuple = ("apple",)

print(type(thistuple))



# NOT a tuple

thistuple = ("apple")

print(type(thistuple))
```

    <class 'tuple'>
    <class 'str'>
    


```python
# joining two tuples



tuple1 = ("a", "b" , "c")

tuple2 = (1, 2, 3)



tuple3 = tuple1 + tuple2

print(tuple3)
```

    ('a', 'b', 'c', 1, 2, 3)
    


```python
# we can even multiply a tuple



fruits = ("apple", "banana", "cherry")

mytuple = fruits * 2



print(mytuple)
```

    ('apple', 'banana', 'cherry', 'apple', 'banana', 'cherry')
    


```python
# fun fact, you can do these with lists as well



list1 = ["a", "b" , "c"]

list2 = [1, 2, 3]



list3 = list1 + list2

print(list3)



fruits = ["apple", "banana", "cherry"]

mylist = fruits * 2



print(mylist)
```

    ['a', 'b', 'c', 1, 2, 3]
    ['apple', 'banana', 'cherry', 'apple', 'banana', 'cherry']
    

<div dir="rtl">



## توابع

تاکنون با توابعی مانند Print 

و type

آشنا شده‌ایم. توابع قسمت‌هایی از کد هستند با نامی خاص که هر گاه آن نام را در کد بیاوریم، آن قسمت از کد اجرا می‌شود. توابع آنجایی به درد ما می‌خورند که نیاز باشد یک تکه کد را چندین بار اجرا کنیم. در چنین شرایطی نمی‌توان مدام کد را کپی پیست کرد و بهتر است تا به آن تیکه کد یک نام مشخص بدهیم و آن نام را در کد استفاده کنیم.

</div>


```python
# functions are declared using the def keyword



def my_function():

    print("Hello from a function")



my_function()
```

    Hello from a function
    


```python
# you can pass parameters into your function



def func(n):

    3*n - 2 + n**2

func(5)



def email_creator(name, domain):

    print(name + "@" + domain)



email_creator("masih", "aut.ac.ir")

email_creator("mozakkam", "gmail.com")
```

    masih@aut.ac.ir
    mozakkam@gmail.com
    


```python
# you can define functions in the middle of your code, but its best practice to put all

# definitions at the top



print("hello this is a definition")



def email_creator(name, domain):

    print(name + "@" + domain)



email_creator("masih", "aut.ac.ir")

email_creator("mozakkam", "gmail.com")
```


```python
# if you try to call the function with one argument, you will get an error

def email_creator(name, domain):

    print(name + "@" + domain)



email_creator("masih")
```


```python
# default arguments



def email_creator(name, domain="yahoo.com"):

    print(name + "@" + domain)



email_creator("masih", "aut.ac.ir")

email_creator("masih")
```


```python
# returning values from a function



def my_function(x):

  return 5 * x



print(my_function(3))

print(my_function(5))

print(my_function(9))
```


```python
# the function stops executing as soon as reaching a return keyword



def my_function(x):

    if x == 9:

        return 10 * x

    return 5 * x



print(my_function(3))

print(my_function(5))

print(my_function(9))
```


```python
# functions cannot be empty, so if you still havent written code, write pass

def myfunction():

    pass
```

## recursion

<div dir="rtl">



اگر در کد تابع، خود تابع را فرابخوانیم ریکرژن خواهیم داشت. تابع خودفراخوانی خواهد کرد تا زمانی که به یک شرط خروجی برسد

</div>


```python
def func (x):

    if x > 10:

        return x

    else:

        print(x)

        func(x+1)



func(5)
```


```python
# we can use recursion for a lot of fun things



def factorial(n):

    if n == 1:

        return 1

    else:

        return n * factorial(n-1)



print(factorial(5))
```


```python
# functions inside function



def myfunc():

  x = 300

  def myinnerfunc():

    print(2*x)

  myinnerfunc()



myfunc()
```

<div dir="rtl">



### تمرین

تابعی بنویسید که با گرفتن قد و وزن، بی‌ام‌آی را از فرمول

</div>



$$\text{bmi} = weight/(height^2)$$



<div dir="rtl">



محاسبه کند.

</div>

<div dir="rtl">



### تمرین

تابعی بنویسید که طول و عرض یک مستطیل را گرفته، مساحت آن را محاسبه می‌کند و اگر این مساحت از ۱۰ بزرگتر بود مقدار True را برگرداند و اگر کوچکتر بود False

</div>


