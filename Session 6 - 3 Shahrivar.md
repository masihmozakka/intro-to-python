<div dir="rtl">

# جلسه ششم،‌ سوم شهریور
در این جلسه قصد داریم تا با برنامه نویسی شئ‌گرا در پایتون آشنا شویم. تا اینجای کار صرفا به صورت 
Procedural Programming
پیش می‌رفت.
</div>

<div dir="rtl">

فرض کنید که می‌خواهیم اطلاعات کارمندان یک شرکت را نگه داریم، با اطلاعات کنونیمان بهترین راه استفاده از یک لیست بنظر می‌آید.
</div>


```python
kirk = ["James Kirk", 34, "Captain", 2265]
spock = ["Spock", 35, "Science Officer", 2254]
mccoy = ["Leonard McCoy", "Chief Medical Officer", 2266]
```

<div dir="rtl">

اما این روش مشکلاتی دارد، مثلا ممکن است شما بر روی فایل بزرگی کار کنید و برایتان سخت باشد که همیشه به یاد داشته باشید که 
`kirk[0]`
نام یک کارمند را می دهد. یا، باید همیشه به یاد داشته باشیم که سن 
`spock`
موجود نیست و برنامه را با توجه به آن تغییر دهیم.

مفهوم کارمند چه چیزی را به یاد شما می‌آورد؟ وقتی که به کلمه کارمند فکر می‌کنیم به طور اتوماتیک به ویژگی هایی مانند شغل، محل کار و نام و نام خانوادگی فکر می‌کنیم که بین تمامی کارمندان مشترک است. در واقع، یک «کلاس» از کارمندان داریم که تعدادی «نمونه» از این کارمندان ساخته می شود.
</div>


```python
class Employee:
    pass
```


```python
# the first function we will learn about is __init__, it creates the variables of each specific object
# classes are like blueprints, objects are like specific examples

class Employee:
    def __init__(self, n, a):
        self.name = n
        self.age = a

# self means that specific object, instead of the whole class
```




    20




```python
masih = Employee("masih", "20")
employee_2 = Employee("ali", "24")
print(masih.name)
print(employee_2.age)
print(type(masih))
```

    masih
    24
    <class '__main__.Employee'>
    


```python
# class attribute vs object attribute
class Employee:
    # class attribute
    # class attributes have to be defined outside of __init__
    company = "amirkabir university of technology"
    def __init__(self, name, age):
        # object attribute
        self.name = name
        self.age = age
```


```python
masih = Employee("masih", "20")
masih.age = "21"
employee_2 = Employee("ali", "24")
print(masih.age)
print(employee_2.age)
print(masih.company, employee_2.company)
```

    21
    24
    amirkabir university of technology amirkabir university of technology
    


```python
# methods
# a function that is defined inside of a class is called a method

class Employee:
    # class attribute
    company = "amirkabir university of technology"
    def __init__(self, name, age):
        # object attribute
        self.name = name
        self.age = age

    # Instance method
    def description(self):
        return f"{self.name} is {self.age} years old"

    # Another instance method
    def speak(self, sound):
        return f"{self.name} says {sound}"

masih = Employee("masih", "21")
masih.description()
```




    'masih is 21 years old'




```python
# printing objects
print(masih)
print(employee_2)
```

    <__main__.Employee object at 0x0000024DF62EECD0>
    <__main__.Employee object at 0x0000024DF62EE7C0>
    


```python
# the __str__ method 
class Employee:
    # class attribute
    company = "amirkabir university of technology"

    # the init method helps us initialize the method
    def __init__(self, name, age):
        # object attribute
        self.name = name
        self.age = age

    # the __str__ method helps us to print info about the object
    def __str__(self):
        return f"{self.name} is an object, not a person, and they are {self.age} years old"

    # Instance method
    def description(self):
        return f"{self.name} is {self.age} years old"

    # Another instance method
    def speak(self, sound):
        return f"{self.name} says {sound}"

masih = Employee("masih", 21)
print(masih)
```

    masih is an object, not a person, and they are 21 years old
    

<div>

## Inheritence
there are 3 main features that make object oriented programming unique (OOP); inheritence, polymorphism and encapsulation.
</div>


```python
# first we make a class called person
class Person:
    def __init__(self, name, age):
        self.name_of_person = name
        self.age_of_person  = age

```


