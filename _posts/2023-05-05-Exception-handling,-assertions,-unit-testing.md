There are two main kinds of `errors` in Python. 

One is a `syntax error` - you included a token in a phrase that ought not have been there. Maybe it was a character, a parenthesis, a semi-colon, but something was spelled wrong and Python compiler could not parse your program.

The other is an `exception`. An exception is basically a logical error in your code - you tried to divide by zero, concatenate a string with an integer, or call a variable that was not defined. 

The basic syntax is like this:

```
try:
	# An operation occurs here

except ExceptionName:
	# We would specify an exception above, like an IOError or TypeError, that       would create some output. 
except ExceptName2:
	# And we cam actually have multiple exceptions for a single try block           which is neato.
```

Just to give an example of wha this could look like, observe the below:

```
try:
	fh = open("testfile", "r")
	fh.write("This is my test file for exception handling!!")
except IOError:
	print "Error: can\'t find file or read data'"
else:
	print "Written in the file successfully"
```

So in this example, we are trying to write to a file called `fh`. If we cannot write to it because the file does not exist, an IOError will be raised. If not, we'll make it to the `else` block and we'll just get a notice that the file has been written to successfully.

There's also something called `finally` for when we always want something to be executed, which looks like this:

```
try:
	# An operation goes here, which may be skipped because of some exception
except Blah:
	# That's not a real error code or anything, this is just an example
	  though, okay?
finally:
	# This would be executed always, no matter what happens
```

You can also force exceptions to be raised so long as they have been previously defined, whether they are built-in or user-made. For example:

```
try:
    raise NameError('HiThere')
except NameError:
    print('An exception flew by!')
    raise
```

So here, the print would look like:

```
An exception flew by!

Traceback (most recent call last):
  File "<stdin>", line 2, in <module>
NameError: HiThere
```

You can also chain exceptions, which can help with traceback:

```
def func():  
raise ConnectionError  
  
try:  
	func()  
except ConnectionError as exc:  
	raise RuntimeError('Failed to open database') from exc
```

Exceptions are used in a process called `Unit Testing`, which is a methodology for testing out small pieces of a script as you build to make sure they are functional. A bit confusingly, while `Unit Testing` is a collection of practices in Computer Science, `UnitTest` is actually a module you have to import, like this:

```
import unittest

def div(a,b):
	return a/b
class raiseTest(unittest.TestCase):
	def testraise(self):
		self.assertRaises(ZeroDivisionError, div, 1,0)

if __name__ == '__main__':
	uniittest.main()
```

Let's break this down line by line. 

```
import unittest
```

This imports the test module.

```
def div(a,b):
	return a/b
```

This defines a method for dividing `a` over `b`.

```
class raiseTest(unittest.TestCase):
	def testraise(self):
		self.assertRaises(ZeroDivisionError, div, 1,0)
```

This defines an object that contains a method that runs `assertRaises`, for which there is a specific syntax:

```
assertRaises(exception, callable, *args, **kwds)
```

The `args` in this case are just `div` - it's the method we are running through the unit test.  The `kwds` (keywords) are the parameters for the method we are defining as the `arg`. 

In this case, since we are trying to divide 1 by 0, the error would be raised. If we changed the script to:

```
import unittest

def div(a,b):
	return a/b
class raiseTest(unittest.TestCase):
	def testraise(self):
		self.assertRaises(ZeroDivisionError, div, 1,1)

if __name__ == '__main__':
	uniittest.main()
```

Then no exception would be raised. 

`For now this is as far as I am going to get here.`

#drafting
