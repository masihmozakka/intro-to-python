<div dir="rtl">



# جلسه هفتم، پنج شهریور

در جلسه گذشته با مفاهیم اولیه برنامه نویسی شی گرا آشنا شدیم، در این جلسه قصد داریم تا کمی بیشتر به کتابخانه های کاربری پایتون بپردازیم و دانش خود را کامل تر کنیم.

</div>


```python
# meaning of comma separated arguments:

x, y = 0, 1



# this is the same as:

# x = 0

# y = 1

print(x, y)
```

    0 1
    


```python
# in general, we can unpack any tuple of values

numbers = [1, 2, 3]

# but first we have to convert to a tuple

numbers = tuple(numbers)

x, y, z = numbers

print(x, 2*y)
```

    1 4
    


```python
# some functions also return more than one output

def func(n):

    return n, 2*n, 3*n



print(func(2))
```

    (2, 4, 6)
    


```python
# we can unpack the returned values too

def func(n):

    return n, 2*n, 3*n



x, y, z = func(2)

print(z)
```

    6
    

# Sympy



We have explored two packages so far; Numpy and Matplotlib. In this section, we will explore two more key packages for python: Sympy and csv



Sympy stands for Symbolic Python, its main purpose is symbolic computation (this is by itself a major area of computer science and applied mathematics). Sympy basically helps us do regular math using the computer!


```python
from math import sqrt

# perfect square

print(sqrt(4))

# not a perfect square

print(sqrt(8))
```

    2.0
    2.8284271247461903
    

We should have a tool that lets us figure out that

<a href="https://www.codecogs.com/eqnedit.php?latex=\huge&space;\sqrt{8}&space;=&space;2\sqrt{2}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\huge&space;\sqrt{8}&space;=&space;2\sqrt{2}" title="\huge \sqrt{8} = 2\sqrt{2}" /></a>


```python
# sympy allows us to do this, first we need to install it

# by running pip install sympy

# then we can write

import sympy

sympy.sqrt(3)
```

<a href="https://www.codecogs.com/eqnedit.php?latex=\huge&space;\displaystyle&space;\sqrt{3}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\huge&space;\displaystyle&space;\sqrt{3}" title="\huge \displaystyle \sqrt{3}" /></a>

```python
sympy.sqrt(8)
```



<a href="https://www.codecogs.com/eqnedit.php?latex=\huge&space;\displaystyle&space;2&space;\sqrt{2}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\huge&space;\displaystyle&space;2&space;\sqrt{2}" title="\huge \displaystyle 2 \sqrt{2}" /></a>


```python
from sympy import symbols

# the symbols function defines symbolic variables

x, y = symbols('x y')

expr = x + 2*y

expr
```

<a href="https://www.codecogs.com/eqnedit.php?latex=\huge&space;\displaystyle&space;x&space;&plus;&space;2&space;y" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\huge&space;\displaystyle&space;x&space;&plus;&space;2&space;y" title="\huge \displaystyle x + 2 y" /></a>



```python
# we can do most normal operations on an expression

expr + 1
```




    4




```python
# x is not a normal python variabld! its a symbolic variable now

expr - x
```
<a href="https://www.codecogs.com/eqnedit.php?latex=\huge&space;\displaystyle&space;2&space;y" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\huge&space;\displaystyle&space;2&space;y" title="\huge \displaystyle 2 y" /></a>

```python
# sympy will keep things simplified unless we tell it not to using the expand function

x*expr
```
<a href="https://www.codecogs.com/eqnedit.php?latex=\huge&space;\displaystyle&space;x&space;\left(x&space;&plus;&space;2&space;y\right)" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\huge&space;\displaystyle&space;x&space;\left(x&space;&plus;&space;2&space;y\right)" title="\huge \displaystyle x \left(x + 2 y\right)" /></a>

```python
# we can subsitute values to calculate expressions

# substitute the symbolic value x with 1

# remember that expr = x + 2y

expr.subs(x, 2)
```
<a href="https://www.codecogs.com/eqnedit.php?latex=\huge&space;\displaystyle&space;2&space;y&space;&plus;&space;2" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\huge&space;\displaystyle&space;2&space;y&space;&plus;&space;2" title="\huge \displaystyle 2 y + 2" /></a>

```python
# you can do more than one substitution using a list of tuples

substitutions = [(x, 1), (y, 2)]

expr.subs(substitutions)
```




    sympy.core.numbers.Integer




```python
# the expand function allows us to get a single computed expression

from sympy import expand

expanded_expr = expand(x*expr)

expanded_expr
```