```python
# now we make a class called employee which inherits from person

class Employee(Person):
    def __init__(self, name, age, company):
        super().__init__(name, age)
        self.company = company

masih = Employee("masih", 21, "aut")
print(masih.name_of_person)
```

    masih
    

## Encapsulation


```python
# first we make a class
class Counter:
    def __init__(self):
        self.current = 0

    def increment(self):
        self.current += 1

    def value(self):
        return self.current

    def reset(self):
        self.current = 0
```


```python
# now we can run this class
counter = Counter()


counter.increment()
counter.increment()
counter.increment()

print(counter.value())
```

    3
    


```python
# but we can change values from outside of class

counter = Counter()

counter.increment()
counter.increment()
counter.current = -999

print(counter.value())
```

    -999
    


```python
# encapsulation lets us hide data from outside of the class to improve program consistancy and security
# members with double underscore (__) are private and cannot be accessed from outside of class
class Counter:
    def __init__(self):
        self.__current = 0

    def increment(self):
        self.__current += 1

    def value(self):
        return self.__current

    def reset(self):
        self.__current = 0

counter = Counter()

print(counter.__current)
```


    ---------------------------------------------------------------------------

    AttributeError                            Traceback (most recent call last)

    ~\AppData\Local\Temp/ipykernel_2400/3131441731.py in <module>
         15 
         16 counter = Counter()
    ---> 17 print(counter.__current)
    

    AttributeError: 'Counter' object has no attribute '__current'



```python
# but you still have access by writing
counter = Counter()
counter.increment()

# name mangling
print(counter._Counter__current)
```

    1
    

