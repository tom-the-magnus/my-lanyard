
In [[Comprehensions]], I mentioned that you could use these functions to perform the same operations that a list comprehension would. So what are these things anyway? Let's find out.

Let's look at this script:

```
numbers = [1, 2, 3, 4, 5] 
squares = list(map(lambda num: num**2, numbers)) 
```

Now, before we break down this script, there a few things to learn about map() and lambda().

First, map is really just a function for transforming a list of values. Typically, you define a method outside the map() function and then call it using the map function. Here's a simple example:'

```
def multiply_2(n):
	return n * 2

numbers = [1, 2, 3, 4, 5] 
times_two = map(multiply_2, numbers)) 
```

In this case, map() would take the `numbers` list, process each element according to `multiply_2`, and output this:

```
[2,4,6,8,10]
```

So, for the map() function, the syntax is really:

```
method_name = map(other_method, list)
```

**So the inputs for a map() method are a method and a list/tuple.** The map function returns an object that is called a **map object**. 

But wait Tom, what if I want to make our code a bit more legible and concise?! What would we do? Is there no hope?! 

Fret not my sapling - just use `lambda`.

`lambda` allows you to define what's called an "anonymous function", which is really just a function that has no `def` . Really, it behaves just like `def`  does when we're typically writing methods, but we don't have to give the lambda function a name and whatever lambda function we write cannot be called outside of where we write it.

Alright, so let's return to that script we were looking at before:

```
numbers = [1, 2, 3, 4, 5] 
squares = list(map(lambda num: num**2, numbers)) 
```

So there are a few parts to this script, those being:

- list - this is a built-in function that makes sure the object generated is of the data type list
- map - this is a built in takes a function and an iterable as parameters and returns a map object. to put that into English - it goes over a list with a certain method and returns a transformed copy of the list.
- lambda - in this instance, this is used to create the method right in the map() method itself. the lambda function is meant to be interpreted as "for each num in the list called numbers, multiple it by two and append it to the new list called squares" 
- numbers - this is the iterator, a list of numbers

So, as we can see, lambda and map are pretty cool for transforming lists. 

Oh wait but no! What if I don't want to make a new list by transforming my iterable, but actually *exclude* values from the new list? There must be no hope...well, time do just give up and - 

No way! There's a way to do this as well using `filter()`. It's really almost exactly the same as map, it's just that it's used to exclude values from the list you create. Here's an example.

```
numbers = [1, 2, 3, 4, 5] 
even_numbers = list(filter(lambda num: num % 2 == 0, numbers))
```

The syntax is the exact same as map, except **filter returns an iterable containing only the elements that satisfy the condition. It filters out elements based on the condition.**

So really, map() is used if you want to transform and keep every element. You use filter() if you want to exclude certain elements. 