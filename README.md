# alien-snippets
Programming exercises for Python based on documentation of new programming languages.

The key idea for this repo is that newer programming languages provide us with useful code examples in their documentation.
Using these examples might give some fresh air, authority and intrigue to an introductory Python class or a self-study session.
You can ask your students: 

> Can you make this work in Python? People made a whole new programming language to make this work!

## Languages considered

Anything rather new, less mainstream and possible for a human to read qualifies, examples:

- Zig
- vlang
- Vale
- Pony
- Crystal
- Julia
- D
- Odin

Personal preferences: really like v’s one-page documentation, fond of parts of Julia (but it is kind of mainstream lang now), and cannot remember that one programming language that had hello world in different human languages at their front page - it would make a great example to replicate.

## Exercises

Can you do the examples below in Python? Steps involved: 

- go over the code in an alien programming language
- make up your mind what this code does
- match to familiar concepts
- come up with implementation in Python.

Of course you can make a ChatGPT prompt for this – but only when you are totally stuck and can settle for clues, not a ready solution.

### Maps from ballerina 

<details><summary>Hint</summary>
... are dictionaries in Python!
</details>


```ballerina
import ballerina/io;

public function main() {
    // Creates a `map` constrained by the `int` type.
    map<int> ages = {
        "Tom": 23,
        "Jack": 34
    };

    // Gets the entry for `Tom`.
    int? v = ages["Tom"];
    io:println(v);

    // As there exists an entry for `Tom`, it can be accessed using the `map:get()` method. 
    // Using `ages["Tom"]` wouldn't work here because its type would be `int?` and  not `int`.
    int age = ages.get("Tom");
    io:println(age);
```

### [Gleam](https://tour.gleam.run/functions/labelled-arguments/) allows keyword arguments

<details><summary>Refactoring idea</summary>
Does the order of arguments in the orginal Gleam function seem natural to you? 
</details>

```gleam
import gleam/io

pub fn main() {
  // Without using labels
  io.debug(calculate(1, 2, 3))

  // Using the labels
  io.debug(calculate(1, add: 2, multiply: 3))

  // Using the labels in a different order
  io.debug(calculate(1, multiply: 3, add: 2))
}

fn calculate(value: Int, add addend: Int, multiply multiplier: Int) {
  value * multiplier + addend
}
```

### Case switch in [Nim](https://nim-lang.org/)

<details><summary>Precaution</summary>
Only a part of this code can be translated to Python `match`/`case`.
</details>

```nim
# Case switch.
var letter = 'c'

case letter
of 'a':
  echo "letter is 'a'"
of 'b', 'c':
  echo "letter is 'b' or 'c'"
of 'd'..'h':
  echo "letter is between 'd' and 'h'"
else:
  echo "letter is another character"
```

### What century is it now? 

Example from excellent [v docs](https://github.com/vlang/v/blob/master/doc/docs.md#module-import-aliasing).

<details><summary>Extra question</summary>
What is the significance of `0.009999794661191` constant?
</details>

```vlang
import time
import math

type MyTime = time.Time

fn (mut t MyTime) century() int {
	return int(1.0 + math.trunc(f64(t.year) * 0.009999794661191))
}

fn main() {
	mut my_time := MyTime{
		year: 2020
		month: 12
		day: 25
	}
	println(time.new(my_time).utc_string())
	println('Century: ${my_time.century()}')
}
```

### [Vale](https://vale.dev/): print a list of planets

Probably the easiest task on the list.

<details><summary>Extension idea</summary>
Consider adding "Hello, Venusians!" and varieties for Earth and Mars to your print statement. 
/details>


```vale
import stdlib.*;

exported func main() {
 planets = [#]("Venus", "Earth", "Mars");
 foreach planet in planets {
   println("Hello " + planet + "!");
 }
}
```

## Notes

- Code examples are abundant at [Rosetta Code][rc], but I find the new programming language docs specifically to be a place where a lot of effort, knowledge and attention focus is concentrated, thus making them a good resource to draw from.
- A great cross-language reference for mainstream and older programming langauges is [hyperpolyglot](https://hyperpolyglot.org/).
- If I'm to provide some basis for comparing languages I'd use [this Reddit comment of mine] that got surprisingly popular. Would probably need more account for  programming paradigms though.

[rc]: https://rosettacode.org/wiki/Rosetta_Code
[rc2]: https://www.reddit.com/r/learnprogramming/comments/1cgl7df/comment/l1wpykk/