<a href="https://www.codecogs.com/eqnedit.php?latex=\huge&space;\displaystyle&space;x^{2}&space;&plus;&space;2&space;x&space;y" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\huge&space;\displaystyle&space;x^{2}&space;&plus;&space;2&space;x&space;y" title="\huge \displaystyle x^{2} + 2 x y" /></a>

```python
# factor reverses the process

from sympy import factor

factor(expanded_expr)
```

<a href="https://www.codecogs.com/eqnedit.php?latex=\huge&space;\displaystyle&space;x&space;\left(x&space;&plus;&space;2&space;y\right)" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\huge&space;\displaystyle&space;x&space;\left(x&space;&plus;&space;2&space;y\right)" title="\huge \displaystyle x \left(x + 2 y\right)" /></a>

```python
# we can differenciate stuff

from sympy import *

x, t, z, nu = symbols('x t z nu')

# differenciate expression sin(x)*exp(x) with respect to x

diff_of_expression = diff(sin(x)*exp(x), x) # df/dx, f = sin(x)*exp(x)

diff_of_expression
```

<a href="https://www.codecogs.com/eqnedit.php?latex=\huge&space;\displaystyle&space;e^{x}&space;\sin{\left(x&space;\right)}&space;&plus;&space;e^{x}&space;\cos{\left(x&space;\right)}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\huge&space;\displaystyle&space;e^{x}&space;\sin{\left(x&space;\right)}&space;&plus;&space;e^{x}&space;\cos{\left(x&space;\right)}" title="\huge \displaystyle e^{x} \sin{\left(x \right)} + e^{x} \cos{\left(x \right)}" /></a>

```python
# lets compute the integral of this expression to see what we get

integrate(diff_of_expression, x)
```

<a href="https://www.codecogs.com/eqnedit.php?latex=\huge&space;\displaystyle&space;e^{x}&space;\sin{\left(x&space;\right)}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\huge&space;\displaystyle&space;e^{x}&space;\sin{\left(x&space;\right)}" title="\huge \displaystyle e^{x} \sin{\left(x \right)}" /></a>

```python
# we can also calculate limits

# sin(x)/x x -> 0

limit(z*sin(x)/x, x, 0)
```

<a href="https://www.codecogs.com/eqnedit.php?latex=\huge&space;\displaystyle&space;z" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\huge&space;\displaystyle&space;z" title="\huge \displaystyle z" /></a>

```python
# and solve equations

# this code solves x^2 - 2 = 0

ans = solve(x**2 - 2, x)

# returns a list

type(ans)
```




    list




```python
ans
```


<a href="https://www.codecogs.com/eqnedit.php?latex=\huge&space;\displaystyle&space;-1.4142135623731" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\huge&space;\displaystyle&space;-1.4142135623731" title="\huge \displaystyle -1.4142135623731" /></a>

```python
# sympy can evaluate numerical expressions by the evalf method

pi.evalf()
```


<a href="https://www.codecogs.com/eqnedit.php?latex=\huge&space;\displaystyle&space;3.14159265358979" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\huge&space;\displaystyle&space;3.14159265358979" title="\huge \displaystyle 3.14159265358979" /></a>

```python
# with arbitrary precision!

pi.evalf(50)
```

<a href="https://www.codecogs.com/eqnedit.php?latex=\huge&space;\displaystyle&space;3.1415926535897932384626433832795028841971693993751" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\huge&space;\displaystyle&space;3.1415926535897932384626433832795028841971693993751" title="\huge \displaystyle 3.1415926535897932384626433832795028841971693993751" /></a>


```python
# we can use sympy to simplify expressions

# indeed, cos^2 + sin^2 = 1

simplify(sin(x)**2 + cos(x)**2)
```




<a href="https://www.codecogs.com/eqnedit.php?latex=\huge&space;1" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\huge&space;1" title="\huge 1" /></a>




```python
simplify((x**3 + x**2 - x - 1)/(x**2 + 2*x + 1))
```


<a href="https://www.codecogs.com/eqnedit.php?latex=\huge&space;\displaystyle&space;x&space;-&space;1" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\huge&space;\displaystyle&space;x&space;-&space;1" title="\huge \displaystyle x - 1" /></a>


```python
simplify(gamma(x)/gamma(x - 2))
```


<a href="https://www.codecogs.com/eqnedit.php?latex=\huge&space;\displaystyle&space;\left(x&space;-&space;2\right)&space;\left(x&space;-&space;1\right)" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\huge&space;\displaystyle&space;\left(x&space;-&space;2\right)&space;\left(x&space;-&space;1\right)" title="\huge \displaystyle \left(x - 2\right) \left(x - 1\right)" /></a>

```python
# calculating binomial coefficients

binomial(5, 2)

# = 5!/3!2! = 120/(6*2) = 10
```

