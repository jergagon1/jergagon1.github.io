---
layout: post
title:  "Ruby Hashes vs JavaScript Objects"
date:   2015-01-18 17:00:00
categories: technical
tags: ruby hash javascript object
---
When you frequently work several different coding languages, you begin to notice interesting comparisons between the languages.

One interesting comparison can be drawn between a Ruby hash and a JavaScript object. Let's take a look at the examples of each:

{% highlight ruby %}
# Ruby hash literal
my_hash = {
  :name => "Jeremy Gagon",
  :occupation => "Web Developer"
}

# Ruby hash literal with alternate syntax
my_hash = {
  name: "Jeremy Gagon",
  occupation: "Web Developer"
}
{% endhighlight %}

{% highlight javascript %}
// JavaScript object
var myObject = {
  name: "Jeremy Gagon",
  occupation: "Web Developer"
};
{% endhighlight %}

As you can see, using the alternate Ruby hash literal syntax is essentially the same as using the literal object constructor in JavaScript. They both commonly use symbols for the name or key and can contain any type of object as the value.

They look the same syntactically, so what's the difference?

A Ruby hash is itself an object, in fact, it's an instance of the Hash class. It inherits attributes and methods from the Object parent class and has additional built-in functionality from the Enumerable module.

A hash exists to deal with collections of data. It is an object that's a container for other objects. It allows you to assign a name to each separate value in your collection.

In contrast, a JavaScript object is a complex data structure that allows you to store a collection of properties and methods. These properties and methods define the state and abilities of the object.

Using the literal object constructor, you are creating a one-off object.

{% highlight javascript %}
var myNewObject = {
  property1: value1,
  property2: value2
}
{% endhighlight %}

Here I have created a new object myNewObject that has properties and values. If I wanted to create another similar object, I would need to repeat the code with a different variable name.

In a way, this could be considered similarity between a JavaScript object created in this way and a Ruby hash literal instance. Neither the literal object constructor in JavaScript or an instance of the Hash class in Ruby is designed to  make multiple instances of itself. It is designed to be a unique object instance containing other objects.

There is an alternate form of object construction in JavaScript where you can create multiple similar objects through a constructor function, but the syntax is different to Ruby hashes and not specifically related to the issue here.

There are some similarities between a Ruby hash and a JavaScript literal object that extend beyond appearance alone. However, the use and implementation can be different in the two languages.