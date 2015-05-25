---
layout: post
title:  "Arrays and Hashes in Ruby"
date:   2014-12-07 15:30:00
categories: technical
tags: array hash
---
In this week's tech blog, I will dive into arrays and hashes in the Ruby programming language. What are they? How do they work? Why would I use them? Do they have anything to do with corned beef? Spoiler alert: the answer to the last one is NO!

I could start off with some dry technical definitions about what they are (an integer-indexed list of...), but I find that these things make more sense when you identify the problem they are solving. Most things in computer programming are created to solve a problem whether it's making something faster or easier, sorting complex sets of data, communicating information or whatever.

Here's a simple scenario: I want to build an application where I can store the top 100 current pop singles. My app needs to store the following information:

* Song Ranking/Position (This part's important, right? It tells which artist has the #1 single)
* Song Title
* Artist
* Album

Here are the features that I need in my app:

* The ability to move songs up and down the list week-to-week as the songs become more or less popular.
* Keep the song title, artist and album all together as the songs are moved up and down the list.
* The ability to query my app to find things like <q>Which artist has the #10 single</q> or <q>What are the top 10 songs?</q>

Okay, so where to start?

In computer programming, you can store information in variables. Variables point to little pieces of computer memory. The information stored in that location can change (hence the name <q>variable</q>), but essentially you are giving a name to a memory location: the thing that I'm calling `my_variable` occurs here. Variables are, borrowing the words of George Carlin, <q>A place for my stuff</q>.

If I put all of the songs, artists and albums in separate variables, they won't really have a relationship to one another. How would I know that <q>Don't</q> is by Ed Sheeran and that it's on his album <q>X</q>? How would I sort all of these songs by popularity?

So, we have identified two problems to solve:


1. We need to keep the song name, artist and album together and be able to reference which piece of information is which, like <q>Maroon 5</q> is the artist and <q>Animals</q> is the song. There could be (and was) an artist <q>The Animals</q> so we need to make sure we can tell the difference.
2. We need to be able to take the groups of values that we created in step 1 and put them in a numerical order based on popularity.

### Problem 1 ###

We need a data structure that can store a collection of values (<q>Blank Space</q>, Taylor Swift, 1989) and reference those values with a name or <q>key</q> for each value (song_name, artist, album). Luckily, someone encountered this problem before in ruby programming and created the data structure `hash`.

### Solution: The Hash ###

A hash in Ruby is a collection of key, value pairs. You could write the syntax:

{% highlight ruby %}
song_1_hash = {
  "song_name" => "Blank Space",
  "artist" => "Taylor Swift",
  "album" => "1989"
}
{% endhighlight %}

The first thing in quotes is the key and it points to (=>) the second thing in quotes which is the value. Each different key value pair is separated by a comma. The quotes just mean the things are strings of text. You can put things other than strings in hashes (like numbers) and in those cases you would omit the quotes. The quotes are only for strings.

The key in Ruby hashes is often just a symbolic name for the value it is pointing to, so you can use a different syntax which does not take up all the memory of storing the separate keys as text strings. You can use a symbol:

{% highlight ruby %}
song_1_hash = {
  :song_name => "Blank Space",
  :artist => "Taylor Swift",
  :album => "1989"
}
{% endhighlight %}

It's easy - you just leave off the quotes for the key and put a colon before it. Now I can reference my song name like so:

{% highlight ruby %}
song_1_hash[:song_name]
{% endhighlight %}

I would get back:

{% highlight ruby %}
"Blank Space"
{% endhighlight %}

Okay, so by using hashes we have a solution to the first problem. We can keep all of the information about a particular song in one object and individually reference the song name, artist and album. What about the second problem?

### Problem 2 ###

Now we need to sort each song numerically. We want to know which song is #1, 2, 3, 4.... The order is important. Luckily, this problem has also been addressed previously in the ruby language!

### Solution: The Array ###

An array is a collection of values where each value has an associated number or <q>index</q>. The index identifies the position of the value in the list. Let's look at an example:

{% highlight ruby %}
my_array = [
  "first thing",
  "second thing",
  "third thing"
]
{% endhighlight %}

So, to get the first item in the array:

{% highlight ruby %}
my_array[1]      #returns the value below
"second thing"
{% endhighlight %}

Wait, what just happened? There's a catch: array indexes start with 0 instead of 1.

To get the first item using the correct syntax:

{% highlight ruby %}
my_array[0]      #returns the value below
"first thing"
{% endhighlight %}

Okay, so how do we use our song hashes and an array to create the top 100 list?

An array can contain any other type of Ruby object: strings, numbers, other arrays and even hashes.

{% highlight ruby %}
my_array = [
  "string here",
  42,
  ["nested", "array", "here", 26],
  13.0,
  {:first_name => "Jeremy", :last_name => "Gagon"}
]
{% endhighlight %}

So, to start building my app, I would create an empty array top_100_songs:

{% highlight ruby %}
top_100_songs = []
{% endhighlight %}

I could then assign a hash to each postion of the array based on it's current ranking:

{% highlight ruby %}
top_100_songs[0] = {
  :song_title => "Animals",
  :artist => "Maroon 5",
  :album => "Animals"
}
top_100_songs[1] = {
  :song_title => "Don't",
  :artist => "Ed Sheeran",
  :album => "X"
}
# etc...
{% endhighlight %}

so now my array is:

{% highlight ruby %}
top_100_songs = [
  {
    :song_title => "Animals",
    :artist => "Maroon 5",
    :album => "Animals"
  },
  {
    :song_title => "Don't",
    :artist => "Ed Sheeran",
    :album => "X"
  },
# etc...
]
{% endhighlight %}

I can find out the number one hit song by typing:

{% highlight ruby %}
puts top_100_songs[0][:song_title]    # returns the value below
"Animals"
{% endhighlight %}

There are ruby algorithms (or methods) associated with the array object that will allow me to sort, insert, move or remove the songs in the array as songs lose or gain popularity. For example, the code below adds a new song to the beginning of the top 100 list and shift all the previous values by 1 place to the right.

{% highlight ruby %}
top_100_songs.unshift({
  :song_title => "Black Widow",
  :artist => "Iggy Azalea featuring Rita Ora",
  :album => "The New Classic"
})
{% endhighlight %}

We've created our app and solved our problems using the ruby hash and array objects. To recap, a hash is a collection of key value pairs and an array is a collection of items where each item has a numerical index (starting with 0!!!).

Until next time.
