# Syntax

##
A class is defined with the following syntax
```grime
class MyClass {
	
}
```

## Adding Fields
```grime
class MyClass {
	var MyField: Int;
}
```

## Adding Methods
A method can be added to a class using the following syntax.
```grime
class MyClass {
	var myField: Int;

	func myFunc(x: Int) -> Int {
		ret = myField + x;
	}
}
```
A method **CAN NOT** mutate any of the objects fields. The following code would not compile for that reason.
```grime
class MyClass {
	var myField: Int;

	func myFunc(x: Int) {
		myField += x;
	}
}
```
## Adding a Constructor
Constructors are similar to methods except they can mutate the fields of an object. However, constructors delete all previous contents of an object. Constructors can be named or unnamed but there can only be one unnamed constructor per class.
```grime
class MyClass {
	val myField: Int;
	
	build (val field: Int) {
		myField = field;
	}
}
```
### Adding a Named Constructor
```grime
class MyClass {
	var myField: Int;
	build create(val field: Int) {
		myField = field;
	}
}
```
### Extracting Methods From Constructors
Constructors can call methods however these methods can not mutate the class unless specified using the following syntax.
```grime
class MyClass {
	var myField: Int;
	func myFunc(x: Int) -> Int {
		ret = myField + x;
	}
	mut func myMutFunc(x: Int) {
		myField = x;
	}
	build (x: Int) {
		myMutFunc(x);
	}
}
```
Normal methods **CAN NOT** call mutable methods.

## Traits
Traits provide some pre-implemented methods, fields and constructors and some pre-defined methods, fields and constructors that must be implemented by a child class or trait. They are defined with the following syntax.
```grime
trait MyTrait {

}
```
You can add a method, constructor or variable to a trait with the following syntax.
```grime
trait MyTrait {
	var x: Int;
	func myTraitFunc(x: Int) -> Int;
	build (y: Int);
}
```
This method and constructor have not been implemented by the trait so it must be implemented by a child class or trait with the following syntax.
```
class MyClass : MyTrait {
	impl func myTraitFunc(x: Int) -> Int {
		ret = x + 5;
	}

	impl build (x: Int) {
		x = y;
	}
}
```
Fields **DO NOT** need to be implemented by a child class or trait as they have a default "Getter, Setter" implementation. They, along with methods and constructors with a default implementation, can still be implemented to override the default implementation. The "Setter" of a field **CAN NOT** be accessed outside constructors or methods that have been marked to mutate the object. The Setter of a field **CAN NOT** be overridden; because of the immutability of objects there is simply no need. A field's "Getter" can be implemented using the following syntax.
```grime
class MyClass : MyTrait {
	impl var x: Int {
		ret = x;
	}
}
```
## Destructor
A class can only have one destructor. This destructor is defined with the following syntax and is only ever called by the runtime not the programmer. It allows the programmer to do things like close files or clean up any unsafe memory that was being used when the object is garbage collected.
```
class MyClass : MyTrait {
	demolish {
		
	}
}
```
