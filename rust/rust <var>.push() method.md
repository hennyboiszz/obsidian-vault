
# What does it do?

The String.push() method accepts a single variable of the char data type `A` for example, and it takes that char and adds it to the end of the string


```rust
let x = String::from("Hello");

x.push("A");
println!("{}", x);
```
# Common Pitfalls while using

The .push() function can only accept a single char at a time if we want to append more than one char onto a variable then we have to use the `push_str()` function that rust provides us

