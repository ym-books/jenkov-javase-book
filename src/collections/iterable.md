# Java Iterable

>- [使用`for-each`循环迭代可迭代对象](#jump1)
>- [通`Iterator`迭代可`Iterable`对象集合](#jump2)
>- [通过`forEach()`方法迭代](#jump3)
>- [`Iterable`接口定义](#jump4)
>- [接口`Iterable`的实现类](#jump5)
>- [自己实现`Iterable`接口](#jump6)
>- [获取一个`Spliterator`分割迭代器](#jump7)
>- [`Iterable`迭代的性能](#jump8)

<a id="jump1"/>

## 使用`for-each`循环迭代可迭代对象

迭代`Java Iterable`元素的第一种方法是通过`Java for-each`循环。下面是一个示例，演示如何通过`Java for-each`循环迭代`Java List`的元素。因为`Java List`接口扩展了`Collection`接口，而`Collection`接口扩展了`Iterable`接口，所以`List`对象可以与`for-each`循环一起使用。

```java
List<String> list = new ArrayList><();

list.add("one");
list.add("two");
list.add("three");

for( String element : list ){
    System.out.println( element.toString() );
}
```

上面例子，首先创建一个`List`对象并添加3个元素，然后通过`for-each`循环迭代`List`中的元素并输出每个元素。

<a id="jump2"/>

## 通`Iterator`迭代可`Iterable`对象集合

第二种方法迭代可迭代集合对象是调用可`Iterable`对象的`Iterator()`方法获取迭代器`Iterator`。然后迭代获取元素。你可以在我的[Java Iterator教程](iterator.md)中阅读更多关于`Java Iterator`的内容。下面是一个迭代`Java Iterable`(本例中的`Java List`)元素的例子:

```java
List<String> list = new ArrayList><();

list.add("one");
list.add("two");
list.add("three");

Iterator<String> iterator = list.iterator();

while(iterator.hasNext()) {
    String element = iterator.next();
    System.out.println( element );
}
```

<a id="jump3"/>

## 通过`forEach()`方法迭代

第三种迭代`Java Iterable`元素的方法是通过它的`forEach()`方法。`forEach()`方法接受一个`Java Lambda`表达式作为参数。这个`lambda`表达式对`Iterable`中的每个元素调用一次。下面是一个通过`forEach()`方法迭代`Iterable`的元素的例子:

```java
List<String> list = new ArrayList><();

list.add("one");
list.add("two");
list.add("three");

list.forEach( (element) -> {
    System.out.println( element );
});
```

<a id="jump4"/>

## `Iterable`接口定义

`Java Iterable`接口有三个方法，其中只有一个需要实现。其他两个有默认实现。下面是`Iterable`接口的定义:

```java
public interface Iterable<T> {

  Iterator<T>    iterator();

  Spliterator<T> spliterator();

  void           forEach(Consumer<? super T> action);

}
```

必须实现的方法名为`iterator()`。该方法必须返回一个`Java Iterator`，可用于迭代实现`Iterable`接口的对象的元素。迭代器的获取是在幕后进行的，所以您不会看到它已经完成。当您在`for-each`循环中使用`Iterable`时，Java编译器负责为此生成代码。

<a id="jump5"/>

## 接口`Iterable`的实现类

`Java Iterable`接口(Java .lang.Iterable)是`Java Collections API`的根接口之一。因此，Java中几个实现了该接口的对象都是可以迭代其元素的。。

还有一些扩展`Iterable`接口的Java接口。实现了扩展`Iterabl`e接口的接口的类也实现了`Iterable`接口。这样的类也可以迭代它们的元素。

`Collection`接口扩展了`Iterable`，因此`Collection`的所有子类型也实现了`Iterable`接口。例如，`Java List`和`Set`接口都扩展了`Collection`接口，因此也扩展了`Iterable`接口。


<a id="jump6"/>

## 自己实现`Iterable`接口

那么怎么样实现`Iterable`接口并使用`for-each`迭代对象元素呢，下面是一个简单的例子:

```java
public class Persons implements Iterable {
    private List<Person> persons = new ArrayList<Person>();    
    
    public Iterator<Person> iterator() {
        return this.persons.iterator();
    }
}
```

Persons的实例可以像这样与`Java for-each`循环一起使用:

```java
Persons persons = ... //obtain Persons instance with Person objects inside.

for(Person person : persons) {
    // do something with person object.
}
```

<a id="jump7"/>

## 获取一个`Spliterator`分割迭代器

你可以通过`Java Iterable`的`Spliterator()`方法从`Java Iterable`中获得一个`Java Spliterator`迭代器。这里不会介绍`Spliterator`的使用，只是演示如何从`Iterable`中获得`Spliterator`:

```java
List<String> list = new ArrayList><();

list.add("one");
list.add("two");
list.add("three");

Spliterator<String> spliterator = list.spliterator();
```

<a id="jump8"/>

## `Iterable`迭代的性能

如果您正在编写一些需要在一个紧凑的循环中多次迭代集合元素的代码，比如每秒迭代`Java List`数千次，那么通过`Java for-each`循环迭代`List`的速度要比通过标准`for-loop`迭代`List`的速度慢，如下所示:()。

```java
for(int i=0; i<list.size(); i++) {
    Object obj = list.get(i);
}
```

`for-each`循环较慢的原因是，每次迭代都会调用`List iterator()`方法，该方法将创建一个新的`iterator`对象。与使用标准`for-loop`迭代`List`相比，每秒创建数千次甚至数百万次新对象的性能损失较小。

对于大多数偶尔迭代集合的标准业务应用程序，这种性能差异是无关紧要的。它只对每秒执行数千次的非常紧密的循环有影响。
