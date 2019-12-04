# Basics
## Functions
Basic grime functions can easily be run in C and, if they are named correctly, in Grime. Grime can be configured to generate C headers as well as the Grime module outline files.
```grime
mod xyz.grime.example
use xyz.grime.core.Int
use xyz.grime.io.println

func main() -> Int {
	println("Hello, World");
	ret = 0;
}

```

```c
#include <grime/core.h>
#include <grime/io.h>

struct xyz_grime_core_Int *xyz_grime_example_main() {
	struct xyz_grime_core_String _0 = _default_xyz_grime_core_String; // creates a struct with the default value (this has all of the function pointers)
	struct xyz_grime_core_String *_0_ref = &_0;
	_0_ref->_init(_0_ref); // runs any of the initialisation needed by the string
	_0_ref->_literal(_0_ref, "Hello, World"); // creates the string object from a char *, starts with `_` because this is managed by the compiler not the user;

	xyz_grime_io_println(_0);
 
	struct xyz_grime_core_Int ret;
	struct xyz_grime_core_Int *ret_ref = &ret;
	ret_ref->_init(ret_ref);
	ret_ref->_literal(_0_ref, 0);
	return ret_ref;
}

int main() {
	struct xyz_grime_core_Int *ret = xyz_grime_example_main();
	return ret->_c_val(ret); // function that gets the c integer value;
}

```
