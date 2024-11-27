# markdown calendar creator

idea for this project: i use markdown to write and plan my life. I want the next 5 to 10 days to appear as headers.. for example, if today is august 08 thursday. Then this would be generated:

# August 08 Thursday 2024
# August 09 Friday 2024
# August 10 Saturday 2024
# August 11 Sunday 2024
# August 12 Monday 2024
# August 13 Tuesday 2024
# August 14 Wednesday 2024

I want to write this program in C/C++/Rust. 


1. get todays date
2. get the next weeks date
3. have the string formatted as above. # before each date and after a \n for new line
4. print output to the terminal


Shouldn't be too hard. Let's have them as little side quests and see how well I do. 

1. Get Todays Date

Get the current system time...
- SystemTime::now()

Calculate the number of days since the UNIX epoch...
- calculating the number of days since january 1 1970 by dividing the seconds by the number of seconds in a day

Convert the number of days to a NaiveDate using a library like chrono, but if we stick strictly to std, this step will be manual...
- approximates the current date from the number of days. considering leap years and months with varying days

Use a custom function to map the day of the week and month to their names...
- adjustment to find the day of the week
- maps numeric month and day values to their names and prints the formatted date

```rust
use std::time::{SystemTime, UNIX_EPOCH, Duration};
use std::fmt;


const SECONDS_IN_DAY: u64 = 86_400; // 24 * 60 * 60

fn main(){

    //current system time
    let now = SystemTime::now();

    // calc duration since the UNIX epoch

    // calc the number of days since the epoch

    // get the current yr month and day

    // get the day of the week (0=Monday, 6=Sunday)

    // Map days and months to their names

    // Format and print the result
}

```



--- 

Help me finish this design doc by helping me choose a language. 

---

pros/cons of each:
- c is straightforwar and easy
- c has high performance and low level management
- extensive library and tools available for c
- the cons of manual memory mangement can lead to bugs and vulnerabilities
- c's error handling is primitive compared to modern languages. 
- c++ supports classes and inheritance and other OOP programming features
- the rich standard libraries will help with data nd time operations
- the language is more complex thanC and has more features to learn and manage. 
- also requires memory managmement and must be careful but we have tools like RAII to help or RALL
- rust is memory safe 
- rust has built in concurrency support
- rust has a steeper learning curve if you are new to its ownership model


RAII ~ Resource Acquisition Is Initialization is a C++ programming technique. 
This technique gaurantees that a resource is available to any function that may access the object
https://en.cppreference.com/w/cpp/language/raii

Ownership in Rust
- unique feature
- enables Rust to make memory safety guarantees without needing a garbage collector. It's important to understand how ownership works. 
- how ownership works
    - set of rules
    - the compiler checks the rules
    - I am going to learn by walking thru examples that focus on common data structure: Strings!


- borrowing
- slices
- how does rust lay out data in memory?

Stack and Heap
- Most programming languages don't make you think about the stack and the heap very often. Boooooo
- in a systems programming language like rust, whether a value is on the stack or the heap affects how the langauge behaves and why you have to make certain decisions. 
- both the stack and the heap are parts of memory available to your code to use at runtime but they are structured in differnt ways
- the stack stores values in the order it gets them and removes the values in teh opposite order
- the heap is not organized that well. putting the data on the heap u request a certain amount of space. the memory allocator guy finds an empty spot in the heap that is big enough, marks it as being in use, and returns a pointer ( ADDRESS TO THE LOCATION WE JUST MARKED AS IN USE) 
- because the pointer (the ADDRESS) has a known size we can store the pointer on the stack, but when you want the actual data you must follow the pointer (GO TO THE ADDRESS)
- Pushing to the stack FASTER THAN allocating to the heap
    - because the stack does not use the allocator. It knows its going to just add it to the top of the stack
    - because the heap uses the allocator, it needs to find a spot that meet the space requirements
- accessing data in the heap is slower than accessing data on thes tack because you have to follow a pointer to get there
- when code is called. lets say a function is called. the arguments of the function (which might be pointers to data on the heap) and the functions local variables get pushed onto the stack. when the function is over, those values get popped off the stack
- keeping track of what parts of code are using what data on the heap, minimizing the amount of duplicate data on the heap and cleaning up unused data on the heap so you don't run out of space are all problems that ownership addressess. 
- once I understand ownership, I wont need to think abt the stack or the heap very often. I need to know the main purpose of ownership is to manage heap data can explain why it works the way it does.


