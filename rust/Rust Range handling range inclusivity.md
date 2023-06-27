#rust 

# info

previously when we used the range notation and an  iterator like  `a..b` to provide a list of numbers to a _for_ x _in_ list_of_xs specifically `1..100`.

The thing we did not mention is that by default when we are using range notation the values the .. iterator creates are not inclusive so in our previous example `1..100` only the values 1, 2, 3 .. 99. Would be the values considered in the _for in_ function. 

To get all the values of 100 we have two options:

```rust
for x in 1..101{ // just adds one to the selected range so that we can get the value of 100 to be used in the function
	println!("{}", x);
}
```

Or by using the _=_ option when choosing a range:

```rust
for x in 1..=100 {
	println!("{}", x)
}
```

The _=_ after the _.._ are what makes the range provided inclusive


