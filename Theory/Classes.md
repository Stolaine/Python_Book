# Classes
- Creating a new class creates a new type of object.
- Class instances can have attributes to define its state and methods for modifying its state.
- Classes are created at runtime and can be modified after creation.
## Python Scopes and Namespaces
- **Namespace**
	- It is a mapping from names to objects.
	- The name following a dot is called an attribute.
	- Attributes can be read-only or writable.
	- If writable then there can be assignment as `modname.attrname = value` or there can be deletion as `del modname.attrname`.
	- `del` keyword will remove the `attrname` from `modname`.
	- Created at different moments and have different lifetimes.
	- When python interpreter starts a namespace is created which contains built-in names and it is never deleted.
	- The global namespace for a module is created when module definition starts.
	- Local namespace for a function starts at funtion definition and ends when the control is given back to the caller or an exception occurs.
- **Scope**
	- Textual region where a namespace is directly accessible.
	- At any time there are three nested scopes
		1. Innermost is the one which contains local names. It is searched first. They contain non-local and non-global variables.
		> There can be various local scopes neseted in each other.
		2. Middle one contains the current module's global names.
		3. Outermost is the namespace containing built-in names. It is searched last.
	- If a name is declared `global` then it gets its namespace in middle one.
	- To access and update the variables found outside the innermost scope `nonlocal` is used, if not then the outer varialbe is read-nly and assignment will create a new variable in the innermost scope.
	- Class definition create separate namespace in the local scope.
	- `global` statement is used to declare that the variable is located in the middle scope (global scope below the builtin level) and can be updated in innermost scope as well.
	- `nonlocal` statement is used to declare that the variable is located in the scope just above the local scope in the hierarchy.
	
	```
	def scope_test():
		def do_local():
			spam='local spam'
		def do_nonlocal():
			nonlocal spam
			spam = 'nonlocal spam'
		def do_global():
			global spam
			spam - 'global spam'
		spam = 'test spam'
		do_local()
		print(spam)
		do_nonlocal()
		print(spam)
		do_global()
		print(spam)
	scope_test()
	print(spam)
	```
## A First Look at Classes
### Class Definition Syntax
```
class ClassName:
	statement-1
	...
	statement-N
```
- Class definitions must be executed before they are used.
- At the start of class definition a new namespace is created and treated as current local space. Any new declaration to variables and functions are bind to this namespace.
- At the end of class definition a class object is created and the previous local space becomes active and the class object is bind to this namespace.
- Class definition can start anywhere e.g. inside if-else statements or inside functions etc.
### Class objects
- **Attribute References**
	- `className.attrName` attribute name can be name of variable or name of function defined inside the class.
	- It will return either a object of a data type which can be built-in or user-defined or a function object.
- **Class Instantiation**
	- `x = className()` Resembles a parameter less function to create a new instance of the class.
	- To instantiate a class instance to an initial state \_\_init\_\_() is defined in the class definition.
	- It takes an argurment `self`(**compulsory**) and can take other arguments as well. In that case the other arguments must be passed at the time of Instantiation.
### Instance Objects
> There are two kinds of attributes. One defined(functions) or initialized(data members) at the time of class definition and other using the **Attribute Reference** with instance objects.
- **Data Attribute References**
	- There is no need of declaring data attributes. Initialization takes care of that.
	```
	x = MyClass()
	x.counter = 1
	```
- **Method References**
	- A method is a function that 'belongs to' an object.
	- There is a difference between `x.f` and `MyClass.f`. Former is Method object while latter is a function object.
	- `x.f` is a method of `\_\_main\_\_.MyClass` instance while `MyClass.f` is a function in moudle \_\_main\_\_.
### Method Objects
- Method objects can be assigned to some variable like `xf = x.f`.
- When method is called the instance variable is passed to the function to which it is referring. i.e. `x.f()` is equivalent to `MyClass.f(x)`.
- When a non-data attribute is referenced which happens to be a function in class definition an abstract object is created with the function and the instance variable, and when the referenced attribute is called the referred function is called with instance variable as the first argument.
### Class and Instance Variables
- Class variables are for attributes and methods shared by all instances of the class.
- Instance variables are for data unique to each instance of the class.
## Random Remarks
