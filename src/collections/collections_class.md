# Java Collections类

>- [addAll()方法]()
>- [binarySearch()方法]()
>- [copy()方法]()
>- [reverse()方法]()
>- [shuffle()方法]()
>- [sort()方法]()
>- [copy()方法]()
>- [min()方法]()
>- [max()方法]()
>- [replaceAll()方法]()
>- [unmodifiableSet()方法]()

Java `Collections（java.util.Collections）`类，包含许多很有用的实用程序方法。本节中，我们将学习其中一些最常用的方法。

## addAll()方法

利用该方法，你能够将多个元素添加到一个具体集合对象中，如`List`，`Set`。下面是一个使用例子：
```java
List<String> list = new ArrayList<>();

Collections.addAll(list, "element 1", "element 2", "element 3");
```

## binarySearch()方法

`Collections binarySearch()`方法可以使用二进制搜索算法在`Java List`中搜索元素。在使用`binarySearch()`搜索List之前，必须按升序排序。有关如何按升序对`List`进行排序的更多信息，请参阅关于[Java有序集合](sorting_collections.md)教程。下面是一个使用`Collections binarySearch()`方法搜索`List`的例子:
```java
List<String> list = new ArrayList<>();
list.add("one");
list.add("two");
list.add("three");
list.add("four");
list.add("five");

Collections.sort(list);

int index = Collections.binarySearch(list, "four");

System.out.println(index);
```

## copy()方法

`Collections copy()`方法可以将一个集合中的所有元素拷贝到另外一个集合中。下面是使用例子：
```java
List<String> source = new ArrayList<>();
Collections.addAll(source, "e1", "e2", "e3");

List<String> destination = new ArrayList<>();
Collections.copy(destination, source);
```