# Strong and Weak Pointers

Grime deals with 2 different types of pointers. Strong pointers and Weak Pointers

## Rules

A weak pointer can not be passed to a function requiring a strong pointer but a strong pointer can be passed to a function requiring a week pointer.

```grime
mod test::strong-weak

func push(ref: [Int], val: Int) {
	...
}

func peek(ref: {Int}) -> Int {

}

func main() -> Int {
	
}

```

