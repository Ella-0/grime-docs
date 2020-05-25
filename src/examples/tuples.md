# Tuples

```grime
type Vector3f : (
	x: Float
	y: Float
	z: Float
)

impl Vector3f {
	add(b: Vector3f) -> Vector3f {
		ret = Vector3f(this.x + b.x, this.y + b.y, this.z + b.z)
	}
}

func main() -> Int {
	
}
```
