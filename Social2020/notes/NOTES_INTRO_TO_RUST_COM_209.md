
```rust

// /$$$$$$$  /$$   /$$ /$$$$$$ /$$       /$$$$$$$         /$$$$$$   /$$$$$$   /$$$$$$   /$$$$$$ 
// | $$__  $$| $$  | $$|_  $$_/| $$      | $$__  $$       /$$__  $$ /$$$_  $$ /$$__  $$ /$$$_  $$
// | $$  \ $$| $$  | $$  | $$  | $$      | $$  \ $$      |__/  \ $$| $$$$\ $$|__/  \ $$| $$$$\ $$
// | $$$$$$$ | $$  | $$  | $$  | $$      | $$  | $$        /$$$$$$/| $$ $$ $$  /$$$$$$/| $$ $$ $$
// | $$__  $$| $$  | $$  | $$  | $$      | $$  | $$       /$$____/ | $$\ $$$$ /$$____/ | $$\ $$$$
// | $$  \ $$| $$  | $$  | $$  | $$      | $$  | $$      | $$      | $$ \ $$$| $$      | $$ \ $$$
// | $$$$$$$/|  $$$$$$/ /$$$$$$| $$$$$$$$| $$$$$$$/      | $$$$$$$$|  $$$$$$/| $$$$$$$$|  $$$$$$/
// |_______/  \______/ |______/|________/|_______/       |________/ \______/ |________/ \______/ 

// /$$$$$$   /$$$$$$  /$$      /$$        /$$$$$$   /$$$$$$   /$$$$$$ 
// /$$__  $$ /$$__  $$| $$$    /$$$       /$$__  $$ /$$$_  $$ /$$__  $$
// | $$  \__/| $$  \ $$| $$$$  /$$$$      |__/  \ $$| $$$$\ $$| $$  \ $$
// | $$      | $$  | $$| $$ $$/$$ $$        /$$$$$$/| $$ $$ $$|  $$$$$$$
// | $$      | $$  | $$| $$  $$$| $$       /$$____/ | $$\ $$$$ \____  $$
// | $$    $$| $$  | $$| $$\  $ | $$      | $$      | $$ \ $$$ /$$  \ $$
// |  $$$$$$/|  $$$$$$/| $$ \/  | $$      | $$$$$$$$|  $$$$$$/|  $$$$$$/
// \______/  \______/ |__/     |__/      |________/ \______/  \______/   Intro to Rust

//Speaker: Meaghan Lewis



/*Overview

Rust is used for almost anything and everything 

Used to write low level modules for Windows that were originally written in C/C++

Statically typed.

Cargo is the build system for Rust

Create a project for a guessing game by typing "cargo new new_guessing_game" in the terminal. A directory will be created called new_guessing_game.

A cargo.toml configuration file is created in that directory.

Install the random library by typing <code>rand = "0.7.3"<\code> underneath "[dependencies]" in cargo.toml (line 9).

For more information: https://www.rust-lang.org/

*/

use std::io;//import the standard i/o library
use rand::Rng;//random number library
use std::cmp::Ordering; //compare 2 values and whether they are greater than, less than or equal to.

fn main() {
    

    //generate a random number between 1 and 10
    let number = rand::thread_rng().gen_range(1,11);

    //infinite loop
    loop{      

        println!("Guess a number b/w 1 and 10");

        //create a mutable var. By default vars are immutable in Rust
        let mut guess = String::new();

        //access the variable without copying it to memory. (Pass by reference).
        io::stdin()
            .read_line(&mut guess)
            .expect("Failed to read line");


        println!("You guessed: {}", guess);

        //convert the string guess into a 32 bit integer by first trimming the string and then parsing it into an integer.
        let guess: u32 = guess.trim().parse().expect("Please type a number.");
        //above we `shadowed` the variable guess with a new one so that we didn't have to worry about creating new variables.
        
        println!("The number is {}", number);

        match guess.cmp(&number){

            Ordering::Less => {println!("Too Low");}
            Ordering::Greater => {println!("Too high");}
            Ordering::Equal => {println!("You win!"); break;}

        }

        //We can also use standar if/else statements to compare numbers

        // if guess < number {
        //     println!("Low");
        // }


    }
    
}


//now run by typing `cargo run` in the command line


```
