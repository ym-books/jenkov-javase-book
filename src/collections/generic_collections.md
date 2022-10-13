# Java泛型集合

>- [泛型集合例子](#jump1)
>- [泛型迭代器](#jump2)
>- [使用for循环的泛型迭代](#jump3)

可以为`Java Collections API`中的大多数(如果不是全部)组件指定泛型类型。在本教程中，我将解释如何为两个集合类型指定泛型类型。看了这些示例后你将学会如何在`Java Collections API`中使用泛型。本文一般不讨论Java泛型。Java泛型在我的教程[Java Generics tutorial](generic_collections.md)。

<a id="jump1"/>

## 泛型集合例子

当您为Java集合设置泛型类型时，在声明的时候就就指定具体类型。下面是一个将`Collection`和`HashSet`的泛型类型设置为`Java String`的示例，这意味着它只能包含String实例:
```java
Collection<String> stringCollection = new HashSet<String>();
```

这个`stringCollection`现在只能包含`String`类型的元素。如果试图添加其他类型的元素，或将集合中的元素强制转换为`String`以外的任何类型，编译器将会报错。

实际上，如果您稍微作弊(或纯粹愚蠢)，也可以插入`String`对象以外的其他对象，但不建议这样做。

你可以为`List`, `Set`等指定泛型类型。

<a id="jump2"/>

## 泛型迭代器

当您为Java集合指定泛型类型时，该泛型类型也适用于`Iterator()`方法返回的`Iterator`。下面是一个示例，说明如何获取一个设置了泛型类型的迭代器:
```java
Iterator<String> iterator = stringCollection.iterator();
```

您可以按下面方法迭代其元素：
```java
while(iterator.hasNext()) {
    String element = iterator.next();
    //do something with element.
}
```

注意，没有必要强制转换从`iterator.next()`方法调用返回的`String`。因为迭代器将泛型类型设置为`String`，所以Java编译器已经知道`next()`将返回`String`。

<a id="jump3"/>

## 使用for循环的泛型迭代

您也可以使用`for-loop`来迭代泛型集合，如下：
```java
Collection<String> stringCollection = new HashSet<String>();

for(String stringElement : stringCollection) {
  //do something with each stringElement    
}
```

注意，可以将每个元素`(stringElement)`的变量类型指定为`String`。因为集合的泛型类型被设置为`String`。
