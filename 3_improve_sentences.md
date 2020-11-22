## Understanding self
self points to the instance object itself. Use self when calling an instance object in a class or when calling that instance object.
If your code is inside an instance method, self is an instance of that class. In other words, self is an object.:

**Example of self:**
Let's run this program
```
class Author
    puts "Class name is: #{self}"
end
```
The output will be:
```
Class name is: Author
```
As you can see in the above program, a valiable`#{self}` points to that self class and it prints the class name.
