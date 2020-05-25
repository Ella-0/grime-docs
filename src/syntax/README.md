# Syntax
Grime is a statically typed language that aims to bring a modern syntax to C whilst adding features such as strong and weak references to help prevent resource management errors.

## Functions

## The Entry Point
In Grime the entry point of a program is the main function.

```grime
mod test::entry

use func std::io::println

func main() -> Int {
	println("Hello, World");
}
```

## Includes


```grime
mod test::includes

use mod std::maths // includes the math module
use trait std::string::String // includes String trait
use func std::io::println // includes the println function from std::io

func main() -> Int {
	val vec1 : [Float] = {1.0f, 6.0f, 3.0f}
	val vec2 : [Float] = {3.0f, 4.0f, 2.0f}
	val vec3 : [Float] = maths::dot3f(vec1, vec2)

	del vec1
	del vec2

	val out : [UByte] = String.formatCreate("({0}, {1}, {2})", vec3) // no string:: needed as trait included not mod
	
	del vec3

	println(out) // no io:: needed because func included not mod
	del out
	
	ret = 0
}

```
