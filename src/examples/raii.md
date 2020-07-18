```grime
mod examples::raii

trait RAII {
	func clean()
}

trait InputStream<T> {
	func recv() -> Option<T>
	func recvAll(count: UInt) -> [T]
}

trait OutputStream<T> {
	func send(val: T) -> Bool
	func sendAll(vals: [T]) -> UInt
}

type FileInputStream : {
	cFile : []
}

impl FileInputStream {
	func open(file: File) -> FileInputStream {
		ret := {
			fopen(file.path(), "r")
		}
	}
}

impl InputStream<UByte> for FileIntputStream {
	func recv() -> {
		
	}
}

type FileOutputStream : {
	cFile : []
}





```
