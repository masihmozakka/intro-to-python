<div dir="rtl">

# جلسه پنجم، ۲۹ مرداد
در این جلسه قصد داریم تا کمی برنامه‌های خود را از محوریت تک فایلی بودن، به فایل‌های مختلف گسترش دهیم و کمی هم با نحوه برخورد با خطاهای کد آشنا شویم.
</div>

<div dir="rtl">

## List comprehension
این تکنیک به ما کمک می‌کند تا برنامه‌های جمع و جور تری بنویسیم،‌ فرض کنید لیستی از میوه‌ها را داریم و فقط می‌خواهیم آنهایی را نگه داریم که با حرف a شروع می‌شوند.
راه اول:
</div>


```python
fruits = ["apple", "apricot", "banana", "cherry", "kiwi", "mango"]
newlist = []

for x in fruits:
  if "a" == x[0].lower():
    newlist.append(x)

print(newlist)
```


```python
# [<do something> for <var> in <list>]
# if is optional:
# [<do something> for <var> in <list> if <var satisfies condition>]

fruits = ["apple", "apricot", "banana", "cherry", "kiwi", "mango"]

newlist = [x for x in fruits if "a" == x[0]]

print(newlist)
```


```python
# program to get 5 numbers from the console and double them
numbers = [2*int(input()) for i in range(0, 5)]
print(numbers)
```

<div dir="rtl">

## assert
یکی از کارهایی که زمان بسیاری از یک برنامه‌نویس می‌گیرد، بررسی نحوه کارکرد کد است. خصوصا اگر شما بر روی یک فایل بزرگ کار می‌کنید و ممکن است دقیقا یادتان نباشد که هر تابع یا تکه کد، دقیقا چه خروجی‌ای باید داشته باشد. حال اگر شما بر روی این تکه کد کار کنید نیاز دارید تا آن را **تست** کنید. تست کردن یکی از کارهای بسیار پراهمیت در برنامه نویسی است.

در پایتون می‌توانیم با استفاده از کلیدواژه `assert` یک تست ساده بنویسیم.
</div>


```python
# assert can be used to verify the correctness of a piece of code
def func(a, b):
    return a + b

# if the condition is true, then assert would do nothing.
assert func(1, 2) == 3, "the program is not adding correctly!"
```


```python
# lets imagine we did something to our code to break it
def func(a, b):
    return a + b

# if the condition is false, then assert would raise an AssertionError and print our message
assert func(1, 2) == 3, "the program is not adding correctly!"
```


```python
# if we wanted to write the same code, we had to:
def func(a, b):
    b += 2
    return a + b

def check_func(f):
    if f(1, 2) != 3:
        print("the program is not adding correctly")

check_func(func)
```

<div dir="rtl">

## raise
اگر در کد بالا می‌خواستیم خود `AssertionError` را اعلام کرده و اجرای کد را متوقف کنیم چه باید می‌کردیم؟ جواب ما در کلیدواژه `raise` نهفته است.

هر خطا در پایتون نام خود را دارد. به عنوان مثال اگر شما سعی کنید از متغیری استفاده کنید که آن را در برنامه تعریف نکرده‌اید،‌ یک `NameError` توسط برنامه اعلام گشته و اجرای آن متوقف می‌شود. به خطاها در پایتون `Exception` می‌گویند.