<a href="https://www.codecogs.com/eqnedit.php?latex=\huge&space;\displaystyle&space;10" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\huge&space;\displaystyle&space;10" title="\huge \displaystyle 10" /></a>


```python
# we used Symbols to create symbolic values

# we can now use Functions to create Functional values



y = Function('y')

# solve the differential equation y′′−y=e^t

eq = Eq(y(t).diff(t, t) - y(t), exp(t))

solved = dsolve(eq, y(t))

solved
```

<a href="https://www.codecogs.com/eqnedit.php?latex=\huge&space;\displaystyle&space;y{\left(t&space;\right)}&space;=&space;C_{2}&space;e^{-&space;t}&space;&plus;&space;\left(C_{1}&space;&plus;&space;\frac{t}{2}\right)&space;e^{t}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\huge&space;\displaystyle&space;y{\left(t&space;\right)}&space;=&space;C_{2}&space;e^{-&space;t}&space;&plus;&space;\left(C_{1}&space;&plus;&space;\frac{t}{2}\right)&space;e^{t}" title="\huge \displaystyle y{\left(t \right)} = C_{2} e^{- t} + \left(C_{1} + \frac{t}{2}\right) e^{t}" /></a>

```python
# we can substitute t = 1 to get a new expression

solved.subs(t, 1)
```


<a href="https://www.codecogs.com/eqnedit.php?latex=\huge&space;\displaystyle&space;y{\left(1&space;\right)}&space;=&space;\frac{C_{2}}{e}&space;&plus;&space;e&space;\left(C_{1}&space;&plus;&space;\frac{1}{2}\right)" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\huge&space;\displaystyle&space;y{\left(1&space;\right)}&space;=&space;\frac{C_{2}}{e}&space;&plus;&space;e&space;\left(C_{1}&space;&plus;&space;\frac{1}{2}\right)" title="\huge \displaystyle y{\left(1 \right)} = \frac{C_{2}}{e} + e \left(C_{1} + \frac{1}{2}\right)" /></a>

```python
# lets see a complete list of variables in our function

solved.free_symbols
```




    {C1, C2, t}




```python
# now lets create a specific function

C1, C2 = symbols("C1, C2")

f = solved.subs([(C1, 2), (C2, 1)])

f
```

<a href="https://www.codecogs.com/eqnedit.php?latex=\huge&space;\displaystyle&space;y{\left(t&space;\right)}&space;=&space;\left(\frac{t}{2}&space;&plus;&space;2\right)&space;e^{t}&space;&plus;&space;e^{-&space;t}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\huge&space;\displaystyle&space;y{\left(t&space;\right)}&space;=&space;\left(\frac{t}{2}&space;&plus;&space;2\right)&space;e^{t}&space;&plus;&space;e^{-&space;t}" title="\huge \displaystyle y{\left(t \right)} = \left(\frac{t}{2} + 2\right) e^{t} + e^{- t}" /></a>


```python
f.subs(t, 5)
```

<a href="https://www.codecogs.com/eqnedit.php?latex=\huge&space;\displaystyle&space;y{\left(5&space;\right)}&space;=&space;e^{-5}&space;&plus;&space;\frac{9&space;e^{5}}{2}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\huge&space;\displaystyle&space;y{\left(5&space;\right)}&space;=&space;e^{-5}&space;&plus;&space;\frac{9&space;e^{5}}{2}" title="\huge \displaystyle y{\left(5 \right)} = e^{-5} + \frac{9 e^{5}}{2}" /></a>

```python
f.subs(t, 5).evalf(40)
```


<a href="https://www.codecogs.com/eqnedit.php?latex=\huge&space;\displaystyle&space;y{\left(5&space;\right)}&space;=&space;667.8659539085938008621167462309084067299" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\huge&space;\displaystyle&space;y{\left(5&space;\right)}&space;=&space;667.8659539085938008621167462309084067299" title="\huge \displaystyle y{\left(5 \right)} = 667.8659539085938008621167462309084067299" /></a>

```python
# plotting with sympy

from sympy import symbols

from sympy.plotting import plot

# first make a free variable x

x = symbols('x')

# make two plots

p1 = plot(x*x, show=False)

p2 = plot(x, show=False)

# combine the two plots into one

p1.append(p2[0])

# show plot

p1.show()
```


    
![svg](Session%207%20-%205%20Shahrivar_files/Session%207%20-%205%20Shahrivar_35_0.svg)
    


## Simple example from physics

From Newton's second law we have

<a href="https://www.codecogs.com/eqnedit.php?latex=\huge&space;F&space;=&space;ma" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\huge&space;F&space;=&space;ma" title="\huge F = ma" /></a>

