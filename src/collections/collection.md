# Java Collection类

>- [创建一个`Collection`实例](#jump1)
>- [`Collection`的子类型](#jump2)
>- [添加元素到`Collection`](#jump3)
>- [从`Collection`中删除元素](#jump4)
>- [将一个`Collection`对象元素添加到另一个`Collection`](#jump5)
>- [从`Collection`中移除一个`Collection`对象元素](#jump6)
>- [保留`Collection`中某些元素](#jump7)
>- [检查`Collection`中是否包含某个元素](#jump8)
>- [`Collection`的大小](#jump9)
>- [迭代`Collection`的元素](#jump10)

`Java Collection`接口`(Java .util.Collection)`是[`Java Collection API`](index.md)的根接口之一。虽然不直接实例化`Collection`，而是实例化`Collection`的子类型，但通常可以将这些子类型统一地视为`Collection`。在这篇文章中，你将看到如何。

<a id="jump1"/>
      
## 创建一个`Collection`实例

正如上面所提到的，您不可直接创建`Collection`实例，而是`创建Collectio`n的一个子类型的实例。下面是一个创建`List`的例子，它是`Collection`的子类型:

```java
Collection collection = new ArrayList();
```

上面的示例适用于Collection的每个子类型。

<a id="jump2"/>      
                     
## `Collection`的子类型

下面是一些扩展继承`Collection`的一些接口：

>- [List](list.md)
>- [Set](set.md)
>- [SortedSet](sorted_set.md)
>- [NavigableSet](navigable_set.md)
>- [Queue](queue.md)
>- [Deque](deque.md)

Java没有提供`Collection`接口的可用实现，因此必须使用如上面列出的子类型之一。`Collection`接口只是定义了这些C`ollection`子类型共享的一组方法(行为)。这使得可以忽略正在使用的集合的特定类型，而只是将其视为集合。这是标准继承，因此没有什么神奇的地方，但它有时仍然是一个不错的特性。本文后面的章节将描述这些常用操作中最常用的。

下面是一个用来操作`Collection`集合的例子：
```java
public class MyCollectionUtil{

  public static void doSomething(Collection collection) {
    
    Iterator iterator = collection.iterator();
    while(iterator.hasNext()){
      Object object = iterator.next();

      //do something to object here...
    }
  }
}
```

下面是几种使用不同`Collection`子类型调用此方法的方法:
```java
Set  set  = new HashSet();
List list = new ArrayList();

MyCollectionUtil.doSomething(set);
MyCollectionUtil.doSomething(list);    
```

<a id="jump3"/>      

## 添加元素到`Collection`

无论您使用的是什么`Collection`的具体类型，都有一些向`Collection`添加元素的标准方法。向`Collection`中添加元素是通过`add()`方法完成的。下面是一个向`Java Collection`中添加元素的例子:
```java
String     anElement  = "an element";
Collection collection = new HashSet();

boolean didCollectionChange = collection.add(anElement);
```

`add()`方法把给定的元素添加到集合中，如果由于调用`add()`方法而导致集合发生更改(添加成功)，则返回`true`。一个`Set`实例可能没有改变。如果`Set`已经包含该元素，则不会再次添加它。另一方面，如果在`List`上调用`add()`，而`List`已经包含了该元素，则该元素将在`List`中存在两次。

<a id="jump4"/>      

## 从`Collection`中删除元素

`remove()`方法从集合中删除给定的元素，如果被删除的元素存在于集合中并被删除，则返回`true`。如果元素不存在，`remove()`方法返回`false`。下面是一个从`Java Collection`中移除元素的例子:
```java
boolean wasElementRemoved = collection.remove("an element");
```

<a id="jump5"/>      

## 将一个`Collection`对象元素添加到另一个`Collection`

还可以使用`addAll()`方法将对象集合添加到Java集合中。下面是一个向`Java collection`中添加对象集合的示例:
```java
Set  aSet  = ... // get Set  with elements from somewhere

Collection collection = new HashSet();

collection.addAll(aSet);    //returns boolean too, but ignored here
```

`addAll()`方法把集合对象作为参数，会找到集合对象中所有的元素添加到另外一个集合中，而不是对象本身。如果使用`Collection`作为参数调用`add()`，则会添加`Collection`对象本身，而不是它的元素。

`addAll()`方法的具体行为取决于`Collection`具体实现类。有些`Collection`的具体实现类允许多次添加同一元素，而有些则不允许。

<a id="jump6"/>      

## 从`Collection`中移除一个`Collection`对象所有元素

`removeAll()`方法将集合对象作为参数，会在另外集合中删除相关对应元素。如果`Collection`参数包含目标集合中没有找到的任何元素，则忽略这些元素。下面是一个从`Java collection`中移除元素集合的例子:
```java
Collection objects = //... get a collection of objects from somewhere.

collection.removeAll(objects);
```

<a id="jump7"/>      

## 保留`Collection`中某些元素

`Java Collection`的`retainAll()`的作用与`removeAll()`刚好相反。它不是删除在参数`Collection`中找到的所有元素，而是保留所有这些元素，并删除所有其他元素。请记住，只有当元素已经包含在目标集合中时，它们才会被保留。在参数`Collection` 中找到的任何不在目标集合中的新元素都不会自动添加。他们只是被忽视了。下面是一个将一个集合中的所有元素保留到另一个Java集合中的示例:   
```java
Collection colA = new ArrayList();
Collection colB = new ArrayList();

colA.add("A");
colA.add("B");
colA.add("C");

colB.add("1");
colB.add("2");
colB.add("3");

Collection target = new HashSet();

target.addAll(colA);     //target now contains [A,B,C]
target.addAll(colB);     //target now contains [A,B,C,1,2,3]

target.retainAll(colB);  //target now contains [1,2,3]
```

<a id="jump8"/>      

## 检查`Collection`中是否包含某个元素

`Collection`接口有两个方法来检查`Collection`是否包含一个或多个特定元素。它们是`contains()`和`containsAll()`方法。如下图所示:
```java
Collection collection   = new HashSet();
boolean containsElement = collection.contains("an element");

Collection elements     = new HashSet();
boolean containsAll     = collection.containsAll(elements);
```

调用`contains()`方法，如果集合包含元素，返回`true`，否则返回`false`。

调用`containsAll()`方法，如果集合中包含参数集合的所有元素，返回`true`，否则返回`false`。

<a id="jump9"/>      

## `Collection`的大小

可以使用`size()`方法检查集合的大小。“大小”指的是集合中元素的数量。下面是一个例子:
```java
int numberOfElements = collection.size();   
```

<a id="jump10"/>      

## 迭代`Collection`的元素

您可以迭代集合的所有元素。通过获取获取集合的`Java Iterator`，并遍历该集合来实现。如下：
```java
Collection collection = new HashSet();
//... add elements to the collection

Iterator iterator = collection.iterator();
while(iterator.hasNext()){
    Object object = iterator.next();
    System.out.println(object);
}
```

也可以用`Java for-each loop`来迭代集合：
```java
Collection collection = new HashSet();
collection.add("A");
collection.add("B");
collection.add("C");

for(Object object : collection) {
    System.out.println(object);
}
```
