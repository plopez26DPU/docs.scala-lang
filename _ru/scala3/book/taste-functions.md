---
layout: multipage-overview
title: Функции первого класса
scala3: true
partof: scala3-book
overview-name: "Scala 3 — Book"
type: section
description: На этой странице представлено введение в функции в Scala 3.
language: ru
num: 11
previous-page: taste-methods
next-page: taste-objects
---

Scala обладает большинством возможностей, которые вы ожидаете от функционального языка программирования, в том числе:

- Lambdas (анонимные функции)
- Функции высшего порядка (HOF)
- Неизменяемые коллекции в стандартной библиотеке

Лямбда-выражения, также известные как _анонимные функции_, играют важную роль в том, чтобы ваш код был кратким, но удобочитаемым.

Метод `map` класса `List` является типичным примером функции высшего порядка — 
функции, которая принимает функцию в качестве параметра.

Эти два примера эквивалентны и показывают, как умножить каждое число в списке на `2`, передав лямбда в метод `map`:


{% tabs function_1 %}
{% tab 'Scala 2 and 3' for=function_1 %}
```scala
val a = List(1, 2, 3).map(i => i * 2)   // List(2,4,6)
val b = List(1, 2, 3).map(_ * 2)        // List(2,4,6)
```
{% endtab %}
{% endtabs %}

Примеры выше также эквивалентны следующему коду, в котором вместо лямбда используется метод `double`:


{% tabs function_2 %}
{% tab 'Scala 2 and 3' for=function_2 %}
```scala
def double(i: Int): Int = i * 2

val a = List(1, 2, 3).map(i => double(i))   // List(2,4,6)
val b = List(1, 2, 3).map(double)           // List(2,4,6)
```
{% endtab %}
{% endtabs %}

> Если вы еще раньше не видели метод `map`, он применяет заданную функцию к каждому элементу в списке, 
> создавая новый список, содержащий результирующие значения.

Передача лямбда-выражений функциям высшего порядка в классах коллекций (таких, как `List`) — 
это часть работы со Scala, которую вы будете делать каждый день.


## Неизменяемые коллекции

Когда вы работаете с неизменяемыми коллекциями, такими как `List`, `Vector`, 
а также с неизменяемыми классами `Map` и `Set`, важно знать, 
что эти функции не изменяют коллекцию, для которой они вызываются; 
вместо этого они возвращают новую коллекцию с обновленными данными. 
В результате также принято объединять их вместе в “свободном” стиле для решения проблем.

Например, в этом примере показано, как отфильтровать коллекцию дважды, 
а затем умножить каждый элемент в оставшейся коллекции:


{% tabs function_3 %}
{% tab 'Scala 2 and 3' for=function_3 %}
```scala
// пример списка
val nums = (1 to 10).toList   // List(1,2,3,4,5,6,7,8,9,10)

// методы могут быть сцеплены вместе
val x = nums.filter(_ > 3)
            .filter(_ < 7)
            .map(_ * 10)

// result: x == List(40, 50, 60)
```
{% endtab %}
{% endtabs %}

В дополнение к функциям высшего порядка, используемым в стандартной библиотеке, 
вы также можете [создавать свои собственные функции][higher-order].

[higher-order]: {% link _overviews/scala3-book/fun-hofs.md %}
