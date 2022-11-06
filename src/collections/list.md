# Java List接口

>- [List比较Set](#jump1)
>- [List的实现](#jump2)
>- [创建List实例](#jump3)
>- [`Lists`泛型](#jump4)
>- [`List`中插入元素](#jump5)
>- [插入null到List](#jump6)
>- [List中指定位置插入元素](#jump7)
>- [将一个List中的所有元素插入到另一个List中](#jump8)
>- [从List中获取元素](#jump9)
>- [在List中查找元素](#jump10)
>   - [查找List中元素的最后一次出现](#jump11)
>- [判断List中是否包含某个元素](#jump12)
>- [从List中移除元素](#jump13)
>- [删除List中所有的元素](#jump14)
>- [将一个List中的所有元素保留到另一个List中](#jump15)
>- [List的大小](#jump16)
>- [List截取子List](#jump17)
>- [将List转换为Set](#jump18)
>- [将List转换成Array](#jump19)
>- [转换Array为List](#jump20)
>- [List排序](#jump21)
>    - [排序List元素对象](#jump22)
>    - [用Comparator排序List](#jump23)
>- [迭代List](#jump24)
>    - [使用Iterator迭代List](#jump25)
>    - [使用For-Each迭代List](#jump26)
>    - [使用普通Fori迭代List](#jump27)
>    - [使用`Java Stream API`迭代操作List](#jump28)
>- [查看JavaDoc了解更多List详情](#jump29)

Java列表接口`Java.util.List`，表示对象的有序序列。`Java List`中包含的元素可以按照它们在`Java List`内部出现的顺序进行插入、访问、迭代和删除。正因为元素是有序排列，所以这种数据结构称之为`List`。

每个元素在`list`都有自己的下表，第一个元素的下表为`0`,第二个下标为`1`，类推……。下标索引的意思是“距离列表的开始有多少个元素”。因此，第一个元素距离列表的开头有0个元素(因为它位于列表的开头)。

可以向`List`中添加任何Java对象。如果`List`没有指定特定类型，则使用Java泛型，甚至可以在同一`List`中混合不同类型(类)的对象。然而，在实践中，通常不会在同一个`List`中混合不同类型的对象。

`Java List`接口是一个标准的Java接口，它是`Java Collection`接口的子类型，这意味着`List`继承自`Collection`。

<a id="jump1"/>

## List比较Set

`Java List`和`Java Set`接口非常相似，因为它们都表示元素的集合。然而，有一些显著的区别。这些差异反映在`List`和`Set`接口提供的方法中。

`Java List`和`Java Set`接口之间的第一个区别是，同一个元素可以在`Java List`中出现多次。这与`Java Set`不同，在`Java Set`中每个元素只能出现一次。

`Java List`和`Java Set`接口之间的第二个区别是，`List`中的元素有顺序，元素可以按照该顺序迭代。`Java Set`不会对内部保存的元素的顺序做出任何承诺。

<a id="jump2"/>

## List的实现

作为`Collection`接口的子接口，那么`Collection`中定义的所有方法是适用`List`。

`Java List`是一个接口，您要实例化才能使用它。Java集合库中，已经有一些实现了`List`的类，如下：   

>- java.util.ArrayList
>- java.util.LinkedList
>- java.util.Vector
>- java.util.Stack

在上面的几个实现类中，`ArrayList`是最常用的。

在`java.util.concurrent`包中也有并发的`List`实现。这些`List`实现在我的其他教程中有更详细的解释。

<a id="jump3"/>

## 创建List实例

通过创建实现`List`接口的一个类的实例，可以创建`List`实例。下面是一些如何创建`List`实例的例子:
```java
List listA = new ArrayList();
List listB = new LinkedList();
List listC = new Vector();
List listD = new Stack();
```

记住，大多数情况下您将使用`ArrayList`类，但也可能在某些情况下使用其他实现之一是有意义的。

<a id="jump4"/>

## `Lists`泛型

默认情况下，可以将任何对象放入`List`中，但从Java 5开始，Java泛型可以限制可以插入`List`的对象类型。下面是一个例子:
```java
List<MyObject> list = new ArrayList<MyObject>();
```

这个`List`现在只能插入`MyObject`实例。然后，您可以访问并迭代其元素，而无需强制转换它们。这是它的样子:
```java
List<MyObject> list = new ArrayList<MyObject>();

list.add(new MyObject("First MyObject"));

MyObject myObject = list.get(0);

for(MyObject anObject : list){
   //do someting to anObject...
}
```

如果没有泛型，上面的例子会是这样的:
```java
List list = new ArrayList();   //没有指定泛型类型

list.add(new MyObject("First MyObject"));

MyObject myObject = (MyObject) list.get(0);  //需要强制转换类型

for(Object anObject : list){
    //需要强制转换类型
    MyObject theMyObject = (MyObject) anObject;

   //do someting to anObject...
}
```

如果没指定泛型类型，那么编译器只知道`list`中包含的是`Object`对象，所以要强制转换成元素的具体类型使用。如果你指定了具体类型，则获取列表元素的时候，编译器就知道是什么具体的类型了。

只要可以，您都应该为`list`指定泛型类型，它能够帮助您避免将错误的类型对象元素插入到`List`中，而且在检索元素对象的时候无序再强制转换元素类型。另外，能够提高代码的可读性，一眼就能够看出`List`中包含的具体对象。所以，只有在有很好的理由下，才应该不指定具体类型。

在本`Java List`教程的其余部分中，我将尽可能多地使用泛型`List`示例。

有关Java泛型的更多信息，请参阅[Java Generics](../generics/index.md)教程。

<a id="jump5"/>

## `List`中插入元素

您可以调用`add()`方法对`List`插入元素对象。如下：
```java
List<String> listA = new ArrayList<>();

listA.add("element 1");
listA.add("element 2");
listA.add("element 3");
```
每次调用都会加一个`String`对象元素插入到`List`的尾部。

<a id="jump6"/>

## 插入null到List

实际上可以在`Java List`中插入空值。下面是一个在`Java List`中插入空值的例子:
```java
Object element = null;

List<Object> list = new ArrayList<>();

list.add(element);
```

<a id="jump7"/>

## List中指定位置插入元素

可以在`Java List`特定索引处插入元素。`List`接口有一个版本的`add()`方法，它将索引作为第一个参数，将插入的元素作为第二个参数。下面是一个在`Java List`中插入索引为`0`的元素的例子:
```java
list.add(0, "element 4");
```
插入元素对象到索引`0`的位置，其它元素下推。

<a id="jump8"/>

## 将一个List中的所有元素插入到另一个List中

可以将一个`Java List`中的所有元素添加到另一个`List`中。您可以使用`List addAll()`方法来做到这一点。结果`List`是两个列表的并集。下面是一个将一个`List`中的所有元素添加到另一个List中的例子:
```java
List<String> listSource = new ArrayList<>();

listSource.add("123");
listSource.add("456");

List<String> listDest   = new ArrayList<>();

listDest.addAll(listSource);
```

上面例子，把第一个列表的所有元素插入到第二个列表中。

`addAll()`方法接受`Collection`作为参数，因此可以传递`List`或`Java Set`作为参数。换句话说，您可以使用`addAll()`将`List`或`Set`中的所有元素添加到`List`中。

<a id="jump9"/>

## 从List中获取元素

您可以使用元素的索引从`Java List`中获取元素。你可以使用`get(int index)`方法来做到这一点。下面是一个使用元素索引访问`Java List`元素的例子:
```java
List<String> listA = new ArrayList<>();

listA.add("element 0");
listA.add("element 1");
listA.add("element 2");

//access via index
String element0 = listA.get(0);
String element1 = listA.get(1);
String element3 = listA.get(2);
```

还可以按照`Java List`元素在内部的存储顺序迭代它们。我将在本Java List教程的后面向您展示如何做到这一点。

<a id="jump10"/>

## 在List中查找元素

您可以通过下面方法在`List`中查找元素：
 - `indexOf()`
 - `lastIndexOf()`

`indexOf()`方法查找给定元素在`List`中第一个出现项的索引。下面是一个在`Java List`中查找两个元素索引的例子:
```java
List<String> list = new ArrayList<>();

String element1 = "element 1";
String element2 = "element 2";

list.add(element1);
list.add(element2);

int index1 = list.indexOf(element1);
int index2 = list.indexOf(element2);

System.out.println("index1 = " + index1);
System.out.println("index2 = " + index2);
```
执行输出：
````java
index1 = 0
index2 = 1
````

<a id="jump11"/>

#### 查找List中元素的最后一次出现

`lastIndexOf()`方法查找元素在`List`中最后一次出现的位置。下面是示例：
```java
List<String> list = new ArrayList<>();

String element1 = "element 1";
String element2 = "element 2";

list.add(element1);
list.add(element2);
list.add(element1);

int lastIndex = list.lastIndexOf(element1);
System.out.println("lastIndex = " + lastIndex);
```
代码片段输出：
```java
lastIndex = 2
```

<a id="jump12"/>

## 判断List中是否包含某个元


<a id="jump13"/>

## 从List中移除元素


<a id="jump14"/>

## 删除List中所有的元素

<a id="jump15"/>

## 将一个List中的所有元素保留到另一个List中

<a id="jump16"/>

## List的大小

<a id="jump17"/>

## List截取子List

<a id="jump18"/>

## 将List转换为Set

<a id="jump19"/>

## 将List转换成Array

<a id="jump20"/>

## 转换Array为List

<a id="jump21"/>

## List排序

<a id="jump22"/>

#### 排序List元素对象

<a id="jump23"/>

#### 用Comparator排序List

<a id="jump24"/>

## 迭代List

<a id="jump25"/>

## 使用Iterator迭代List

<a id="jump26"/>

#### 使用For-Each迭代List

<a id="jump27"/>

#### 使用普通Fori迭代List

<a id="jump28"/>

#### 使用普通Fori迭代List

<a id="jump29"/>

#### 使用`Java Stream API`迭代操作List

<a id="jump30"/>

## 查看JavaDoc了解更多List详情