Advanced students: You can read more about how underscores work in python from [this link](https://dbader.org/blog/meaning-of-underscores-in-python)

# Polymorphism
This is where the meaning of an operator changes depending on its left and right operands.


```python
# here, the + operator means add two numbers together
num1 = 1
num2 = 2
print(num1+num2)

# here, it means to attach strings together
str1 = "Python"
str2 = "Programming"
print(str1+" "+str2)

# this is basically polymorphism, the meaning of an operator changes
# depending on the operands
```

    3
    Python Programming
    


```python
# polymorphic function
print(len("Programiz"))
print(len(["Python", "Java", "C"]))
print(len({"Name": "John", "Address": "Nepal"}))
```

    9
    3
    2
    


```python
# polymorphism in variables

class Cat:
    def __init__(self, name, age):
        self.name = name
        self.age = age

    def info(self):
        print(f"I am a cat. My name is {self.name}. I am {self.age} years old.")

    def make_sound(self):
        print("Meow")


class Dog:
    def __init__(self, name, age):
        self.name = name
        self.age = age

    def info(self):
        print(f"I am a dog. My name is {self.name}. I am {self.age} years old.")

    def make_sound(self):
        print("Bark")


cat1 = Cat("Kitty", 2.5)
dog1 = Dog("Fluffy", 4)

# python knows when "animal" refers to a cat and when it refers to a dog
for animal in [cat1, dog1]:
    animal.make_sound()
    animal.info()
    animal.make_sound()
```

    Meow
    I am a cat. My name is Kitty. I am 2.5 years old.
    Meow
    Bark
    I am a dog. My name is Fluffy. I am 4 years old.
    Bark
    


```python
# we can redefine methods when we create child classes
from math import pi
class Shape:
    def __init__(self, name):
        self.name = name

    def area(self):
        pass

    def fact(self):
        return "I am a two-dimensional shape."

    def __str__(self):
        return self.name


class Square(Shape):
    def __init__(self, length):
        super().__init__("Square")
        self.length = length

    def area(self):
        return self.length**2

    def fact(self):
        return "Squares have each angle equal to 90 degrees."


class Circle(Shape):
    def __init__(self, radius):
        super().__init__("Circle")
        self.radius = radius

    def area(self):
        return pi*self.radius**2


a = Square(4)
b = Circle(7)
print(b)
print(b.fact())
print(a.fact())
print(b.area())
```

    Circle
    I am a two-dimensional shape.
    Squares have each angle equal to 90 degrees.
    153.93804002589985
    

## Operator Overloading


```python
class Point:
    def __init__(self, x=0, y=0):
        self.x = x
        self.y = y


p1 = Point(1, 2)
p2 = Point(2, 3)
print(p1+p2)
```


    ---------------------------------------------------------------------------

    TypeError                                 Traceback (most recent call last)

    ~\AppData\Local\Temp/ipykernel_2400/1142224220.py in <module>
          7 p1 = Point(1, 2)
          8 p2 = Point(2, 3)
    ----> 9 print(p1+p2)
    

    TypeError: unsupported operand type(s) for +: 'Point' and 'Point'



```python
class Point:
    def __init__(self, x=0, y=0):
        self.x = x
        self.y = y

    def __str__(self):
        return "({0},{1})".format(self.x, self.y)

    # here is where we overload the + operator
    def __add__(self, other):
        x = self.x + other.x
        y = self.y + other.y
        return Point(x, y)
```


```python
p1 = Point(1, 2)
p2 = Point(2, 3)

print(p1+p2)
```

    <class '__main__.Point'>
    

Advanced students: A complete list of overloading functions is available at [this link](https://www.programiz.com/python-programming/operator-overloading)

### Exercise:
Write a program that _builds a coordinate system_, it should store points as objects, have a method to print the information of the vector (using str), have a method to calculate the length of a vector by the formula
$len = \sqrt{x^2 + y^2}$, it should also have a way of determining which vector is bigger than another using the `<` operator. If a vector has a bigger size than another one, the `<` operator should return True. 

## args and kwargs

In the previous example, what if we wanted to create a system that takes it as many points as we'd like? As a simpler example, consider this function:


```python
# this works fine, but it should be easy to add more than 2 numbers right?
def my_sum(a, b):
    return a + b

print(my_sum(1, 2))
```

    3
    


```python
# WRONG, YOU CANT!
print(my_sum(1, 2, 3))
```


    ---------------------------------------------------------------------------

    TypeError                                 Traceback (most recent call last)

    ~\AppData\Local\Temp/ipykernel_2400/2246072414.py in <module>
          1 # WRONG, YOU CANT!
    ----> 2 print(my_sum(1, 2, 3))
    

    TypeError: my_sum() takes 2 positional arguments but 3 were given



```python
# this should work, buts its not ideal
def my_sum(my_integers):
    # result = 0
    # for x in my_integers:
    #     result += x
    # return result
    return sum(my_integers)

# we dont want this:
# data -> list -> data -> result
# we want this:
# data -> result

list_of_integers = [1, 2, 3]
print(my_sum(list_of_integers))
```

    6
    


```python
# python takes positional arguements then turns them into a tuple
# packing
def my_sum(*args):
    result = 0
    # Iterating over the Python args tuple
    print(args)
    for x in args:
        result += x
    return result

print(my_sum(1, 2))
```

    (1, 2)
    3
    


```python
# but what does * mean?
# unpack
print(*[1, 2, 3])
print(1, 2, 3)
# is same as print(1, 2, 3)
```

    1 2 3
    1 2 3
    


```python
# you can also include more arguments before *args
# python automatically assigns the first argument we pass into the function
# ("masih") to name and sends the rest to *args
def my_sum(name, *args):
    result = 0
    # Iterating over the Python args tuple
    print(name)
    for x in args:
        result += x
    return result

print(my_sum("masih", 1, 2, 3))
```

    masih
    6
    


```python
# we also have kwargs
# python creates a dictionary from the keyword arguements
def concatenate(**kwargs):
    result = ""
    print(kwargs)
    # Iterating over the Python kwargs dictionary
    for arg in kwargs.values():
        result += arg
    return result

print(concatenate(a="Real", b="Python", c="Is", d="Great", e="!"))
```

    {'a': 'Real', 'b': 'Python', 'c': 'Is', 'd': 'Great', 'e': '!'}
    RealPythonIsGreat!
    


```python
# args has to come before kwargs
def my_function(a, b, *args, **kwargs):
    print(a, b)
    print(args)
    print(kwargs)

# python assigns first value to a, then second value to b
# then assigns values to args until it gets to a keyword arguement
# then assigns to kwargs
my_function("hello", "world", 1, 2, 3, 4, name="masih")
```

    hello world
    (1, 2, 3, 4)
    {'name': 'masih'}
    


```python
# fun fact, you can return a tuple of values from a function
def func():
    return 1, 2, 3, 4

var = func()
print(type(var))
print(var)
```

    <class 'tuple'>
    (1, 2, 3, 4)
    


```python

```
