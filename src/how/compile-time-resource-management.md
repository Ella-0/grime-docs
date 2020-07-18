# Compile Time Resource Management


```grime



fun abc(a: Copyable, b: NotCopyable, c: &Type) -> &Type {


	a dropped here
	b dropped here
	c not dropped
}

fun add(a: Int, b: Int) -> Int {

}

```


```c

// return ref needs a point on the stack to return the value to

// copyable structs can be passed by value

// noncopyable are passed by refference and dropped as they are moved
// but we don't copy the values inside them because that could be slow
// depending on the size of the struct

// values passed by refference are not dropped

// Box values when dropped internally call free()

struct Type *ret abc(struct Type *ret, struct Copyable *a, struct NotCopyable *b, struct Type *c) {


	drop(a);
	drop(b);
	// c is not dropped
	return ret; // return the reference to make expr evaluation easier
}

```

```llvm
define i32 _grime_add(i32 %0, i32 %1) {
entry:
	%2 = add %0, %1
	ret %2
}


```

```c
struct _grime_std_Box {
	struct _grime_dyn *mem,
};

struct _grime_std_Box _grime_std_Box_new(struct _grime_dyn value) {
	struct _grime_std_Box ret = {
		malloc(value.size)
	};
	*ret.mem = value;
}

struct _grime_std_Vec {
	size_t count;
	struct _grime_dyn *mem;
};

void _grime_std_Box_grime_std_Drop_drop(struct _grime_std_Box *self) {
	free(self->mem);
}

struct _grime_std_Vec _grime_std_Vec_new(struct _grime_dyn value) {
	return {
		0,
		NULL,
	};
}

struct _grime_std_Vec_push(struct _grime_std_Vec *self, struct _grime_dyn value) {
	self->mem = realloc((self->count + 1) * value.size)
	self->mem[self->count] = value;
	self->count++;
}

void _grime_std_Vec_grime_std_Drop_drop(struct _grime_std_Vec *self) {
	free(self->mem);
}


```
