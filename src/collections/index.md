# Java集合

>- [Java集合核心类和接口](#jump1)
>    - [Java Collection](#jump1_1)
>    - [Java List](#jump1_2)
>    - [Java Set](#jump1_3)
>    - [Java SortedSet](#jump1_4)
>    - [Java NavigableSet](#jump1_5)
>    - [Java Map](#jump1_6)
>    - [Java SortedMap](#jump1_7)
>    - [Java NavigableMap](#jump1_8)
>    - [Java Stack](#jump1_9)
>    - [Java Queue](#jump1_10)
>    - [Java Deque](#jump1_11)
>    - [Java Iterator](#jump1_12)
>    - [Java Iterable](#jump1_13)
>- [Java Collections类](#jump2)
>- [Java Properties](#jump3)
>- [Java Collection Packages](#jump4)
>- [Java Collections概览](#jump5)
>- [Java Collections 和 Generics](#jump6)
>- [Java Collections and the equals() and hashCode() Methods](#jump7)

Java集合API为Java开发者提供了一组类和接口，使其更容易的来处理对象和集合，例如列表（list）、映射（map）、堆栈（stacks）等。

你不需要编写自己的集合类，Java提供了很多现成的集合类。本教程将带你深入学习这些集合类，特别是Java8+中的一些集合类。

本节教程的目的是向概览Java集合类，不会描述集合类里面的每个类的细节。但是，只要你对集合类有了全局的熟悉，后面你在JavaDoc中查看相关内容将会变得容易的多。

<link id="jump1"/>

## Java集合核心类和接口

下面是Java集合库中的核心的类和接口：

>- [Java Collection](#jump1_1)
>- [Java List](#jump1_2)    
>- [Java Set](#jump1_3)     
>- [Java SortedSet](#jump1_4)
>- [Java NavigableSe](#jump1_5)
>- [Java Map](#jump1_6)     
>- [Java SortedMap](#jump1_7)
>- [Java NavigableMa](#jump1_8)
>- [Java Stack](#jump1_9)   
>- [Java Queue](#jump1_10)   
>- [Java Deque](#jump1_11)   
>- [Java Iterator](#jump1_12)
>- [Java Iterable](#jump1_13)

这些核心的接口，在后面的教程中都会有介绍，这里先给大家一个快速的介绍说明。

Java集合API中还包含上述接口的一些有用的实现类以及一些非常实用的程序类，其中的一些是：

- Collections
- Properties
- Comparable
- Comparator

<a id="jump1_1"/>

### Java Collection

Java Collection接口是集合的一个顶层的抽象接口，下面如一些子接口List、Set、Stack、Queue和Deque。其抽象了集合的一些通用的操作，例如，在Java Collection接口中可以使用基于索引访问元素的方法。在后面章节中，将会更加详细介绍Java Collection接口。

<a id="jump1_2"/>

### Java List

Java List接口表示有序集合，集合元素是有序的。通过有序的方式，您可以按照元素在列表中出现的顺序访问它们。该接口在后面章节将详细介绍。

<a id="jump1_3"/>

### Java Set

Java Set接口是个无序集合，集合元素无序排列。和List不同，Set不保证顺序访问其元素。有一些Set的实现可以根据元素的自然顺序对其排序，但是Set接口本身不提供这样的保证，你必须要自己去实现它。在后面章节将会详细介绍Set集合接口。

<a id="jump1_4"/>

### Java SortedSet

Java SortedSet接口是Set的一个子接口，表示元素的有序集合。因此，SortedSet中的元素可以按排序顺序迭代。SortedSet接口在Java SortedSet教程中有更详细的解释。

<a id="jump1_5"/>

### Java NavigableSet

Java NavigableSet接口是SortSet的一个子接口，其额外提供了一些方法，以更加方便的导航式的访问Set集合中的元素。后见章节将做详细介绍。

<a id="jump1_6"/>

### Java Map

Java Map接口表示键集和值集之间的映射。键和值都是对象。将键+值对插入到Map中，稍后可以通过键检索值—这意味着稍后只需要键就可以再次从Map中读取值。Map接口在Java Map教程中有更详细的说明。

<a id="jump1_7"/>

### Java SortedMap

Java SortedMap接口是Map接口的扩展，表示对Map中的键进行排序的Map。因此，您可以按已排序的顺序迭代存储在SortedMap中的键，而不是按普通Map中的那种随机顺序迭代它们。在Java SortedMap教程中更详细地解释了SortedMap接口。

<a id="jump1_8"/>

### Java NavigableMap

Java NavigableMap接口是SortedMap接口的扩展，该接口包含用于轻松导航NavigableMap中的键和项的附加方法。在Java NavigableMap教程中更详细地解释了NavigableMap接口。

<a id="jump1_9"/>

### Java Stack

Java Stack类代表了一种经典的堆栈数据结构，其中的元素可以被推到堆栈的顶部，然后再从堆栈的顶部弹出，先进后出。栈接口在Java栈教程中有更详细的解释。

<a id="jump1_10"/>

### Java Queue

Java Queue接口代表了一种经典的队列数据结构，其中将元素对象插入队列的一端，并在队列的另一端从队列中取出，先进先出。这与使用堆栈的方式相反。队列接口在Java队列教程中有更详细的解释。

<a id="jump1_11"/>

### Java Deque

Java Deque接口表示双端队列，这意味着可以从队列的两端插入和删除元素的数据结构。我猜你也可以叫它双端堆栈。deque接口在Java deque教程中有更详细的解释。

<a id="jump1_12"/>

### Java Iterator

Java Iterator接口表示能够迭代某种Java集合的组件。例如，List或Set。你可以从Java Set, List, Map等中获取迭代器实例。

<a id="jump1_13"/>

### Java Iterable

Java Iterable接口在职责上与Java Iterator接口非常相似。Iterable接口允许使用Java中的for-each循环迭代Java Collection。Java Iterable接口在Java Iterable接口教程中有更详细的解释。Java Iterable接口实际上不是Java Collection API的一部分，但它经常与Java Collection API一起使用，因此我将本教程作为Java Collection教程的一部分。for-each循环在我的Java for循环教程中有解释。

<a id="jump2"/>

## Java Collections类

[Java Collections class]()类包含一系列实用程序方法，可以帮助您更有效地使用Java Collections API。

<a id="jump3"/>

## Java Properties

[Java Properties]()类是一个特殊的键值存储，类似于[Java Map]()，但专门用于保存字符串-字符串键值对，并能够从属性文件加载和存储属性。

<a id="jump4"/>

## Java Collection Packages

大多数Java集合位于`Java.util`包。Java在`Java.util.concurrent`包中也有一组并发集合。本教程将不描述并发集合。这些在我的[Java util concurrent tutorial]()教程中有描述。

<a id="jump5"/>

## Java Collections概览

为了帮助您了解[Java集合类和接口的概述]()，本Java集合教程中的第一个文本是Java集合概述文本。

<a id="jump6"/>

## Java Collections 和 Generics

本Java集合教程的第五部分介绍了如何在Java集合中使用泛型。泛型在使用Java的Collection类时非常有用。您可以在[Java Generic Collections]()中找到相关教程内容。

Java泛型在我的[ Java Generics]()教程中有更详细的解释。

<a id="jump7"/>

## Java Collections and the equals() and hashCode() Methods

Java Collection API中的许多核心组件都依赖于`hashCode()`和`equals()`方法的正确实现。[Java hashCode and equals methods]()教程解释了这些方法是如何工作的，以及为什么它们是核心Java集合组件的中心。
