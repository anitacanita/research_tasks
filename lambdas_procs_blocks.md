## Blocks, procs and lambdas

### Block

A block of code is not an object, it's part of the syntax of the method call.

In the example below, the `.each` method takes a block of code that will return the product of each element in the array multiplied by 10.


```Ruby
array = [1,2,3]
array.each {|x| puts x * 10} #=> [10, 20, 30]
```


### Proc

A proc is an instance of `Proc`. It's an object that takes a block of code, turning it into its body.

```Ruby
Proc.ancestors
#=> Proc < Object

pr = Proc.new {puts "Whoa! I'm inside a Proc's block."}
pr.call
#=> Whoa! I'm inside a Proc's block
```

In the example below, we're defining a `gen_times` method that returns a new instance of Proc with a given factor and when that proc gets called with a number, it will multiply that same number by that factor. In the example we'll be calculating the factor 3 of the number 10: `10 * 3`. Step by step, this is what it does:

1. `times3 = gen_times(3)` assigns the factor to the `Proc` instance.
2. `times3.call(10)` calls the `Proc` object with the multiplicand number
3. `#=> 30` the return value is product of the multiplicand and the factor.

```Ruby
def gen_times (factor)
  return Proc.new { |n| n * factor}  
end

times3 = x
times3.call(10) #=> 30
```

### Lambda

*Note: Both procs and lambdas are `Proc` objects.*

`lambda` is a method that returns a `Proc` object, using the provided block as the function body.

It's like a flavour of the `Proc` class and lambda-flavoured procs are different from regular ones in 3 different ways:

1) lambdas require explicit creation - wherever Ruby creates Proc objects implicity, they're procs and not lambdas.

2) `return` inside a lambda triggers an exit from the body of the lambda

```Ruby
def return_test
  l = lambda { return }
  l.call             # this triggers a return from the body of the lambda,
  puts "Still here!" # the execution of the method continues where it left off
  p = Proc.new { return }
  p.call             # this triggers a return from the return_test method
  puts "You won't see this!"
end

return_test #=> Still here!
```
3) lambda-flavoured procs have to be called with the right number of arguments

```Ruby
l = lambda { |x,y| p x,y }
l.call(1,2)
#=> [1,2]

l.call(1)
#=> ArgumentError: wrong number of arguments (1 for 2)

```