یک لیست خوب از خطاهای متداول پایتون در [این لینک](https://www.w3schools.com/python/python_ref_exceptions.asp) موجود است.
</div>


```python
def func(a, b):
    b += 2
    return a + b

def check_func(f):
    if f(1, 2) != 3:
        raise AssertionError("the program is not adding correctly")

check_func(func)
```

<div dir="rtl">

## try... except
</div>

<div dir="rtl">

استفاده از `assert` برای مقاصد تست کردن مناسب است. ولی کد شما ممکن است بیشتر از یک نوع خطا را تجربه کند. همچنین، خیلی اوقات لازم نیست تا اجرای کل برنامه متوقف شود و می‌توان با بعضی خطاها به طور پویا برخورد کرد. به طور مثال، ممکن است شما برنامه‌ای نوشته باشید که فقط باید اعداد صحیح مثبت را دریافت کند. یک راه این است که با چند `assert`‌ این را چک کنید. ولی اگر خطایی داده شود برنامه کاملا متوقف خواهد شد. اما ممکن است شما نخواهید تا برنامه اجرایش را متوقف کند. یا، اگر عدد صحیح مثبتی به برنامه داده نشده بود شما می‌توانید خود این عدد را تولید کنید.
</div>


```python
# basic try except block
x = 2
try:
  print(x)
except:
  print("An exception occurred")
```


```python
# you can chain exceptions

#x = 2
try:
  print(x)
except NameError:
  print("Variable x is not defined")
except:
  print("Something else went wrong")
```


```python
# else block executes if nothing goes wrong

try:
  print("Hello")
except:
  print("Something went wrong")
else:
  print("Nothing went wrong")
```


```python
# finally will execute if something goes wrong or not

try:
  print(x)
except:
  print("Something went wrong")
finally:
  print("The 'try except' is finished")
```

<div dir="rtl">

## Files
تا به حال، خروجی برنامه را در کنسول چاپ می‌کردیم، حال، خروجی را به یک فایل می‌نویسیم تا بعدا به آن دسترسی داشته باشیم.
</div>


```python
# "r" - Read - Default value. Opens a file for reading, error if the file does not exist
# "a" - Append - Opens a file for appending, creates the file if it does not exist
# "w" - Write - Opens a file for writing, creates the file if it does not exist
# "x" - Create - Creates the specified file, returns an error if the file exists

# these are extra modes that we can use to further articulate the nature of the file
# "t" - Text - Default value. Text mode
# "b" - Binary - Binary mode (e.g. images)
# open a text "t" file for reading "r"

f = open("demofile.txt", "rt")
```


```python
# create a text file

f = open("newfile.txt", "wt")
```


```python
# if you want to read a text file no need to specify "rt"
f = open("newfile.txt")
print(f.read(4))
print(f.read(4))
print(f.read(5))
f.close()
```


```python
# append content to end of file

f = open("newfile.txt", "a")
f.write("Now the file has more content!")
f.close()

#open and read the file after the appending:
f = open("newfile.txt")
print(f.read(5))
```


```python
# "w" overwrites entire file

f = open("newfile.txt", "w")
f.write("Woops! I have deleted the content!")
f.close()

#open and read the file after the appending:
f = open("newfile.txt")
print(f.readline())
```

<div dir="rtl">

## Modules
برنامه نویسی خیلی سخت می‌شود اگر تمامی کد را داخل یک فایل بسیار بزرگ ذخیره کنیم. بهتر است تا کد را در چندین فایل قابل مدیریت نگه داریم.
</div>


```python
# import <module>
import test_module

test_module.func(5)
# print(test_module.variable2)
```


```python
# you can define aliases using the as keyword
import test_module as tm

tm.func(4)
```


```python
# you can use the from keyword to import part of a module
# this helps to write faster code

from test_module import variable2

print(variable2)
```

<div dir="rtl">

## چند ماژول بدردبخور
اول با ماژون رندوم شروع می‌کنیم:
</div>


```python
import random as rd 

rd.seed(None)
cards = ["Ace", "Deuce", "Queen", "Jack", "King"]
for i in range(0, 5):
    print(rd.random())
    print(rd.choice(cards))
```


```python
import cmath as cm

cm.exp(1+2j)
cm.phase(1-2j)
cm.polar(1+1j)
```


```python
# use dir() to get information related to the module
import statistics as st
dir(test_module)
```




    ['__builtins__',
     '__cached__',
     '__doc__',
     '__file__',
     '__loader__',
     '__name__',
     '__package__',
     '__spec__',
     'func',
     'variable2']




```python
import statistics as st

data = [1, 1, 5, 4, 6, 8, 2, 12, 2, 4, 6]
st.variance(data)
```




    11.054545454545455



<div dir="rtl">

## pip
در پایتون بعضی مدول‌ها داخل خود برنامه هستند و ما صرفا نیاز داریم تا آنها را `import`
کنیم. ولی هزاران مدول هم توسط برنامه نویسان دیگه نوشته شده است که ما می‌توانیم دانلود کنیم. بدین منظور، باید کار با پیپ را یاد بگیریم. پیپ خود یک ماژول پایتون است که دانلود و نصب بقیه ماژول های پایتون را انجام می‌دهد.
</div>

these should be run in the terminal (like powershell or cmd prompt or bash):

> pip --version

or

>python -m pip --version

if you get an output telling you a version that means you're good

you can install packages by
>pip install "package name"

and uninstall them using
>pip uninstall "package name"

lets install a package called matplotlib that helps us plot graphs:

>pip install matplotlib


```python
import numpy as np
import matplotlib.pyplot as plt


category_names = ['Strongly disagree', 'Disagree',
                  'Neither agree nor disagree', 'Agree', 'Strongly agree']
results = {
    'Question 1': [10, 15, 17, 32, 26],
    'Question 2': [26, 22, 29, 10, 13],
    'Question 3': [35, 37, 7, 2, 19],
    'Question 4': [32, 11, 9, 15, 33],
    'Question 5': [21, 29, 5, 5, 40],
    'Question 6': [8, 19, 5, 30, 38]
}


def survey(results, category_names):
    """
    Parameters
    ----------
    results : dict
        A mapping from question labels to a list of answers per category.
        It is assumed all lists contain the same number of entries and that
        it matches the length of *category_names*.
    category_names : list of str
        The category labels.
    """
    labels = list(results.keys())
    data = np.array(list(results.values()))
    data_cum = data.cumsum(axis=1)
    category_colors = plt.get_cmap('RdYlGn')(
        np.linspace(0.15, 0.85, data.shape[1]))

    fig, ax = plt.subplots(figsize=(9.2, 5))
    ax.invert_yaxis()
    ax.xaxis.set_visible(False)
    ax.set_xlim(0, np.sum(data, axis=1).max())

    for i, (colname, color) in enumerate(zip(category_names, category_colors)):
        widths = data[:, i]
        starts = data_cum[:, i] - widths
        rects = ax.barh(labels, widths, left=starts, height=0.5,
                        label=colname, color=color)

        r, g, b, _ = color
        text_color = 'white' if r * g * b < 0.5 else 'darkgrey'
        ax.bar_label(rects, label_type='center', color=text_color)
    ax.legend(ncol=len(category_names), bbox_to_anchor=(0, 1),
              loc='lower left', fontsize='small')

    return fig, ax


survey(results, category_names)
plt.show()
```


    
![svg](Session%205%20-%2029%20Mordad_files/Session%205%20-%2029%20Mordad_34_0.svg)
    


<div dir="rtl">

## intro to matplotlib
</div>

<div dir="rtl">

## numpy
بعدا بیشتر در مورد نامپای حرف خواهیم زد، اما فعلا یک ورودی کوتاه به آن داشته باشیم:
</div>


```python
import numpy as np

arr = np.array([1, 2, 3, 4, 5])

print(arr)
```

    [1 2 3 4 5]
    


```python
arr = np.array([[1, 2, 3], [4, 5, 6]])

print(arr[0, 1])
```

    2
    


```python

a = np.array(42)
b = np.array([1, 2, 3, 4, 5])
c = np.array([[1, 2, 3], [4, 5, 6]])
d = np.array([[[1, 2, 3], [4, 5, 6]], [[1, 2, 3], [4, 5, 6]]])


print(a.ndim)
print(b.ndim)
print(c.ndim)
print(d.ndim)
print(d)
```

    0
    1
    2
    3
    [[[1 2 3]
      [4 5 6]]
    
     [[1 2 3]
      [4 5 6]]]
    


```python
arr = np.array([[1,2,3,4,5], [6,7,8,9,10]])

print('2nd element on 1st dim: ', arr[0, 1])
```

    2nd element on 1st dim:  2
    


```python
# numpy also has many useful builtin functions
x = np.sin(np.pi/2)

print(x)
```

    1.0
    


```python
arr = np.array([np.pi/2, np.pi/3, np.pi/4, np.pi/5])

x = np.sin(arr)
print(x)
```

    [1.         0.8660254  0.70710678 0.58778525]
    


```python
from numpy import random
x = random.randint(100, size=(3, 3))

print(x)
```

    [[11 93  3]
     [90  1 62]
     [63 80 93]]
    


```python
# imports
import matplotlib.pyplot as plt
import numpy as np

# use numpy arrays
xpoints = np.array([0, 4, 6])
ypoints = np.array([0, 2, 250])

# show the plot
plt.plot(xpoints, ypoints)
plt.plot(xpoints, ypoints, 'o')
plt.show()
```


    
![svg](Session%205%20-%2029%20Mordad_files/Session%205%20-%2029%20Mordad_44_0.svg)
    



```python
xpoints = np.array([1, 2, 6, 8])
ypoints = np.array([3, 8, 1, 10])

plt.plot(xpoints, ypoints, marker='s', linestyle = 'dotted', color='#6E3F50')
plt.show()
```


    
![svg](Session%205%20-%2029%20Mordad_files/Session%205%20-%2029%20Mordad_45_0.svg)
    



```python
y1 = np.array([3, 8, 1, 10])
y2 = np.array([6, 2, 7, 11])

plt.plot(y1)
plt.plot(y2)

plt.show()
```


    
![svg](Session%205%20-%2029%20Mordad_files/Session%205%20-%2029%20Mordad_46_0.svg)
    



```python
x1 = np.array([0, 1, 2, 3])
y1 = np.array([3, 8, 1, 10])
x2 = np.array([0, 1, 2, 3])
y2 = np.array([6, 2, 7, 11])

plt.plot(x1, y1, x2, y2)
plt.show()
```


    
![svg](Session%205%20-%2029%20Mordad_files/Session%205%20-%2029%20Mordad_47_0.svg)
    



```python
from numpy import random
x = random.randint(100, size=(1000))
y = random.randint(100, size=(1000))

fig, ax = plt.subplots()
ax.plot(x, y, 'o')

ax.set(xlabel='test no.', ylabel='result',
       title='Can you see a pattern?')

ax.grid()
plt.show()
```


    
![svg](Session%205%20-%2029%20Mordad_files/Session%205%20-%2029%20Mordad_48_0.svg)
    



```python
# Data for plotting
t = np.arange(0.0, 2.0, 0.01)
s = np.sin(2 * np.pi * t)
fig, ax = plt.subplots()
ax.plot(t, s)

ax.set(xlabel='time (s)', ylabel='voltage (mV)',
       title='About as simple as it gets, folks')
ax.grid()

fig.savefig("test.png")
plt.show()
```


    
![svg](Session%205%20-%2029%20Mordad_files/Session%205%20-%2029%20Mordad_49_0.svg)
    

