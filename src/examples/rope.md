# Rope

```grime
mod std::rope

trait Rope<T> {

	func valueAt(index: Int) -> Option<T>

}

type EmptyRope<T> {
	next: Option<Rope<T>>
}

type NonEmptyRope<T> {
	vals: [T]
	next: Option<Rope<T>>
}

impl Rope<T> for EmptyRope<T> {
	func valueAt(index: Int) -> T {
		if (!next.null()) {
			ret = next.valueAt(index: Int)
		} else {
			ret = Option<T>()
		}
	}
}

impl Rope<T> for NonEmptyRope<T> {

}
```

```c

struct _grime_type_g_std_option {
	bool null;
	struct _grime_generic data;
};

struct _grime_generic {
	uint32_t size;
	void *data;
};

struct _grime_trait_g_std_rope_Rope {
	uint32_t size;
	void *data;
	struct _grime_type_g_std_option (*valueAt)(uint32_t index)
};

struct _grime_type_g_std_option _grime_impl_g_std_option() {
	struct _grime_type_g_std_option ret;
	ret.null = true;
	ret.data = NULL;
	return ret;
}

struct _grime_type_g_std_option _grime_impl_g_std_rope_Rope_g_std_rope_EmptyRope_g_valueAt(_grime_std_rope_Rope this, uint32_t index) {

	struct _grime_type_g_std_option ret;
	
	if (!)

}



```
