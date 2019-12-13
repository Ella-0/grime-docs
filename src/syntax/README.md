# Syntax

## Functions
In Grime functions 

## The Entry Point
In Grime the entry point of a program is the main function.

```grime
mod example::hello-world
use std::core
use std::io

func main() -> Int {
	println("Hello, World");
}
```

## Classes, Masks

```grime
mask Stack<T> {
	val size: Int;
	val pop: Stack<T>;
	val peek: T;
	func push(element: T) -> Stack<T>;
}

class EmptyStack<T> : Stack<T> {
	impl val depth: Int = 0;
	impl val Pop: Stack<T> {
		// Illegal State
	}
	impl func push(element: T) {
		return NonEmptyStack<T>.create(this, element);
	}
}

class NonEmptyStack<T> : Stack<T> {
	impl val depth: Int;
	impl val peek: T;

	impl func push(element: T) {
		return NonEmptyStack.create(this, element);
	}

	build create(tail: Stack<T>, head: T) {
		pop = tail;
		peek = head;
		depth = tail.depth + 1;
	}
}
```

## Enums

```grime
enum LogLevel {
	LOG;
}
```


## Operator Overloading
