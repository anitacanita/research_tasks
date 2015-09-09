#### Inheritance

Inheritance is very nice when your classes have a clear hierarchical structure between them. However, it can get in the way when used inappropriately.

Inheritance is used to indicate that one class will get most or all of its features from a parent class.It can happen in three ways:

1) Implicit Inheritance - actions on the child imply an action on the parent.

````
class Parent

  def implicit()
    puts "PARENT implicit()"
  end
end

class Child < Parent
end

````

2) Explicit Override - actions on the child override the action on the parent.

  The problem with having functions called implicitly is sometimes you want the child to behave differently.

````
class Parent

  def override()
    puts "PARENT override()"
  end
end

class Child < Parent
  def override()
    puts "CHILD override()"
  end
end
````


3) Override Before and/or After - actions on the child alter the action on the parent.

The third way to use inheritance is a special case of overriding where you want to alter the behavior before or after the Parent class's version runs.

````
class Parent
  def altered()
    puts "PARENT altered()"
  end
end

class Child < Parent
  def altered()
    puts "CHILD, BEFORE PARENT altered()"
    super()
    puts "CHILD, AFTER PARENT altered()"
  end

end

````

## Composition vs Inheritance
Inheritance is useful, but another way to do the exact same thing is just to use other classes and modules, rather than rely on implicit inheritance. If you look at the three ways to exploit inheritance, two of the three involve writing new code to replace or alter functionality. This can easily be replicated by just calling functions in a module.


```
class Other

  def override()
    puts "OTHER override()"
  end

  def implicit()
    puts "OTHER implicit()"
  end

  def altered()
    puts "OTHER altered()"
  end
end

class Child

  def initialize()
    @other = Other.new()
  end

  def implicit()
    @other.implicit()
  end

  def override()
    puts "CHILD override()"
  end

  def altered()
    puts "CHILD, BEFORE OTHER altered()"
    @other.altered()
    puts "CHILD, AFTER OTHER altered()"
  end
end
```

The question of "inheritance versus composition" comes down to an attempt to solve the problem of reusable code. You don't want to have duplicated code all over your software, since that's not clean and efficient. Inheritance solves this problem by creating a mechanism for you to have implied features in base classes. Composition solves this by giving you modules and the ability to call functions in other classes.

If both solutions solve the problem of reuse, then which one is appropriate in which situations? The answer is incredibly subjective, but we can follow three guidelines for when to do which:

1. Avoid something called "meta-programming" at all costs, as it is too complex to be useful reliably. If you're stuck with it, then be prepared to know the class hierarchy and spend time determining where everything is coming from.

2. Use composition to package up code into modules that are used in many different unrelated places and situations.

3. Use inheritance only when there are clearly related reusable pieces of code that fit under a single common concept or if you have to because of something you're using.


Example of Inheritance using ships.

`````
Class Ship
  def initialize(coordinates)
    @position = ''
    @position << coordinates
    @number_of_hits = []
  end

  def location
    return @position
  end

  def receive_hit
    number_of_hits.pop
    fail "You sunk me!" if number_of_hits.empty?
  end
end

Class Submarine < Ship
  def initialize(coordinates)
    @number_of_hits = ['X','X']
    super()    
  end
end

`````
