# Dynamic Types
Dynamic types are required for doing things like generics
and OOP like programming. In Grime they are implemented by
using a simple vtable for every trait implementation.

## Source Representation
In grime dynamic types are specified with a `dyn` keyword.
```grime
trait Shape {
	func sides() -> U32
}

type Polygon : {
	sides: U32
}

impl Shape for Square {
	func sides(&self) -> U32 {
		ret := self.sides
	}
}

func test() -> U32 {
	val polygon := Polygon {
		10
	}
	val shape := polygon as dyn Shape

	ret := shape.sides()
}

```

## Runtime Representation
In Grime dynamic types are specified with the `dyn` keyword.
it is represented as a vtable like the following

```c
// trait Shape
struct _vtable_grime_test_Shape {
	// a pointer to the actual data of an object on the stack
	void *data;

	// every function in a vtable is represented as a function pointer
	uint32_t (*sides)(void *data);
};

struct _grime_test_Polygon {
	uint32_t sides;
}

// impl Shape for Square {
uint32_t _grime_test_Square_sides(struct _grime_test_Square *self) {
	uint32_t ret = self->sides;
	return ret;
}

struct _vtable_grime_test_Shape _impl_grime_test_Shape_grime_test_Square = {
	NULL,
	&_grime_test_Square_sides
}
// }


uint32_t _grime_test_test() {
	uint32_t ret;

	struct _grime_test_Polygon polygon = {
		10
	}
	struct _vtable_grime_test_Shape shape = _impl_grime_test_Shape_grime_test_Square;
	shape.data = &_grime_test_Polygon;
	
	ret = shap.sides();
	
	return ret;
}
```

## Dropping
When the value is dropped the data inside is not free'd as it is stack allocated and free'd later
though the drop function for that object is called. We never need to heap alloc inside a vtable unless
a subtype, like Vec, Box or Arc is used but this is handled by their drop functions.


