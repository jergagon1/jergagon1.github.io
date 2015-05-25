---
layout: post
title:  "The group_by Method in Ruby"
date:   2014-12-14 17:00:00
categories: technical
tags: array hash enumerable group_by
---
Welcome back to my blog!

This week I am looking at the Ruby `group_by` method of the Enumerable module.

In case you don't know what an Enumerable module is:

In Ruby, a class definition is where we provide the blueprint for an object. We then create an object from that class by instantiating a new instance of the class.

In our class definition, we teach our object how to do stuff by defining methods that we can then ask our object to do.

Sometimes dissimilar classes of objects have similar methods: you could have a `set_sale_price` method for a car object and a frying pan object. These objects would not come from the same inherited class, but could benefit from use of the same method. That's where modules come in.

A module provides a set of common methods or functions that can be added or <q>Mixed in</q> to a class definition. The objects instantiated from that class can then use those methods.

The Enumerable module provides a set of methods to deal with collections of data like arrays and hashes. Using Enumerable methods, you can iterate through a collection of data and do things with some or all of the elements of that data.

The `group_by` method is one of the perhaps lesser-known Enumerable methods. However, it does interesting things and can be very useful in the right context.

The `group_by` method allows you to iterate through a set of data and group the contents of the data according to a block of code that you pass in.

The returned object is a hash where each hash key represents a category of the sorted data. The hash value is a nested array containing all of the elements from the original array or hash that meet the criteria.

Let's look at an array example: I will take an array of numbers and organize them into groups of those that are evenly divisible by 2 and those that are not.

{% highlight ruby %}
# my initial array
my_number_array = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]

# call group_by method to find numbers evenly divisible by 2
my_number_array.group_by { |x| x % 2 == 0 }

# returned hash sorting data into groups
=> {
  false => [1, 3, 5, 7, 9],
  true => [2, 4, 6, 8, 10]
}
{% endhighlight %}

In this case, the keys are boolean categories of evenly divisible by 2 (true) and not evenly divisible by two (false).

It's actually really handy! If you capture the returned hash in a variable, you have access to the sorted data set for future processing.

What happens when you call group_by on a hash?

When you call group_by on a hash, you are also returned a new hash. The hash contains keys that represent the categories. Like arrays, the value for each key is a nested array. Due to the structure of hashes, the nested arrays that serve as the hash values contain other nested arrays for each key-value pair from the original hash that satisfy the criteria.

Here's a hash example. Let's figure out which values are strings and which are not:

{% highlight ruby %}
my_hash = {
  :first_name => "Jeremy",
  :last_name => "Gagon",
  :age => 21
}

my_hash.group_by {|k,v| v.is_a? String}

=> {
  true => [
    [:first_name, "Jeremy"],
    [:last_name, "Gagon"]
  ],
  false => [[:age, 21]]
}
{% endhighlight %}

Like with all Enumerable methods, as you use it more, you understand the context in which it is most effective. I will definitely keep this method in mind as I'm tackling new problems with Ruby data collections.