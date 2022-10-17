# Java Collections类

>- [addAll()方法]()
>- [binarySearch()方法]()
>- [copy()方法]()
>- [reverse()方法]()
>- [shuffle()方法]()
>- [sort()方法]()
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

//不声明destination长度会报数组越界错误，看源码就知道，要求destination的size大于等source的size
/*List<String> destination = new ArrayList<>();
Collections.copy(destination, source);*/

//正确方式
List<String> destination = new ArrayList<>(Arrays.asList(new String[source.size()]));
Collections.copy(destination, source);
destination.forEach(s -> System.out.println(s));
```

## reverse()方法

`Collections reverse()`方法可以反转`Java List`中的元素。下面是一个倒转`List`元素的例子:
```java
List<String> list = new ArrayList<String>();

list.add("one");
list.add("two");
list.add("three");

Collections.reverse(list);
```

执行上面代码后，`list`中元素是：`three,two,one`。

## shuffle()方法

`Collections shuffle()`方法可以对`List`的元素进行洗牌，随机打乱再重排。      
如果提供的列表没有实现`RandomAccess`接口，`shuffle`方法会将元素复制到数组中，然后打乱数组元素的顺序，最后再将打乱顺序后的元素复制回列表。
下面是一个使用`Collections shuffle()`方法洗牌列表的例子:    
```java
List<String> list = new ArrayList<String>();

list.add("one");
list.add("two");
list.add("three");
list.add("four");
list.add("five");

Collections.shuffle(list);
```

## sort()方法

`Collections sort()`方法可以对`Java List`进行排序。我已经在我的Java列表排序教程中介绍了列表的排序。下面是一个使用`Collections sort()`方法对`Java List`进行排序的例子:
```java
List<String> list = new ArrayList<String>();

list.add("one");
list.add("two");
list.add("three");
list.add("four");

Collections.sort(list);
```

## min()方法

`Collections min(`)方法可以根据元素的自然顺序找到`List`中最小的元素(请参阅我的[Java List排序](sorting_collections.md)教程)。下面是一个使用`Collections min()`方法在`Java List`中查找最小元素的示例:
```java
List source = new ArrayList();
source.add("1");
source.add("2");
source.add("3");

String min = (String) Collections.min(source);
```
执行上面代码，最小元素`min`将为1。

## max()方法

`Collections max()`方法可以根据元素的自然顺序找到`List`中的最大元素(请参阅我的[Java List排序](sorting_collections.md)教程)。下面是一个在`Java Lis`t中查找最大元素的例子:
```java
List source = new ArrayList();
source.add("1");
source.add("2");
source.add("3");

String max = (String) Collections.max(source);
```
执行上面代码，返回最大值为`3`。

## replaceAll()方法

`Java Collections replaceAll()`方法可以将集合中一个相同元素替换为另一个元素。将要替换的元素和要替换它的元素作为参数传递给replaceAll()方法。如果有元素被替换，`Collections replaceAll()`方法返回`true`，否则返回`false`。下面是一个用`Java List`中所有出现的元素替换另一个元素的例子:
```java
List source = new ArrayList();
source.add("A");
source.add("B");
source.add("A");

boolean replacedAny = source.replaceAll(source, "A", "C");
```

`Collections replaceAll()`方法使用每个元素的`equals()`方法来确定该元素是否等于要替换的元素。在关于`Java equals()`方法的部分中，我写了更多关于`equals()`方法如何工作的细节。

## unmodifiableSet()方法

`Java Collections`类中的`unmodifiableSet()`方法可以从普通`Java Se`t创建一个不可变(不可修改)的`Set`。下面是一个从普通`Set`创建不可变`Set`的Java示例:
```java
Set normalSet    = new HashSet();

Set immutableSet = Collections.unmodifiableSet(normalSet);
```

