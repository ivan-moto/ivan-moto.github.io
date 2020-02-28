---
layout: post
title: "Kotlin interfaces: enforce a constructor"
---
Is it possible to enforce a "constructor" through Kotlin interfaces? Yes it is.

I love how Kotlin's simple and logical abstractions can be combined to produce some very powerful patterns.

# A problem

I recently started using the Java Database Connectivity (JDBC) API at work. While reading the JavaDoc for the DataSource
interface, I ran across

{% highlight java %}
...
 * An implementation of {@code DataSource} must include a public no-arg
 * constructor.
...
 */

public interface DataSource  extends CommonDataSource, Wrapper {
...
{% endhighlight %}

Interfaces exist in order to codify contracts. Wouldn't it be better to enforce this requirement -- must include a public
no-arg constructor -- in the interface itself? Instead, we're relying on the due dilligence and good intentions of
the implementers of DataSource.

Java can't solve this for us. Can Kotlin?

# A solution

Here's the solution:

```kotlin
fun main() {
    val dataSource = NoOpDataSource()
}

interface DataSource {

    operator fun invoke(): DataSource // Now implementer must have a no arg "constructor"
}

class NoOpDataSource : DataSource {

    override fun invoke(): DataSource = NoOpDataSource()
}
```

Strictly speaking, this is not a constructor, it's a function.

In Kotlin, we have [operator overloading](https://kotlinlang.org/docs/reference/operator-overloading.html). We can implement
certain operators (such as + or == or >) on our types through regular functions (such as `operator fun plus(other: T): T` for +).

It just so happens that `()` is an operator than we can overload, using the `operator` keyword and `invoke` function
name.

Given that `invoke` is a regular function, we can go even further and require certain parameters. Or even `suspend` it.

<hr>

If you're interested in learning more Kotlin tips and tricks, I created a collection of Kotlin snippets that you can read
and understand in 30 seconds: https://github.com/IvanMwiruki/30-seconds-of-kotlin
