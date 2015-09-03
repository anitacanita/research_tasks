## Classes

A class is like a blueprint that allows you to build objects (instances of that class). This blueprint (if designed properly) will have all the attributes the object needs. It will have:
* __States__ (values stored in variables for example)
* __Behaviours__ (methods which interact with state to make the object do whatever we need it to do)

For example, if we want to build a car, you need to plan what a car should look like, how it should behave, and what attributes it should have. So by our analogy, you draw a blueprint by creating a `Car` class `class Car ... end`. We can give it `wheels`, `engine`, `speed`, `colour`, etc.

Then we just pass the blueprint (class) to our assembly line: `car = Car.new`, our new `car` will have all the methods and properties we drew on our blueprint which will allow the new `car` instance to behave and look as we planned.

Instance method = car.accelerate
Class method    = Car.new

"car" is a variable containing an instance of a class
"Car" is the actual class.

There can be MANY versions of car
There can only be ONE Car.  
