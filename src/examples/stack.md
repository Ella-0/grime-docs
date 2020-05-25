# Example Stack Implementation

```grime
mod std::stack

type Stack<T> : {
	peek: T,
	pop: {Stack},
)

impl Stack<T> {
	func () -> Stack {
		return
	}

	func push(a: T) -> Stack {
		ret := Stack<T>(a, {this});
	}
}
```
