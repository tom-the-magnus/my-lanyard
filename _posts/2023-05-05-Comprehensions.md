Comprehensions are used to transform one list into another list using only a single line of code. So if you already have a list and want to produce a new list by performing some operation on every element of the existing list, you use a comprehension.

There are list comprehensions and dictionary comprehensions. This document addresses both.

## List Comprehensions

The syntax is:

```
`new_list = [expression for item in old_list]`
```

So, all list comprehensions have these elements:

- a new list
- an expression ( the operation to be preformed on the iterable )
- a for statement with a variable
- an iterable ( e.g a list/tuple )

And in this case, those specifically are:

- a new list - `new_list` 
- an expression - `expression` 
- a for statement with a variable - `for item`
- an iterable - `old_list` 

Here's an example:

```
# An existing list
numbers = [1, 2, 3, 4, 5] 

# A new list we are going to create with list comprehension
squares = [num**2 for num in numbers]
```

So here we have two lists, `numbers` and `squares`. `numbers` is an existing list of values. `squares` is the list we are going to create using our list comprehension. 

To recap, for any list comprehension, we must have these things:

- a new list
- an expression
- a for statement
- a list to be iterated on

In this example, these thing are:

- a new list - `squares`
- an expression - `num**2`
- a for statement - `for num`
- a list to be iterated on - `numbers`

If we ran this code, `squares` would be equal to: 

```
[1,4,9,16,25]
```

You can also include conditional statements on the end of a comprehension to exclude certain values from the final list. For example, say we wanted a list of squares, but only if they were even. We could write: 

```
# An existing list
numbers = [1, 2, 3, 4, 5] 

# A new list we are going to create with list comprehension
squares = [num**2 for num in numbers if num % 2 ==0] 
```

Since we've added that `if num % 2 ==0 ` at the end, we'll only get even outputs. So the final list produced would be:

```
[4,16]
```

## Dictionary Comprehensions

First, if you can wrap your head around list comprehensions, dictionary comprehensions are syntactically and logically very similar. There are a few important differences which are worth understanding though. 

Before we discuss these, let's discuss some built-in methods to transforms dictionaries, as you'll really always have to do this before putting a dictionary through a comprehension.

First, you can use these built-in methods to generate a list of the values or keys in a dictionary.

```
dict1 = {'a': 1, 'b': 2, 'c': 3, 'd': 4}
key_list = dict1.keys()
val_list = dict1.val()
```

Pretty simple - it just takes all the keys or values and puts them into a list, so they'd look like:

```
key_list = [a,b,c,d]
val_list = [1,2,3,4]
```

If we wanted a list of the key value pairs, each pair being an element in the list, we would use:

```
dict_items = dict1.items()
```

Which would look like:

```
dict_items = ([('c', 3), ('d', 4), ('a', 1), ('b', 2)])
```

What does this mean? **It means that very often you can work around making a dictionary comprehension by converting the dictionary values to a list.**

That said, there are going to be times when that is not possible and you will have to write a comprehension for an object of the dictionary type. Good news, though - you'll probably be able to understand the syntax for a dictionary comprehension pretty easily:

```
dict_variable = {key:value for (key,value) in dictonary.items()}
```

You can add a condition by doing something like:

```
dict_list = {key:value for (key,value) in dict_items if value < 5000}
```


## Alternative Methods

There are other ways to achieve this same outcome, though. For example, with list comprehensions, we could just use a for-loop like this:

```
numbers = [1,2,3,4,5]  
squares =[]  
  
for num in numbers:  
	if num % 2 == 0:  
		squares.append(num**2)  
```

Or you could even use a combination of map, filter, and lambda to achieve this output.

```
numbers = [1, 2, 3, 4, 5] 
squares = list(map(lambda num: num**2, numbers)) 
even_numbers = list(filter(lambda num: num % 2 == 0, numbers)) 
```

To read more about that, review the [[map(), filter(), lambda]] article.

So, there's a bunch of different ways we could do this same task. What are the unique advantages of comprehension, then? 

**We use comprehension because it many times provides the most legible and least line-intensive solutions for transforming an iterable.**  If you need to produce a new iterable based on an existing iterable using a basic operation or conditional, comprehension is a highly legible, low-line method for this. 

Well done, that's it! If you want to check out some related tutorials, I've linked them below. 

- [[map(), filter(), lambda]]

