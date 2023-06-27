
# Code 

```rust
struct Foo {
	x: u32
}

impl Foo {

	fn eat(self) { // function with an argument without the & as a reference
		println!("eating");
	}

	fn something(&self) { // function with an argument that is a reference to the object
	
		println!("else");
	}
}

fn main(){
	println!("Hello World"); // This is just a normal println! macro statement

	let g = Foo {x: 5};
	g.eat(); // operations causing failure
 	g.something();  // operations causing failure

}
```

# Info

As is this code will fail because of the order that we called the .eat() and .something() functions. For many other languages this may seem like a program that should have any reason to fail but in rust it will because of the **Borrow Checker**. This is what makes rust rust and gives.

# So why does this fail? 

This fails because when we are calling the `eat()` function on _g_ we are passing the entire variable to the `eat()` function therefore giving up the `main()` functions ownership to it. So when we try to call _g_.`something()` it fails because main has already given ownership to the g function and the `something()` function no longer has access to it 
 
## Fix

This works with one simple fix and that is to execute the `something()` function before the `eat()` function.


```rust
struct Foo {
	x: u32
}

impl Foo {

	fn eat(self) { // function with an argument without the & as a reference
		println!("eating");
	}

	fn something(&self) { // function with an argument that is a reference to the object
	
		println!("else");
	}
}

fn main(){
	println!("Hello World"); // This is just a normal println! macro statement

	let g = Foo {x: 5};
	g.something();  // operations causing failure
	g.eat(); // operations causing failure

}
```

### Why does this work?

You can see that we changed ordering of how the `.something()` and the `.eat()` functions are called with `something()` now being before the `eat()`.

If you take this code and run it will now compile/work because when we are calling the `.something()` function we are only passing a reference to the _g_ value and not passing the entire thing which means now we can reuse that value and pass it again to the `.eat()` function but again after the `eat()` function we can no longer call g because the entire value has been passed to the eat function.


The  way that we change whether or not we take a reference or the entire object into a function is with the  **&** operator that we place in front of the arguments of the function we are writing at the time.

So:

```rust
fn function(&self) {
	///
}
```

Rather than:

```rust
fn function(self) {
	///
}
```