---
layout: post
title:  "Ruby Classes"
date:   2015-01-02 17:00:00
categories: technical
tags: ruby class object
---
When you start learning an object-oriented programming language like Ruby, you work with objects. These objects can be representations of things in the real world, for example you could have a person object or a car object. However, a programming object does not have to represent a material physical thing. A programming object can also represent an abstract concept like an idea, a number, a conversation or a piece of data.

Objects have attributes that describe their state. A car object might have a color attribute that would describe its color or a number_of_doors attribute to describe if it's a 2 door or 4 door.

Just like in the real world, objects in programming are typically able to do things. Our car object would be able to drive, brake, turn, etc...

In Ruby, <q>doing things</q> is accomplished by methods. A method is like a function or algorithm that gives an object a set of instructions on how to accomplish a task. You ask the object to do the task by calling the method of the object.

In Ruby - and many other programming languages - objects are constructed using classes. A class is simply a blueprint for how to build an object. You define the attributes and methods for the object in the class. Once you have defined the attributes and methods, you can create or <q>instantiate</q> an instance of the class to use in your program. The class instance will have all of the capabilities defined in the class.

Each instance of a class might have attributes that vary from instance to instance. For example, not all cars are red, so you would want to be able to instantiate a car object that could be a different color. You could build a separate class for red cars, blue cars, yellow cars, etc... but it would not be very efficient: <code>duplicate_code == bad? true</code>

Luckily, there are instance variables in Ruby classes that allow you to set the state of a particular attribute in a class instance. They do not affect the other objects created from the class.

Let's see how it works.

We can build a Ruby class using the class definition keyword:

{% highlight ruby %}
class Car
  # code goes here
end
{% endhighlight %}

That was easy. Now we can create an instance of the class using the new method of the car class and save it to a variable my_car.

{% highlight ruby %}
my_car = Car.new
{% endhighlight %}

Great, we have a new car object, but we haven't defined anything about the state of the car. To solve that, we can set up  instance variables in the class definition. They are prefaced with a @ symbol and they have scope anywhere within the class definition.

We can use a special initialize method that can accept arguments at the time of instantiation. These arguments are then assigned to instance variables within the initialize method.

{% highlight ruby %}
class Car

  def initialize(make, model, year, color)
    @make = make  # assign the argument make to the instance variable @make
    @model = model
    @year = year
    @color = color
  end

end

my_car = Car.new("Honda", "Fit Sport", 2010, "orange")
{% endhighlight %}

Now we can create a car object from the car class and set its instance variables. Unfortunately, we still can't access the variables to read or change them once they have been set up.

We need reader and writer methods to accomplish this (these are similar to getter and setter methods in other languages).

In our class definition, we could add a reader method like so:

{% highlight ruby %}
def make
  @make
end
{% endhighlight %}

Or a writer method:

{% highlight ruby %}
def color=(color) # The equals sign is part of the method name.
  @color = color
end
{% endhighlight %}

These allow you to access the instance variable using a dot notation on your class instance.

{% highlight ruby %}
my_car.make
=> "Honda"

my_car.color=("red")
my_car.color = "red" # This format also works thanks to syntactic sugar
p "I just painted my car!"
{% endhighlight %}

Ruby has a nice shortcut for setting up reader and writer methods. The shortcut uses the attr_reader, attr_writer or attr_accessor methods. The attr_reader is a reader method, attr_writer is a writer method and attr_accessor will both read and write to a particular instance variable.

The examples above could be rewritten:

{% highlight ruby %}
attr_reader :make
attr_writer :color
{% endhighlight %}

or

{% highlight ruby %}
attr_accessor :color # To read and write
{% endhighlight %}

So far, we've set up some attributes for our car class and saved them in instance variables and we can access the instance variables using reader and writer methods.

Our car still can't really do anything. To fix that, we need to add some instance methods.

Instance methods are methods defined within the class definition that can be called on an instance of a class.

We can create a start_engine method that will start the car. It can interact with a boolean instance variable `@ignition_on` so we don't damage the starter.

{% highlight ruby %}
def start_engine
  @ignition_on = true if @ignition_on == false
end
{% endhighlight %}

We can also add methods that accept arguments to give the car object more flexibility. Here's a drive method that can accept a direction argument so you could use forward, backward, left, right, North, South, etc...

{% highlight ruby %}
def drive(direction)
  @moving = true
  puts "We are driving #{direction}."
end

my_car.drive("forward")
=> "We are driving forward."
{% endhighlight %}

Using classes is a great way to create smart usable objects that can contain attributes and execute actions in Ruby. For fun, the code below shows a more flushed out car class. Until next time...


{% highlight ruby %}
class Car

  def initialize(make, model, year, color, fuel_type, fuel_capacity, fuel_measurement)
    @make = make
    @model = model
    @year = year
    @color = color
    @fuel_type = fuel_type
    @fuel_capacity = fuel_capacity
    @fuel_measurement = fuel_measurement
    @fuel_level_percent = 100
    @ignition_on = false
    @moving = false
  end

  # Reader method to check the fuel gauge
  attr_reader :fuel_level_percent

  def start_engine
    # The car won't start if you're out of gas
    if @fuel_level_percent > 0
      # Start the ignition if it is not already on
      @ignition_on = true if @iginition_on == false
    else
      puts "Time to fuel up!"
    end
  end

  def fuel_up
    # Turn off the engine before filling up
    @ignition_on = false if @ignition_on == true
    # Determine percent of tank empty and multiple by fuel capacity to know how much fuel to buy
    fuel_needed = (1 - (@fuel_level_percent.to_i/100.00)) * @fuel_capacity.to_i
    p "You need #{fuel_needed} #{@fuel_measurement} of #{@fuel_type}!"
    # Fill up the tank
    @fuel_level_percent = 100
  end

  def drive(direction)
    # move the car object
    @moving = true
    puts "We are driving #{direction}"
  end

  def brake
    @moving = false if @moving == true
  end

end

my_car = Car.new("Honda", "Fit Sport", 2010, "orange", "gas", 9, "gallons")
{% endhighlight %}