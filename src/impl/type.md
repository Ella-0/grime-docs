# Type System

The type system will need to keep track of several things.

## The Type Name
This holds all of the basic type implementation and is used as a key for looking up functions
for that specific type

## The Lifetime
This is used to indentify the scope that a variable has which dictates when it will be dropped
and where it can be used

## Ownership
This is used to tell who owns the value and weather or not it has been moved

## Copy
Weather or not it uses copy semantics or move semantics

## Implementation
In the initial bootstrap compiler it will be implemented with something like this:
```c
struct Type {
	struct ModId id;
	struct ScopeId scope;
	bool owns;
	bool copyable;
}
```

When selfhosting it will be implemented more like this
```grime
type ModId : U64

type ScopeId : U64

type Type : {
	id: ModId,
	scope: ScopeId,
	owns: Bool,
	copyable: Bool,
}
```
