# cRust 
## Why Rust?
- Easier to write good Rust than good C++ (because compiler yells at you in Rust if you don't) and no header files

## Links
- Easy rust  https://www.youtube.com/watch?v=9bgI1SKIsv0 (https://dhghomon.github.io/easy_rust/Chapter_52.html)

## Basic syntax
- Comments: `/* multiline */` or `// single line` or `/// doc generate`
-
### Hello world
	```
	fn main() {
		// Comments are with the typical double slash
		// Exclamation points signify macros
		println!("hello world")
	}
	```

### Printing
- Use the `{}` to fill in the argument `println!("hehe {}", 69)`
- Or use positional args: `println!("hehe {0}{1}", 69, 420)`

### Loops
Let's say we want to iterate over a `Vec`. `let mut vec1 = vec![1, 2, 3];` We can: 
1. Over a range using `start..end`: `for i in 0..vec1.len() {}`
2. 
3. `loop`: an infinite loop


#### Over indices / range
Rust has no C-style for loops. We must use `..` operator:

```



```

## Macros
- A form of metaprogramming (code that writes other code)
- Macros vs. functions:
	- Macros can have a variable number of params (ex. `println!("hello {}", world)` or a single (see above))
	- Functions have a pre-determined number of paramters

## impl (Implementation)
- Adds methods to a struct to make it more useful (like an object)
	```
	struct Rectangle {
		width: u32,
		height: u32
	}
	impl Rectangle {
		// &self allows you to access width and height
		fn print_description(&self) {
			println!("Rectangle {} x {}", self.width, self.height);
		}
	}
	fn main () {
		let my_rect = Rectangle {width: 10, height: 5};
		my_rect.print_description();
	}
	```

## Attributes
- Generates code so you don't have to put `impl Debug for Book`
- Syntax: 
	- `#[derive(Eq)]` (just for the following struct)
	- For whole file use `!`: `![derive(Eq)]` 
- Specific attributes:
	- `#[test]` will test following function when running
		- `fn my_test() { assert_eq!*(1, 2)} }` will print fail 
	- `#[cfg(target_os = "linux")]` Runs function a different way  based on if it's running on linux
- Example:
	```
	// This #[derive(Debug, Clone, Copy)]
	struct Book {...}
	```
## Traits
- Can be thought of as powers 🦸‍♀️ - abilities you give it
- Similar role to multiple inheritance in other languages
- Seen inside attributes (but can't be done for most)
- Ex. 
	```
	struct Animal {
		name: String
	}
	trait Dog {
		fn bark(&self) {
			println!("woof")
		}
	}
	impl Dog for Animal {}
	fn main() {
		let loaf = Animal {
			name: "Loafy".to_string()
		}
		loaf.bark()

	}
	```
## Scary Rust data types 
- `<Box>` Dictate that data needs to be stored on heap

### Arc: Atomic reference counted
- An arc is allocated on the heap, and allows shared ownership.
- If you clone it, it'll point at the same allocation as the source Arc
- When you need to mutate an `Arc`, use `Mutex` or smth


## Building an API
### Warp: Webserver framework (allows HTTP)


### Tokio
- Asynchronous runtime for Rust (provides `async`/`await`)
- 








