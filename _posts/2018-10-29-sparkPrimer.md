---
title: "Intro to Scala"
date: 2018-10-29
category: blog
tags: [development, data, blog]
header:
    image: "/images/pyScalaHeader1.jpg"
excerpt: "Some notes I took while learning Scala as a JavaScript/Python developer"
---

## Hello there! Today I'll be sharing with you some notes about how to learn Scala

Now, let's be frank. Scala is a _sexy_ language (in the context of Data Science (which is itself a _sexy_ field :smiley:)). If you want to write high-quality, production-grade data science/engineering code, the language Scala often comes up as the statically-typed language of choice. 

Now, of course, Python is the de-facto king of data science and ML prototyping. With it's many popular libraries, easy-to-use dynamically-typed syntax, and vibrant data science community that makes sense. So if you've been working a lot with Python, why learn Scala? 

**Benefits of Scala**
1. Performance - As the scope of your project increases, the engineering benefits of Scala will begin to make a difference. If your datasets can fit in memory, maybe Python will suffice. But as you begin to work with Big Data (and use [Apache Spark](https://spark.apache.org/), for instance), Scala will give you [significant](https://qr.ae/TUhGEh) improvements. This is partially due to it being compiled in the Java Virtual Machine. It is also due to the [tool-kit](https://en.wikipedia.org/wiki/Akka_(toolkit)) and many libraries that support concurrent and distributed computing in Scala. 
<sub>*Note* in some cases Python (and certain Python libraries) can actually outperform Scala. And of course, benchmarks can never make up for inefficient code.</sub> 
2. Catching Errors Early (aka workflow) - Because it is statically typed, coding in Scala with an IDE like IntelliJ can help you catch runtime exceptions before you ever compile.

That being said, Scala is not a panacea. There are good reasons to continue using and master Python:


**Benefits of Python**
1. Learning Curve - Python makes it fun and easy to dive into programming.
2. Extensive Support - There are so many powerful, high-level libraries for python. See [Keras](https://keras.io) (deep learning), [spaCy](https://spacy.io/) (NLP), or [Scikit-learn](scikit-learn.org/
) (general ML)

At the end of the day, it's better to get really good at one language than ok at two. Still, having some experience in a statically-typed language is really worthwhile as a data scientist or engineer. With that in mind, I set out to learn a bit of Scala, and share with you what I learned.

## Lesson 0: Online or Off?
If you'd like to jump right in and get coding, you can use an in-browser Scala environment like [ScalaFiddle](https://scalafiddle.io/) (I recommend this because it compiles faster) or [Scastie](https://scastie.scala-lang.org/).

If you'd like to run Scala code offline (and maybe begin putting together a project), then follow [these instructions](https://docs.scala-lang.org/getting-started.html#if-prefer-working-in-an-ide) to install the prerequisite software/packages. 

If you're like me (_read_ impatient), you just want to dive in and learn! If so you can use the useful site [Scala Exercises](https://www.scala-exercises.org/). You can also follow along with me, as I'll digest the most important  differences/similarities to Python.

## Lesson 1: The Basics

**Methods or Functions:**

```python
# Python
def square(x):
    return x*x
```
```scala
/* In Scala you need to define the type
of the parameter with a colon. */
def square(x: Int) = x*x
/*
square(5) --> 25
square(6.3) --> type mismatch Error
*/
def square(x: Double) = x*x
/*
square(6.3) --> 39.69
*/
```
```scala
/* You can optionally define the type of the return value
NOTE: If your function is recursive, an explicity return type is needed
 */
def square(x: Double): Int = x*x
/*
square(5) --> 25
square(6.3) --> type mismatch Error
*/
def square(x: Double): Double = x*x
/*
square(6.3) --> 39.69
*/
```
**val, def, and var:**

As we've seen `def` is used to immutably define a function. Now, `val` and `var` are used to define variables, with the important difference that `val is immutable` and `var is mutable`. By default, _Scala prefers immutable types_. 

So, what's the difference between `val` and `def`? `val` is evaluated once it is defined, and does not modify after that. On the other hand, `def` is evaluated every time it is used (hence why it is used to define functions). Note that when a function doesn't require any parameters, no parentheses are required. So in the following example, `y` is still techincally a function!: 

```scala
var x = 15 // mutable
def y = x + 8 // immutable, but evaluates lazily 
val z = x + 8 // immutable, already 23 by this line
println(y, z) // --> (23, 23)
x -= 10 
println(y, z) // --> (13, 23)
```

An interesting example used in scala-exercises.org:
```scala
def loop: Int = loop // returns itself
def x = loop // won't evaluate until called
val y = loop // causes an infinite loop as it tries to evaluate loop
```
I'm sure you already know this, but in python everything goes!
```python
x = "hi"
y = 55
def q():
    return y - 13
print(q()) # --> 42
y -= 15
print(q()) # --> 27
q = x
print(q) # --> hi
```

**File, Package, and Object Organization:**
In Scala, 

**Standalone Executable Programs**

**Tail Recursion in Scala**

## Lesson 2: Functional Programming
What is FP? According to Wikipedia, 
>>In functional code, the output value of a function depends only on the arguments that are passed to the function, so calling a function f twice with the same value for an argument x produces the same result f(x) each time; this is in contrast to procedures depending on a local or global state, which may produce different results at different times when called with the same arguments but a different program state.
In many cases, using FP results in less unintended bugs, and cleaner overall code (although there is a learning curve to read and write it). Scala is a language that combines strong support for FP, as well as OOP. Let's focus on the former: 

**First Class Functions**
The concept of _first class functions_ is fundamental to functional programming. The good news is, you're probably familiar with it as a python developer. It means that you can treat a function like any other object, passing it in as an argument into (or returning it from) _another_ function and storing it as a variable, in a dictionary, etc.  So, for example, I can create a higher-order function which takes an arbitrary function as an input, along with some numerical inputs, and applies them together. 
```python
def function_combiner(f1, f2, input1, input2):
    return f1(input1) + f2(input2)
```
then I can just define my two input functions and pass them into `function_combiner`
```python
def doubler(x):
    return x*2

def squarer(x):
    return x**2

print(function_combiner(doubler, squarer, 8, 2))
# prints doubler(8) + squarer(2) = 16 + 4 = 20
```
The same concept works in Scala:
```scala
def doubler(x: Double): Double = x *2
def squarer(x: Double): Double = x*x

def functionCombiner(f1: Double => Double, f2: Double => Double, input1: Double, input2: Double): Double = f1(input1) + f2(input2)

println(functionCombiner(doubler, squarer, 8, 12))
// same as the python
```


<hr>

_Sources_

1. [Scala documentation](https://docs.scala-lang.org/learn.html)
2. [Scala vs. Python - Vademecum of Practical Data Science](https://datasciencevademecum.wordpress.com/2016/01/28/6-points-to-compare-python-and-scala-for-data-science-using-apache-spark/)
3. [Scala vs. Python for Spark- Dezyre.com](https://www.dezyre.com/article/scala-vs-python-for-apache-spark/213)