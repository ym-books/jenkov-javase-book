# Java Iterator迭代器

>- [Java Iterator的核心方法](#jump1)
>- [获取Iterator实例]()
>- [开始迭代]()
>- [迭代顺序]()
>- [Java List迭代器]()
>- [Java Set迭代器]()
>- [迭代期间添加元素]()
>- [迭代期间删除元素]()
>- [forEachRemaining()方法]()
>- [ListIterator迭代器]()
>- [自己实现Iterator]()

Java Iterator接口表示能够迭代集合中的元素，每次迭代一个访问。Iterator接口是Java中用于迭代元素集合的最古老的机制之一(尽管不是最古老的——Enumerator早于Iterator)。

使用Java Iterator迭代器，你首先要从元素集合中获取一个Iterator实例，Iterator会跟踪集合中的每个元素，以确保能够遍历所有的元素。如果在迭代器迭代元素期间修改集合中元素，迭代器通常会检测到它，并在下次尝试从迭代器获取下一个元素时抛出异常。稍后再详细介绍。

<a id="jump1"/>

## Java Iterator的核心方法

Java Iterator迭代器接口非常的简单，核心的方法如下：

| 方法                 | 描述                                                       |
|:-------------------|:---------------------------------------------------------|
| hasNext()          | 如果迭代器有元素返回true，否则返回false                                 |
| next()             | 从迭代器中返回下一个元素                                             |
| remove()           | 从迭代器正在迭代的集合中移除next()返回的最新元素。                             |
| forEachRemaining() | 遍历迭代器中的所有剩余元素，并调用Java Lambda表达式，将每个剩余元素作为参数传递给Lambda表达式。 |

下面内容中，对表中的每个方法都有涉及。

## 获取Iterator实例

标准的Java集合接口collection包含一个名为iterator()的方法。通过调用iterator()，可以从给定的Collection中获得一个迭代器。

你也可以从许多Java集合数据结构中获得迭代器，例如List, Set, Map, Queue, Deque或Map。

下面是一些从各种Java集合类型获取Java Iterator的例子:

```java
List<String> list = new ArrayList<>();
list.add("one");
list.add("two");
list.add("three");

Iterator<String> iterator = list.iterator();


Set<String> set = new HashSet<>();
set.add("one");
set.add("two");
set.add("three");

Iterator<String> iterator2 = set.iterator();
```

## 开始迭代

使用`while`循环迭代`Iterator`中的元素。下面是一个使用`while`循环迭代`Java Iterator`元素的例子:

```java
Iterator iterator = list.iterator();

while(iterator.hasNext()) {
    Object nextObject = iterator.next();

}
```

在上面的Java示例中有两个方法需要注意。第一个方法是`Iterator hasNext()`方法，如果Iterator包含更多元素，该方法将返回true。换句话说，如果`Iterator`还没有遍历集合中的所有元素，那么`hasNext()`方法将返回`true`。如果`Iterator`已经遍历了基础集合中的所有元素，那么`hasNext()`方法将返回`false`。

第二个要注意的方法是`next()`方法。`next()`方法返回迭代器正在迭代的集合的下一个元素。

## 迭代顺序

`Java Iterator`中包含的元素的遍历顺序取决于提供`Iterator`的集合类型。例如，从`List`中获得的迭代器将按元素存储在`List`内部的相同顺序遍历该`List`的元素。另一方面，从`Set`中获得的迭代器不能保证迭代集合中元素的精确顺序。

## Java List迭代器

下面例子是从`List`实例中获取一个`List Iterator`迭代器：

```java
List list = new ArrayList();

list.add("123");
list.add("456");
list.add("789");

Iterator iterator = list.iterator();
```

## Java Set迭代器

下面例子是从`Set`实例中获取一个`Set Iterator`迭代器：

```java
Set set = new HashSet();

set.add("123");
set.add("456");
set.add("789");

Iterator iterator = set.iterator();
```

## 迭代期间添加元素

有些集合不允许在迭代期间修改集合元素。在这种情况下，下次调用`Iterator next()`方法时，您将获得`ConcurrentModificationException`异常。以下示例在执行时会导致ConcurrentModificationException异常:

```java
List<String> list = new ArrayList<>();

list.add("123");
list.add("456");
list.add("789");

Iterator<String> iterator = list.iterator();

while(iterator.hasNext()) {
    String value = iterator.next();

    if(value.equals("456")){
        list.add("999");
    }
}
```

如果在通过迭代器迭代集合时修改集合，则会抛出`ConcurrentModificationException`，因为迭代器与集合不同步。

## 迭代期间删除元素

`Java Iterator`接口有一个`remove()`方法，它允许您从底层集合中删除`next()`刚刚返回的元素。调用`remove()`不会引发ConcurrentModificationException异常。下面是一个在迭代迭代期间从集合中移除元素的例子:

```java
List<String> list = new ArrayList<>();

list.add("123");
list.add("456");
list.add("789");

Iterator<String> iterator = list.iterator();

while(iterator.hasNext()) {
    String value = iterator.next();

    if(value.equals("456")){
        iterator.remove();
    }
}
```

## forEachRemaining()方法

Java Iterator的`forEachRemaining()`方法可以在迭代器内部的所有剩余元素上进行迭代，并且对于每个元素调用一个`Java Lambda`表达式作为参数传递给`forEachRemaining()`。下面是一个使用`Java Iterator forEachRemaining()`方法的例子:

```java
List<String> list = new ArrayList<>();
list.add("Jane");
list.add("Heidi");
list.add("Hannah");

Iterator<String> iterator = list.iterator();

iterator.forEachRemaining((element) -> {
    System.out.println(element);
});
```

## ListIterator迭代器

Java还包含一个名为`ListIterator`的接口，它扩展了`Iterator`接口。`Java ListIterator`接口，它表示一个双向迭代器，这意味着一个可以向前和向后导航元素的迭代器。我不会在这里详细介绍ListIterator接口，但我将向您展示如何使用它的一个快速示例:

```java
List<String> list = new ArrayList<>();
list.add("Jane");
list.add("Heidi");
list.add("Hannah");

ListIterator<String> listIterator = list.listIterator();

//前往后迭代
while(listIterator.hasNext()) {
    System.out.println(listIterator.next());
}
//后往前迭代
while(listIterator.hasPrevious()) {
    System.out.println(listIterator.previous());
}
```

正如您所看到的，该示例首先遍历所有元素向前迭代`ListIterato`r，然后再次向后遍历所有元素返回到第一个元素。

## 自己实现Iterator

如果您有一个特殊的、定制的集合类型，您可以自己实现`Java Iterator`接口，以创建一个`Iterator`，该I`terator`可以遍历自定义集合的元素。在本节中，我将向您展示`Java Iterator`接口的一个超级简单的自定义实现，它将让您对自己实现`Iterator`接口的样子有一个印象。

下面将扩展实现`Java List`的一个迭代器，但它是不完整的，因为不能在迭代过程中检测`List`的内容变更，但是它可以让你大概了解`Iterator`的实现是怎么样的，如下：

```java
import java.util.Iterator;
import java.util.List;

public class ListIterator <T> implements Iterator<T> {

    private List<T> source = null;
    private int index = 0;

    public ListIterator(List<T> source){
        this.source = source;
    }


    @Override
    public boolean hasNext() {
        return this.index < this.source.size();
    }

    @Override
    public T next() {
        return this.source.get(this.index++);
    }

}
```

下面展示怎么使用上面的迭代器：

```java
import java.util.ArrayList;
import java.util.List;

public class ListIteratorExample {

    public static void main(String[] args) {
        List<String> list = new ArrayList();

        list.add("one");
        list.add("two");
        list.add("three");

        ListIterator<String> iterator = new ListIterator<>(list);
        while(iterator.hasNext()) {
            System.out.println( iterator.next() );
        }
    }
}
```
