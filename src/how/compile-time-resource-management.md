
## Simple

```grime

func main() -> [Int] {
	val x: {Int} = {0, 1, 2, 3} // stack allocates array
	val y: {Int} = {0, 1, 2, 3}
	val z: [Int] = [0, 1, 2, 3] // heap allocates array


	//x cleaned
	//y cleaned
}

```

```grime

func main() -> [File] {
	val x: [File] = [File::open("file1"), File::open("file2")]

	
}

```

```grime

func take(x: [Int]) {

}

func borrow(x: {Int}) {

}

func test1() -> Int {

	ret = 0

	val x: [Int] := [1, 2, 3, 4]
	take(x)
	// x now cleaned
	take(x) // fails use after clean but expected strong

}

func test2() -> Int {

	val x: [Int] := [1, 2, 3, 4]

	if (time > 1000) {
		take(x)
	}
	take(x) // can't gaurentee x's existence

	ret = 0
}

func test3() -> Int {

	val x: [Int] := [1, 2, 3, 4]
	val x: {Int} := {1, 2, 3, 4}

	if (time > 1000) {
		borrow(x)
	}
	take(x) // succeds; borrow doesn't free x

	ret = 0
}

func test4() -> [Int] {
	
}

```



```grime

impl Rope<T> {
	build func main(
		file0: File /*passes by copy*/, 
		file1: [File] /*takes a boxed file and takes ownership. will clean up at end of construct or at obj destroy*/,
		file2: {File} /*takes a boxed file and doesn't take ownership. will not clean up */) {

	}
}

```
