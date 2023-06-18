<h1>Minimal Rust Cookbook for JS/TS developer </h1>

## Setup
    curl https://sh.rustup.rs -sSf | sh
    sudo apt-get install build-essential
    mkdir <rust_project_name>
    cd <rust_project_name>
    touch ./src/main.rs Cargo.toml

**Cargo.toml**

    [package]
    name = "<rust_project_name>"
    version = "<version_number>"  <-- numbers; such as 0.0.1
    edition = "2021"

    [dependencies]
    
## Basic

**Functions, classes, and variables**

| JS/TS Concepts | Rust Concepts | Note |
| --- | --- | --- |
| class ClassName{} | struct structName{} | |
|  | impl implName{} | Used to define function for struct |
| function functionName{} | fn fnName(){} | |
| let varName = <br/> const constName = | let mut varName =  <br/> let constName =  | (notice the use of mut) |

**Primitives**

| Primitives | JS/TS Usage | Rust Usage | Note | Example |
| --- | --- | --- | --- | --- |
| Integer | number | i8  \| u8 <br/> i16 \| u16 <br/> i32  \| u32 <br/> i64  \| u64 <br/> <br/> isize \| usize | *(signed \| unsigned)* <br/> <br/> <br/> <br/> <br/> pointer-based | let x: i8 = 5; (fixed value/const in JS/TS) <br/> let mut x: u32 = 5; (mutable value/let or var in JS/TS) |
| Floating-Point | number | f32 \| f64 | | let y: f64 = 10.2376; |
| Boolean | boolean | bool | | let z: bool = true; |
| Character | string | char | | let x: char = "hello world"; |
| Array | Array\<T> | [T; N] <br/> Vec\<T> | *(fixed size)* <br/> *(dynamic size)* | let numbers: [i32; 3] = [1, 2, 3]; <br/> let mut numbers: Vec\<i32> = vec![1, 2, 3]; |
| Slice | - | &[T] <br/> &mut[T] | fixed <br/> mutable | let numbers_slice: &[i32] = &numbers[1..3]; |
| Tuple | tuple | (T1, T2, ...) | | let person: (String, u32, bool) = ("Alice".to_string(), 25, true); |

**Macro**

| Function | Macro |
| --- | --- |
| println(); | println!(); |

Without ```!``` before a function will cause Rust to recognize it as function, which in example ```println``` will be interpreted as ```fn println()``` instead of printing out some text.

**Example**

    struct Person{
      name: String,
      age: i8,
    }

    impl Person{
      fn greet(&self){
        println!("Hello, my name is {}, and I am {} years old.",self.name, self.age)
      }
    }

    pub(crate) fn main(){
      let person = Person{
        name: String::from("Nicholas"),
        age: i8::from(30),
      };

      person.greet();
    }

```pub(crate)``` before ```fn main()``` is optional, even without it ```fn main()``` will execute normally.

**Build**

    cd <to_rust_project_folder>
    cargo build