Where m is mass, a is acceleration and

<a href="https://www.codecogs.com/eqnedit.php?latex=\huge&space;a&space;=&space;\frac{d^2x}{dt^2}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\huge&space;a&space;=&space;\frac{d^2x}{dt^2}" title="\huge a = \frac{d^2x}{dt^2}" /></a>

if x denotes the position of the mass. Now, we know that if we have a spring and we attach a mass to it, then at position X the force on the mass from the spring is -kx (Hooke's law). So, for a simple spring and mass system we have

<a href="https://www.codecogs.com/eqnedit.php?latex=\huge&space;F=ma&space;\Rightarrow&space;-kx&space;=&space;m\frac{d^2x}{dt^2}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\huge&space;F=ma&space;\Rightarrow&space;-kx&space;=&space;m\frac{d^2x}{dt^2}" title="\huge F=ma \Rightarrow -kx = m\frac{d^2x}{dt^2}" /></a>

Lets solve this for a spring with k = 10 and a mass of m = 1 kilograms, we want to solve

<a href="https://www.codecogs.com/eqnedit.php?latex=\huge&space;-10x&space;=&space;\frac{d^2x}{dt^2}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\huge&space;-10x&space;=&space;\frac{d^2x}{dt^2}" title="\huge -10x = \frac{d^2x}{dt^2}" /></a>


```python
# lets first create our free variables

t = symbols('t')

x = Function('x')(t)

# lets write the equation out

eq = Eq(x.diff(t, t), -10*x)

eq
```



<a href="https://www.codecogs.com/eqnedit.php?latex=\huge&space;\displaystyle&space;\frac{d^{2}}{d&space;t^{2}}&space;x{\left(t&space;\right)}&space;=&space;-&space;10&space;x{\left(t&space;\right)}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\huge&space;\displaystyle&space;\frac{d^{2}}{d&space;t^{2}}&space;x{\left(t&space;\right)}&space;=&space;-&space;10&space;x{\left(t&space;\right)}" title="\huge \displaystyle \frac{d^{2}}{d t^{2}} x{\left(t \right)} = - 10 x{\left(t \right)}" /></a>


```python
# now lets solve this

solved = dsolve(eq, x)

solved
```


<a href="https://www.codecogs.com/eqnedit.php?latex=\huge&space;\displaystyle&space;x{\left(t&space;\right)}&space;=&space;C_{1}&space;\sin{\left(\sqrt{10}&space;t&space;\right)}&space;&plus;&space;C_{2}&space;\cos{\left(\sqrt{10}&space;t&space;\right)}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\huge&space;\displaystyle&space;x{\left(t&space;\right)}&space;=&space;C_{1}&space;\sin{\left(\sqrt{10}&space;t&space;\right)}&space;&plus;&space;C_{2}&space;\cos{\left(\sqrt{10}&space;t&space;\right)}" title="\huge \displaystyle x{\left(t \right)} = C_{1} \sin{\left(\sqrt{10} t \right)} + C_{2} \cos{\left(\sqrt{10} t \right)}" /></a>



```python
# for simplicity we can set C1 = C2 = 1

C1, C2 = symbols("C1, C2")

solved = solved.subs([(C1, 1), (C2, 1)])

solved
```



<a href="https://www.codecogs.com/eqnedit.php?latex=\huge&space;\displaystyle&space;x{\left(t&space;\right)}&space;=&space;\sin{\left(\sqrt{10}&space;t&space;\right)}&space;&plus;&space;\cos{\left(\sqrt{10}&space;t&space;\right)}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\huge&space;\displaystyle&space;x{\left(t&space;\right)}&space;=&space;\sin{\left(\sqrt{10}&space;t&space;\right)}&space;&plus;&space;\cos{\left(\sqrt{10}&space;t&space;\right)}" title="\huge \displaystyle x{\left(t \right)} = \sin{\left(\sqrt{10} t \right)} + \cos{\left(\sqrt{10} t \right)}" /></a>



```python
# lets get the right hand side of this equality and plot it

p1 = plot(solved.rhs, (t, 0, 10), show=False)

p1.show()


```


    
![svg](Session%207%20-%205%20Shahrivar_files/Session%207%20-%205%20Shahrivar_40_0.svg)
    


## csv

csv stands for comma separated variable. This is a built-in python package used for data manipulation and communication with files. csv is used to get data from external programs or processes such as other software or sensors in the field.


```python
import csv
```


```python
# with is a keyword that is used for error handling, read more about it if

# you want, we won't talk about it here

with open('WHO_dataset_1.csv') as csv_file:

    csv_reader = csv.reader(csv_file, delimiter=',')

    line_count = 0

    for row in csv_reader:

        if line_count == 0:

            print(f'Column names are {", ".join(row)}')

            line_count += 1

        else:

            pass



csv_file.close()
```

    Column names are ï»¿Name, WHO Region, Cases - cumulative total, Cases - cumulative total per 100000 population, Cases - newly reported in last 7 days, Cases - newly reported in last 7 days per 100000 population, Cases - newly reported in last 24 hours, Deaths - cumulative total, Deaths - cumulative total per 100000 population, Deaths - newly reported in last 7 days, Deaths - newly reported in last 7 days per 100000 population, Deaths - newly reported in last 24 hours
    


```python
# opening a csv file as a dict

with open('WHO_dataset_1.csv', mode='r') as csv_file:

    csv_reader = csv.DictReader(csv_file)

    line_count = 0

    for row in csv_reader:

        # nevermind this, its just to fix the data

        if None in row:

            row.pop(None)

        if line_count == 0:

            print("statistics for the world as of today are:")

            for i in row:

                print(i + ":", row[i])

        for i in row:

            print(i + ":", row[i])

csv_file.close()
```


```python
# lets get the statistics of iran

with open('WHO_dataset_1.csv', mode='r') as csv_file:

    csv_reader = csv.DictReader(csv_file)

    line_count = 0

    for row in csv_reader:

        if row["ï»¿Name"] == 'Iran (Islamic Republic of)':

            print("statistics for Iran as of today are:")

            for i in row:

                print(i + ":", row[i])

            break

csv_file.close()
```

    statistics for Iran as of today are:
    ï»¿Name: Iran (Islamic Republic of)
    WHO Region: Eastern Mediterranean
    Cases - cumulative total: 4796377
    Cases - cumulative total per 100000 population: 5710.45
    Cases - newly reported in last 7 days: 239960
    Cases - newly reported in last 7 days per 100000 population: 285.69
    Cases - newly reported in last 24 hours: 39983
    Deaths - cumulative total: 104022
    Deaths - cumulative total per 100000 population: 123.85
    Deaths - newly reported in last 7 days: 4331
    Deaths - newly reported in last 7 days per 100000 population: 5.16
    Deaths - newly reported in last 24 hours: 665
    


```python
# lets get cases per 100,000 population so that we can plot it against

# deaths per 100,000 population

cases = []

deaths = []

countries = []

with open('WHO_dataset_1.csv', mode='r') as csv_file:

    csv_reader = csv.DictReader(csv_file)

    line_count = 0

    for row in csv_reader:

        if row["Cases - cumulative total per 100000 population"] == "" or row["Deaths - cumulative total per 100000 population"] == "":

            continue

        cases.append(float(row["Cases - cumulative total per 100000 population"]))

        deaths.append(float(row["Deaths - cumulative total per 100000 population"]))

        countries.append(row["ï»¿Name"])

csv_file.close()
```


```python
cases
```



```python
# now lets plot the data

import matplotlib.pyplot as plt

plt.plot(deaths, cases, 'ro')

plt.show()
```


    
![svg](Session%207%20-%205%20Shahrivar_files/Session%207%20-%205%20Shahrivar_48_0.svg)
    



```python
# lets compare log(cases) to deaths

import numpy as np

log_cases = [np.log(i) for i in cases]

plt.plot(log_cases, deaths, 'ro')

plt.show()
```

    C:\Users\98937\AppData\Local\Temp/ipykernel_16484/2857902635.py:3: RuntimeWarning: divide by zero encountered in log
      log_cases = [np.log(i) for i in cases]
    


    
![svg](Session%207%20-%205%20Shahrivar_files/Session%207%20-%205%20Shahrivar_49_1.svg)
    



```python
# turn the data into a dictionary

data = {}

for i in range(0, len(countries)):

    data[countries[i]] = [cases[i], deaths[i]]



print(data)
```

    {'Global': [2742.3382541497726, 57.21159676658748], 'United States of America': [11471.02, 189.17], 'India': [2359.31, 31.62], 'Brazil': [9698.4, 270.86], 'Russian Federation': [4676.44, 122.82], 'The United Kingdom': [9708.56, 194.45], 'France': [9984.41, 172.86], 'Turkey': [7438.64, 65.46], 'Argentina': [11390.63, 245.17], 'Colombia': [9619.54, 244.46], 'Spain': [10173.12, 176.81], 'Iran (Islamic Republic of)': [5710.45, 123.85], 'Italy': [7549.1, 216.15], 'Indonesia': [1472.21, 47.27], 'Germany': [4691.54, 110.72], 'Mexico': [2520.6, 197.36], 'Poland': [7607.02, 198.46], 'South Africa': [4589.89, 135.68], 'Ukraine': [5209.18, 122.48], 'Peru': [6501.58, 600.34], 'Netherlands': [11066.58, 103.25], 'Philippines': [1718.44, 29.65], 'Iraq': [4593.69, 50.74], 'Czechia': [15694.23, 284.21], 'Chile': [8553.86, 192.08], 'Malaysia': [4993.65, 45.78], 'Bangladesh': [900.26, 15.62], 'Canada': [3911.14, 71.14], 'Japan': [1077.52, 12.44], 'Belgium': [10181.07, 219.99], 'Pakistan': [514.21, 11.42], 'Thailand': [1605.83, 14.78], 'Sweden': [10850.82, 142.09], 'Romania': [5659.54, 178.34], 'Portugal': [9963.85, 171.66], 'Israel': [11831.73, 79.82], 'Kazakhstan': [4419.97, 67.4], 'Morocco': [2246.34, 32.73], 'Hungary': [8306.62, 307.65], 'Jordan': [7765.05, 101.32], 'Switzerland': [8802.6, 120.28], 'Nepal': [2583.89, 36.42], 'Serbia': [10808.79, 104.42], 'United Arab Emirates': [7203.05, 20.5], 'Austria': [7591.69, 118.78], 'Tunisia': [5478.5, 193.42], 'Cuba': [5395.81, 42.43], 'Lebanon': [8725.03, 117.56], 'Greece': [5318.59, 126.03], 'Saudi Arabia': [1559.8, 24.43], 'Georgia': [13340.38, 176.18], 'Ecuador': [2829.42, 181.96], 'Bolivia (Plurinational State of)': [4178.19, 157.03], 'Belarus': [5004.08, 39.28], 'Paraguay': [6420.87, 218.9], 'Panama': [10509.63, 162.65], 'Costa Rica': [8788.02, 105.57], 'Bulgaria': [6425.94, 267.76], 'Guatemala': [2483.45, 64.48], 'Kuwait': [9572.42, 56.48], 'Sri Lanka': [1904.28, 37.12], 'Azerbaijan': [3963.12, 53.29], 'Slovakia': [7227.1, 229.89], 'Uruguay': [11062.66, 173.3], 'Viet Nam': [391.79, 9.6], 'Myanmar': [700.02, 27.09], 'Croatia': [9157.41, 204.92], 'occupied Palestinian territory, including east Jerusalem': [7059.24, 76.88], 'Dominican Republic': [3213.21, 36.93], 'Ireland': [6895.62, 102.57], 'Denmark': [5848.89, 44.15], 'Honduras': [3345.64, 87.88], 'Venezuela (Bolivarian Republic of)': [1151.54, 13.8], 'Oman': [5907.68, 79.25], 'Libya': [4372.61, 60.05], 'Ethiopia': [261.03, 4.0], 'Lithuania': [10597.22, 161.52], 'Egypt': [280.39, 16.31], 'Bahrain': [15981.25, 81.57], 'Republic of Moldova': [6589.48, 158.16], 'Slovenia': [12627.27, 227.59], 'Republic of Korea': [474.59, 4.4], 'Armenia': [8090.45, 161.48], 'Kenya': [431.55, 8.55], 'Qatar': [8037.3, 20.86], 'Bosnia and Herzegovina': [6433.13, 297.43], 'Zambia': [1115.68, 19.51], 'Mongolia': [6078.6, 27.85], 'Algeria': [440.52, 11.62], 'Nigeria': [91.63, 1.11], 'Kyrgyzstan': [2679.46, 38.36], 'North Macedonia': [8235.46, 276.23], 'Puerto Rico': [5798.93, 97.1], 'Afghanistan': [392.57, 18.22], 'Uzbekistan': [455.23, 3.14], 'Norway': [2833.92, 15.17], 'Botswana': [6414.37, 92.32], 'Mozambique': [460.82, 5.83], 'Latvia': [7427.16, 134.77], 'Albania': [4912.26, 86.28], 'Estonia': [10560.09, 96.77], 'Kosovo[1]': [7505.57, 131.43], 'Finland': [2249.38, 18.42], 'Namibia': [4881.41, 131.69], 'Zimbabwe': [832.35, 29.19], 'China': [8.35, 0.39], 'Ghana': [371.79, 3.16], 'Cyprus': [12643.85, 54.73], 'Montenegro': [17790.6, 269.88], 'Uganda': [215.41, 6.49], 'El Salvador': [1450.15, 44.14], 'Cambodia': [541.51, 10.98], 'Rwanda': [653.41, 8.09], 'Cameroon': [314.27, 5.09], 'Maldives': [14860.58, 41.62], 'Luxembourg': [12028.6, 132.56], 'Senegal': [431.29, 10.19], 'Singapore': [1142.02, 0.89], 'Jamaica': [2155.6, 48.33], 'Malawi': [313.4, 11.04], 'Democratic Republic of the Congo': [60.55, 1.18], 'CÃ´te dâ€™Ivoire': [204.86, 1.57], 'RÃ©union': [5437.55, 37.08], 'Australia': [183.25, 3.87], 'Angola': [141.6, 3.58], 'Fiji': [4991.38, 51.2], 'Trinidad and Tobago': [3097.13, 88.89], 'Madagascar': [154.74, 3.45], 'Eswatini': [3592.6, 89.81], 'French Polynesia': [14302.9, 125.66], 'Guadeloupe': [9485.81, 106.72], 'Sudan': [85.97, 6.36], 'Malta': [6978.34, 84.93], 'Cabo Verde': [6280.54, 55.4], 'Martinique': [9252.66, 77.55], 'French Guiana': [11290.27, 69.64], 'Mauritania': [698.68, 14.71], 'Guinea': [220.99, 2.42], 'Suriname': [4734.83, 120.01], 'Syrian Arab Republic': [155.54, 11.34], 'Gabon': [1157.46, 7.41], 'Guyana': [3115.62, 76.41], 'Haiti': [182.71, 5.12], 'Togo': [244.53, 2.11], 'Seychelles': [20138.9, 103.71], 'Mayotte': [7230.54, 64.15], 'Papua New Guinea': [200.9, 2.15], 'Bahamas': [4479.41, 87.22], 'Somalia': [107.06, 5.9], 'Tajikistan': [178.31, 1.31], 'Belize': [3944.14, 89.28], 'Timor-Leste': [1160.15, 3.94], 'CuraÃ§ao': [9168.58, 85.32], 'Andorra': [19431.83, 168.25], 'Mali': [73.06, 2.65], 'Lesotho': [671.63, 18.81], 'Aruba': [13256.09, 119.89], "Lao People's Democratic Republic": [191.17, 0.15], 'Burkina Faso': [65.72, 0.82], 'Congo': [245.25, 3.32], 'Benin': [103.04, 1.05], 'Burundi': [99.39, 0.08], 'Djibouti': [1184.92, 15.89], 'South Sudan': [101.37, 1.07], 'Central African Republic': [233.34, 2.05], 'Iceland': [2867.9, 8.51], 'Gambia': [394.47, 12.87], 'Guam': [5482.45, 85.91], 'Equatorial Guinea': [653.82, 8.77], 'Jersey': [8505.88, 70.5], 'Nicaragua': [133.85, 3.0], 'Mauritius': [681.49, 2.12], 'Yemen': [25.56, 4.82], 'Saint Lucia': [4041.34, 53.91], 'Eritrea': [187.09, 1.04], 'Isle of Man': [7547.75, 34.1], 'Sierra Leone': [79.7, 1.52], 'Niger': [23.99, 0.82], 'United States Virgin Islands': [5443.14, 48.84], 'Guinea-Bissau': [286.28, 5.59], 'Liberia': [109.5, 4.84], 'Gibraltar': [15754.95, 284.94], 'San Marino': [15631.45, 265.19], 'Chad': [30.36, 1.06], 'Barbados': [1633.41, 16.7], 'Comoros': [466.31, 16.9], 'Sint Maarten': [8208.57, 107.27], 'Liechtenstein': [8669.06, 149.69], 'Monaco': [8059.83, 89.19], 'Saint Martin': [8140.41, 43.97], 'New Zealand': [59.54, 0.54], 'Bermuda': [4483.48, 52.99], 'Turks and Caicos Islands': [6756.55, 51.66], 'Bhutan': [335.79, 0.39], 'British Virgin Islands': [8492.91, 122.37], 'Sao Tome and Principe': [1165.82, 16.88], 'Saint Vincent and the Grenadines': [2092.12, 10.82], 'Brunei Darussalam': [493.51, 1.37], 'Bonaire': [8343.29, 81.28], 'Saint BarthÃ©lemy': [15710.67, 10.12], 'Antigua and Barbuda': [1572.57, 43.91], 'United Republic of Tanzania': [2.29, 0.08], 'Dominica': [1859.95, 1.39], 'Guernsey': [1853.63, 27.92], 'Faroe Islands': [2044.41, 4.09], 'Saint Kitts and Nevis': [1746.5, 5.64], 'Cayman Islands': [1017.95, 3.04], 'Wallis and Futuna': [4036.99, 62.24], 'Greenland': [551.33, 0.0], 'Northern Mariana Islands (Commonwealth of the)': [403.08, 3.47], 'Grenada': [204.4, 0.89], 'Anguilla': [1159.85, 0.0], 'New Caledonia': [47.29, 0.0], 'Falkland Islands (Malvinas)': [1837.5, 0.0], 'Saint Pierre and Miquelon': [517.69, 0.0], 'Holy See': [3213.84, 0.0], 'Montserrat': [500.1, 20.0], 'Sint Eustatius': [764.57, 0.0], 'Solomon Islands': [2.91, 0.0], 'Saba': [517.33, 0.0], 'Marshall Islands': [6.76, 0.0], 'Vanuatu': [0.98, 0.0], 'Palau': [11.05, 0.0], 'Samoa': [0.5, 0.0], 'American Samoa': [0.0, 0.0], 'Cook Islands': [0.0, 0.0], "Democratic People's Republic of Korea": [0.0, 0.0], 'Kiribati': [0.0, 0.0], 'Micronesia (Federated States of)': [0.0, 0.0], 'Nauru': [0.0, 0.0], 'Niue': [0.0, 0.0], 'Pitcairn Islands': [0.0, 0.0], 'Saint Helena': [0.0, 0.0], 'Tokelau': [0.0, 0.0], 'Tonga': [0.0, 0.0], 'Turkmenistan': [0.0, 0.0], 'Tuvalu': [0.0, 0.0]}
    


```python
plt.hist(cases)

plt.show()
```


    
![svg](Session%207%20-%205%20Shahrivar_files/Session%207%20-%205%20Shahrivar_51_0.svg)
    



```python
# the rotation parameter rotates our labels

plt.figure(figsize=(45,4))

plt.bar(countries, cases)

plt.xticks(rotation='vertical', fontsize=9)
```
    
![svg](Session%207%20-%205%20Shahrivar_files/Session%207%20-%205%20Shahrivar_52_1.svg)
    



```python
# the rotation parameter rotates our labels

plt.figure(figsize=(45,4))



ratio_list = []

for i in range(0, len(cases)):

    if cases[i] != 0:

        ratio_list.append(deaths[i]/cases[i])

    else:

        ratio_list.append(0)

        

print(len(countries), len(ratio_list))

plt.bar(countries, ratio_list)

plt.xticks(rotation='vertical', fontsize=9)
```

    
![svg](Session%207%20-%205%20Shahrivar_files/Session%207%20-%205%20Shahrivar_53_2.svg)
    



```python
plt.plot(ratio_list, 'ro')
```




    [<matplotlib.lines.Line2D at 0x2e834ba12b0>]




    
![svg](Session%207%20-%205%20Shahrivar_files/Session%207%20-%205%20Shahrivar_54_1.svg)
    


### Exercise:

Write a program that _builds a coordinate system_, it should store points as objects, have a method to print the information of the vector (using str), have a method to calculate the length of a vector by the formula

$len = \sqrt{x^2 + y^2}$, it should also have a way of determining which vector is bigger than another using the `<` operator. If a vector has a bigger size than another one, the `<` operator should return True. 

### Exercise:

solve the following differential equation (this equation models a damped oscillator):

$$2\frac{d^2x}{dt^2} + \frac{dx}{dt} + x = 0$$

and plot the resulting graph.


```python
# lets get cases per 100,000 population so that we can plot it against

# deaths per 100,000 population

cases = []

deaths = []

date = []

ratio = []

with open('owid-covid-data.csv', mode='r') as csv_file:

    csv_reader = csv.DictReader(csv_file)

    line_count = 0

    for row in csv_reader:

        if row["iso_code"] == "IRN":

            cases.append(float(row["new_cases"]))

            deaths.append(float(row["new_deaths"]))

            date.append(row["date"])



for i in range(0, len(cases)):

    if cases[i] != 0:

        ratio.append(deaths[i]/cases[i])

    else:

        ratio.append(0)



log_cases = [np.log(i) for i in cases]

csv_file.close()
```


```python
print(date.index("2021-02-09"))

print(date.index("2021-06-08"))

print(date.index("2021-07-18"))
```

    356
    475
    515
    


```python
plt.figure(figsize=(15,4))

plt.xticks(rotation='vertical', fontsize=9)

plt.plot(np.array(deaths)/np.array(log_cases))

plt.plot(deaths)

plt.axvline(356, linestyle="--", color="red", label="start of vaccinations")

plt.axvline(475, linestyle="--", color="green", label="4 million doses")

plt.axvline(515, linestyle="--", color="yellow", label="start of second phase of vaccinations, starting from 4.4 million total")

plt.legend()

plt.show()
```


    
![svg](Session%207%20-%205%20Shahrivar_files/Session%207%20-%205%20Shahrivar_59_0.svg)
    



```python

```
