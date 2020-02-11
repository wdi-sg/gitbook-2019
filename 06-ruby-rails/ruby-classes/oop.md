# OOP in Ruby


## What is a class?
Data and actions on that data.


## Why use classes?

- encapsulation

- separation of concerns

- modeling real world situations

- clean

- will fit in nicely with db tables and the ERDs we will make

- in rails we will organize our models and controllers around classes


## How to create classes


## Class Definition of a person

Let's create our first class.

**person.rb**

```ruby
class Person

end
```

This defines a **class** definition of a `Person`. The *class* keyword denotes the *begining* of a class definition.


### An object is an **instance** of a person

To create a new *instance* of our *class* we write the following:

```ruby
Person.new
```

A class is an imprint of a thing we want to create.
![](https://media.giphy.com/media/6djJPJeaWwTrW/giphy.gif)


## Storing data in a class instance

1. Specify the attributes we want to store.
- these are attributes of the class / thing we are modeling:
```
Person:
  - age
  - weight
  - name
```

These are specified in the class as **instance variables**

Values that are contained within each **instance** of a class.

## Class methods

We can set methods within the class that can be called to do something with the data it contains.

```
class Person

  def set_name( name )
    @name = name
  end

  def greet
    puts "Hello! My name is #{@name}."
  end
end

jane = Person.new
jane.set_name("jane")
john = Person.new
john.set_name("john")



```

Both values we created are instances of the same class, but contain different data.



## Operating on class instance data


```
class Person

  def set_name( name )
    @name = name
  end

  def greet
    puts "Hello! My name is #{@name}."
  end

  def set_weight( weight )
    @weight = weight
  end

  def salad
    @weight -= 1
  end

  def bacon_cheeseburger
    @weight += 1
  end
end

jane = Person.new
jane.set_name("jane")
jane.set_weight(50)

john = Person.new
john.set_name("john")
john.set_weight(50)

john.salad
jane.bacon_cheeseburger
```




The idea behind object oriented programming is that we encapsulate some attributes / data of the thing we are modeling, and then write class methods that operate on that data.




Another example:

```
class Person

  def initialize(age: 0)
    @age = age
  end

  def set_name( name )
    @name = name
  end

  def greet
    puts "Hello! My name is #{@name}."
  end

  def birthday
    @age += 1
  end
end

jane = Person.new(20)
jane.set_name("jane")
jane.birthday
```



## Specifying Objects
OOP is a method for organizing our data and functions / actions on that data. It's meant to try to model real-world processes and data as close as possible.

It's not the only solution or always fit to the problem, but for CRUD type web systems it tends to work well.



### How to specify / model data

How do you know what objects you need? In fact we have already done a data modeling exercise- creating ERDs. When you are creating an object/class/data model for an app or business, an ERD is what you would make.

In the real world an ERD sits somewhere between a table-level database specfication, and a class implementation specification. (It depends on the job.)

Note: *This ERD has nothing to do with DB tables. You are specifying a set of classes, and the data and methods in each class.*


#### Hospital Patient ERD

We want to record patients in the hospital.

- They should have an age and weight.

- If we want to automatically track their age we can add a birthdate.

- We can have doctors. Paitents can be assigned doctors.

- Doctors can prescribe medications. Medications need to be taken every x days or hours.

- Doctors have schedules. Their number of working hours can't exceed x hours.

- We can add appointments.

- Etc.

```ruby
class Patient
  def initialize( name, age, weight )
    @name = name
    @age = age
    @weight = weight

    @doctors = []
    @medications = []
  end

  def name
    @name
  end

  def age
    @age
  end

  def add_doctor( doctor )
    @doctors.push( doctor )
  end

  def doctors
    @doctors
  end

  # add medication methods
end

class Doctor
  def initialize( name )
    @name = name
  end

  def name
    @name
  end
end

class Medication

  def initialize( name, doctor )
    @name = name
    @doctor = doctor
  end

  def name
    @name
  end

  def doctor
    @doctor
  end

  # prescription details methods

end

susan = Patient.new('susan', 23, 23)

bill = Doctor.new('bill')

susan.add_doctor( bill )

panodol = Medication.new('panodol', bill)

# susan.add_medication( panodol )
```


#### Over-fitting objects
You can make everything an object in your system, but be careful, because each object you add also adds complexity. Can your data be a class attribute instead?

### Pairing Exercise

- Pick one or more of the following analyze what it primarily does & try to draw the tables & relationships. Don't try to model every single piece of data within the app. Start with the most important models and add on from there.

  - DBS Bank
  - Medical Clinic
  - Restaurant
  - Tutoring Center


#### 1
An ERD diagram, using crow's foot notation, of whatever app you choose.  For example:


<p align="center">
  <img src ="https://www.edrawsoft.com/images/examples/entity-relationship-diagram.png">
</p>

> Note: this example has "Items" as placeholders for the attributes.

**Warning: DO NOT try to implement the entire app. That will be way too big. Start with the major features. Then move on to the next part (2).** If you get done with the below, come back and add to the ERD.

#### 2
Come up with some example data for each important part of the app.

How are they represented in classes?

What methods would you write to act on that data?

Write the classes and methods and create the individual instances. Classe instances will contain other class instances.

You might have calculations on that data such as `account.calculate_interest`, or you might have methods that send or do something: `student.send_session_reminder_email`- for such methods, simply assume you will write in this actual code later. Leave a comment or `puts` a message.