Finally, the rules of Ownership. 

- Each value in Rust has an owner

--> Makes sense, Every variable is like a car and car's have keys and those keys decide who the owner is. But theres always one owner

- There can be one owner at a time,

--> Continuing the analogy, a car can really only have one owner. whoever has the keys. Honestly if i swap keys with the certificate for the car or whatever but still stands. 

- When the owner goes out of scope, the value will be dropped. 

--> When the owner leaves, honestly, the analogy is go carts now. When someone comes to the gokart rink they get a gokart and they are the owner. If they leave they are no longer the owner and the go kart is brough in for regular maintenance (we run a pretty dangerous go kart track)

A variables scope ....
- scope is the range within a program for which an item is valid
- 2 important times here: when someone shows up to the go kart track and it remains valid until it goes out of scope

the String type ...
- so before this I have only covered data types with known sizes that can be thrown onto the stack
- lets look at one stored on the heap
- String literals are immutable
- Second string type for variable amounts of storage (mutable) at compile time. if unknown at compile time. 

- some code

``` let mut s = String::from("hello");; ```
s is mutable

```rust
s.push_str(", world!");
println!("{s});
```

- we are adding a string literal to our mutable string

Memory allocation ...
- string literal --> known contents at compile time so the text is hardcoded directly into the final executable
- string literals are fast and efficient
- properties only come from the string literals immutabilitiy
- cant put a blob of memory into the binary for each piece of text whose size is unknwon at compile time and whose size might change while running the program
- need to allocate an amount of memory on the heap, unknown at compile time, to hold the contents
- memory must be requested rom the memory allocator at runtime
- i need a way of returning this memory to the allocator when we are done with our Sring
- when we call String::from the implementation requests the memory it needs (first part done)
- the second part is different. for languages with garbage collectors (GC) the GC keeps track of and cleans up memory that isnt being used anymore and I dont need to think about. 
- in languages without a GC its my responsivility to identify when memory is no longer being used and to call code to explicity free it, just as we did to request it. 
- doing this correctly has historically been a difficult programming problem
- if I forget I will waste memory and if I do it too early I will have a invalid variable. I need to pair exactly one allocate with exactly one free.
- the rust approach: the memory is automatically returned once the variable that owns it goes out of scope

more code...

```rust

{
    let s = String::from("hello"); // s is valid from this point forward

    //do stuff with s
}

// this scope is over, and S IS   NO LONGER VALID

```

- THERE IS A NATURAL POINT AT WHICH WE CAN RETURN THE MEMORY our String needs to the allocator: When s goes out of scope. 
- WHen the variable goes out scope, Rust calls a special function for us
- This function is called drop
- the author of String can put the code to return the memory
- Rust calls drop automatically at the closing curly bracket
- in C++ this pattern of deallocating resources at the end of an item's lifetime is sometimes called Resource Acquisition Is Initialized. The drop function in Rust will be fammilliar to you if you have used RAII patterns. 
- Crazy we have RAII in this document from earlier. I am going to learn both and understand all these systems programming languages in unison

Variables and Data interacting with move...
- multiple variables can interact with the same data in different ways in Rust
- look at an example

```rust

let x = 5;
let y = x;

```

- we can guess this is doing: bing the value 5 to x and then make a copy of the value in c and bind it to y. Exactly
- since integers are simple values with a known fixed size I can easily push it onto the stack

Let's look at the string version...
```rust

let s1 = String::from("hello");
let s2 = s1;

```

This ends up being more complicated ...
A String is made up of 3 parts under the covers. 
1. ptr -> pointer to the memory that holds the string (for example: 0)
2. len -> 5
3. capacity -> 5

index | value
=============
0   |  h
1   |  e
2   |  l
3   |  l
4   |  o

- length is how much memory in bytes the contents of the String are currently using
- capacity is the total memory in bytes that the string has recieved from teh allocator
- difference between length and capacity matters but not in this context, so for now, its fine to ignore the capacity

- double free error: when both variables go out of scope they will both try to free the same memory and this can lead to memory corruption and lead to security culnerabilities
- to ensure memory safety, after the line let s2 = s1
- rust considers s1 as no longer valid, therefore, rust doesnt need to free anythning when s1 goes out of scope. 

```rust

let s1 = String::from("hello");
let s2 = s1;

println("{s1}, world!");

```

