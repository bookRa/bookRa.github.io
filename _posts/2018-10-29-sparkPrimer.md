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
1. Performance - As the scope of your project increases, the engineering benefits of Scala will begin to make a difference. If your datasets can fit in memory, maybe Python will suffice. But as you begin to work with Big Data (and use [Apache Spark](https://spark.apache.org/), for instance), Scala will give you [significant](https://qr.ae/TUhGEh) time improvements. This is partially due to it being compiled in the Java Virtual Machine. It is also due to the [tool-kit](https://en.wikipedia.org/wiki/Akka_(toolkit)) and many libraries that support concurrent and distributed computing in Scala. 
<sub>*Note* in some cases Python (and certain Python libraries) can actually outperform Scala. And of course, benchmarks can never make up for inefficient code.</sub> 
2. Catching Errors Early (aka workflow) - Because it is statically typed, coding in Scala with an IDE like IntelliJ can help you catch runtime exceptions before you ever compile.

That being said, Scala is not a panacea. There are good reasons to continue using and master Python:


**Benefits of Python**
1. Learning Curve - Python makes it fun and easy to dive into programming.
2. Extensive Support - There are so many powerful, high-level libraries for python. See [Keras](https://keras.io) (deep learning), [spaCy](https://spacy.io/) (NLP), or [Scikit-learn](scikit-learn.org/
) (general ML)

But... Ok. At the end of the day, it's better to get really good at one language than ok at two. Still, having some experience in a stitcally-typed language is really worthwhile as a data scientist or engineer. With that in mind, I set out to learn a bit of Scala, and share with you what I learned.
<hr>
## Lesson 1: Online or Off?
If you'd like to jump right in and get coding, you can use an in-browser Scala environment like [ScalaFiddle](https://scalafiddle.io/) or [Scastie](https://scastie.scala-lang.org/).

If you'd like to run Scala code offline (and maybe begin putting together a project), then follow [these instructions](https://docs.scala-lang.org/getting-started.html#if-prefer-working-in-an-ide) to install the prerequisite software/packages. 

If you're like me (_read_ impatient), you just want to dive in and learn! If so you can use the useful site [Scala Exercises]()

<hr>
_Sources_

1. [Scala documentation](https://docs.scala-lang.org/learn.html)
2. [Scala vs. Python - Vademecum of Practical Data Science](https://datasciencevademecum.wordpress.com/2016/01/28/6-points-to-compare-python-and-scala-for-data-science-using-apache-spark/)
3. [Scala vs. Python for Spark- Dezyre.com](https://www.dezyre.com/article/scala-vs-python-for-apache-spark/213)