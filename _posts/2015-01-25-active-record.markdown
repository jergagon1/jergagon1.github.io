---
layout: post
title:  "Active Record: An ORM Framework"
date:   2015-01-25 17:00:00
categories: technical
tags:
- orm
- active record
- ruby
- mvc
- model
---

To get an understanding of Active Record, there are a few concepts that must be touched on.

To have persistant data of any size or complexity in web applications, you need to store your data in a database. There are different database structures, but a common one is a relational database.

A relational database is used to store information in tables where a column represents an attribute of data and a row represents an individual data record. For example, if a web application needs to store a person's address, there would be an address column in a customer table and the specific customer would be represented by a row.

Web application frameworks are systems that allow servers to be programmed using an object-oriented language like Ruby.

In the model-view-controller (MVC) web application framework Ruby on Rails, the "model" is responsible for rules, logic and data management. Active Record is the "model" in that relationship.

More specifically, Active Record is the mechanism of linking an object-oriented class to a relational database table. The class wraps the database table so that when a class instance is created, a linked row is created in the database table. Due to this relationship, it is known as a framework for Object Relational Mapping (ORM).

Active record allows you to use the features of class-based object-oriented programming to streamline database information management. You can use OOP features like inheritance to create logical hierarchies in your database.

Also, you can use the object-oriented language to create and update data to minimize SQL programming.