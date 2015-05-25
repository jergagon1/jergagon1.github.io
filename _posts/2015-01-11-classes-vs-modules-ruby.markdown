---
layout: post
title:  "Classes vs Modules in Ruby"
date:   2015-01-11 17:00:00
categories: technical
tags: ruby class module
---
Classes and Modules are both ways to organize code in Ruby. They share some common structural elements but are fundamentally different in nature and work together to build powerful objects.

A class is a construct to provide a blueprint for an object. Once you have defined a class with it’s attributes and methods you can create an instance of the class. The class instance - or object - will have all of the capabilities of the class.

{% highlight ruby %}
class Person

  def initialize(name, age, sex)
    @name = name
    @age = age
    @sex = sex
  end

  def stand
    # stand up
  end

  def walk
    # move one foot in front of other
  end

  def talk(sentence)
    puts sentence
  end

end

john_smith = Person.new("John Smith", 25, "male")
john_smith.stand # John stands up
john_smith.talk("Hi, I'm a person")
=> "Hi, I'm a person"
{% endhighlight %}

A class can inherit behavior from a single parent class.

{% highlight ruby %}
class Male < Person
end

bill_smith = Male.new
bill_smith.walk # I inherited this from my parent class
{% endhighlight %}

Modules, by comparison, have two primary functions:

1.  Modules allow you to define functionality outside of a class and mix it in to one or more classes. You can add multiple modules to simulate multiple inheritance which Ruby does not allow.
2.  Modules allow you to create a namespace to avoid clashes of similarly named classes, methods and constants.

Let's assume we want to include some functionality in our person class that is common to all mammals. We don't want to chain a series of classes all the way from a person to a mammal in the animal kingdom, but it would be helpful to have some mammal functionality.

We could define a mammal module and mix it in to our class using the <q>include</q> keyword.

{% highlight ruby %}
module Mammal

  def grow_hair
    # hair grow
  end

  def breathe_air
    # breathe
  end

end

class Person

  include Mammal

  # rest of code here...

end

jane_smith = Person.new
jane_smith.breathe_air
{% endhighlight %}

The namespace functionality allows you to wrap a class or method in a module so that it can be referred to using the module modifier to avoid any naming clashes.

{% highlight ruby %}
module Athlete
  class Person
    def run
      # running fast here
    end
  end
end

module CouchPotato
  class Person
    def run
      # not running so fast here
    end
  end
end

athlete = Athlete::Person.new
athlete.run # Wow, that was fast!

jeremy = CouchPotato::Person.new
jeremy.run # Not so much...
{% endhighlight %}