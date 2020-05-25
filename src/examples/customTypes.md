# Custom Types
Custom Types allow for names to be given to sepcific value types similar to `typdef` in C.

## Definition

Custom Types are defined with the following syntax

```grime

type Name : Type

// e.g

type Vector3f : (
	x: Float, 
	y: Float,
	z: Float
)

type StrongOption : (
	isNull : Bool,
	data : []
)

type WeakOption : (
	isNull : Bool,
	data : {}
)

```