- to ensure memory safety after the line s2 = s1;, rust considers s1 as no longer valid. 
- therefore rust does not need to free anything when s1 goes out of scope. 
- if u try to use s1 after it wont work. you will get an error which says: value borrowed here after move
- the terms shallow copy and deep copy 
- copying the pointer length and capacity without copying the data sounds like making a shallow copy. 
- Rust also invalidates the first valiable, instead of being called a shallow copy, its known as move. 
- rust will never automatically create deep copies of your data. therefore any automatic copying can be assumed to be inexpensive in terms of runtime performance. 

variables and data interacting with clone ...
- if we do want to deeply copy the heap data of the String not just the stack data we can use a common method called clone. 
- we will discuss method syntax in ch5 but bc methods are a common feature in pl you have seen them before
- here is an example of the clone method in action: 

```rust

let s1 = String::from("hello")l
let s2 = s1.clone();

println!("s1 = {s1}, s2 = {s2}");

```

This works just fine and explicity produces the behavior shown in figure where the heap data does get copied. 
- when u see a call to clone u see that some arbitrary code is being executed and that code may be expensive

Stack-Only Data: Copy...
- code using integers

```rust

let x = 5;
let y = x;

println!("x={x},y={y}");


```

- this code seems to contradict what we just learned: we don't have a call to clone but x is still valid and wasn't moved into y
- the reason is that types such as integers that have a known size at compile time are stored entirely on the stack so copies of the actual values are quick to make
- this means theres no reason we would want to prevent x from being valid after we create the variable y. 
- in other words, theres no differnce between deep and shallow coping here, so calling clone wouldn;t do anythign different from the usual shallow copyigng and we can leave it out

- rust wont let us annotate a type with Copy if the type or any of its parts has implemented the Drop trait. 
- the rtpe needs somethign special to happen when the value goes out of scope and we add the Copy annotation to that type, we will get compile-time error

- So what types implement the Copy trait. 
- check the documentation for the given type to be sure but as a general rule any group of simple scalar values can be implement Copy and nothing requires allocation or is some form of resource can implement Copy
- all integer types like u32
- bool type true and false
- floating points
- char type

Ownership and functions...
- passing a value to a function = assigning a value to a variable
- passing a abariable to a function will move or copy
- just as assignment does

more code ... ;P

```rust


fn main() {
    
    let s = String::from("Hi"); // s comes into scope

    let x = 5; // x comes into scope


    // s's value is moved into tehe function
    takes_ownership(s);

    // s is no longer valid here

    makes_copy(x); // x would move BUT i32 is a Copy so its ok to use x after!

}

fn takes_ownership(some_string: String) { //some_string comes into scope
    println!("{some_string}");
} // drop is called here 

fn makes_copy(some_integer: i32){ // some_integer comes into scope
    println!("{some_integer}");
} // some_integer goes out scope. nothign special

```

- if we tried to use s after the call to takes_owenership.. Rust would throw a compile time error.
- these static checks protect us from mistakes

- try adding code to main that uses s and x and see where you can use them and wehre the ownership ruels prevent you from doing so. 


Return Values and Scope ...
- Returning values can also transfer ownership
- functiosn that return some value with simmilar annoations as those above

```rust

fn main(){


    let s1 = gives_ownership();

    let s2 = String::from("hello");

    let s3 = takes_and_gives_back(s2);
}

fn gives_ownership() -> String {
    let some_strig = String::from("yours");
    some_string
}

fn takes_and_gives_back(a_string: String) -> String {
    a_string
}

```

- the ownership of a variable follows the same pattern every time: assuming a value to another variable moves it
- when a variable includes data on the heap goes out of scope the value will be cleaned up by drop nless ownership of the data has been moved to another variable

- while this works, taking ownership and then returning owenrship with every function is a bit tedious. 
- what if we want to let a function use a value but not take ownership
- its quite annoying that we pass in also needs to be passed back if we want to use it again

- rust has a feature for using a value without transferring ownership called references

https://doc.rust-lang.org/book/ch04-01-what-is-ownership.html

Next section on References and borrowing...

https://doc.rust-lang.org/book/ch04-02-references-and-borrowing.html

I don't know if I have it in me to read another section of this book. I guess I have finished chapter 4 section 1 in this document. ALl of this somehow relates to C++ RAII format except here the compiler checks if you followed it correctly. 
