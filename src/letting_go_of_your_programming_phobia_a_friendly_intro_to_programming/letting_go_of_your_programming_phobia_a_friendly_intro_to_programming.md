---
marp: true
theme: rose-pine
class: invert
style: |
  * {
    font-family: 'Lilex Nerd Font Mono';
  }

  h1 {
    font-size: 45px;
    text-align: center;
  }

  h2 {
    font-size: 35px;
    text-align: center;
  }

  li {
    font-size: 24px;
    text-align: left;
  }

  .author {
    font-size: 20px;
    text-align: center;
  }
---

# LETTING GO OF YOUR PROGRAMMING PHOBIA

## A FRIENDLY INTRO TO PROGRAMMING

<div class="author">
by Bojan Milevski
</div>

---

# WHAT IS PROGRAMMING?

- Thinking
- Debugging
- Fixing
- **Learning**

---

# A FIELD THAT IS CONSTANTLY EVOLVING

- Technology never stays put
- Look at the JavaScript frontend ecosystem
  - JavaScript gets introduced
  - jQuery fixes JavaScript
  - Angular fixes jQuery
  - React fixes Angular
  - Vue, Svelte, Solid, Next.JS ...
  - WebAssembly fixes everything?

---

# ON THE OTHER HAND, NOT SO MUCH

- Systems programming is a very fragile space
- Some technologies do not need (drastic) changes
  - C
  - C++
  - Assembly

---

# WHAT MATTERS

- Programming is the same throughout
- Logic stays
  - Learn once, use everywhere
- Closely coupled with math
  - You are not required to be a **great** mathematician
- Solving problems
- Thinking of solutions

---

# THE FUN PARTS

- Learning and using new
  - Programming languages
  - Programs
  - Frameworks
  - IDEs
  - Tools

---

# OK, BUT REALLY, WHAT IS PROGRAMMING?

- Giving instructions to a computer
  - It always listens to what you tell it to do
  - Even if you make logical errors
  - It **always** obeys, unless you cross a certain line
  - Even then, it does what you tell it do to - avoid mistakes
  - How? Someone programmed it that way
- In essence, it's all 0s and 1s in the background
  - Assembly
- Typing some text that makes sense
- Compilers, interpreters

---

# WHAT YOU WILL BE STUDYING

- Structural programming
- Object-oriented programming
  - C++
- Client-side internet programming
  - JavaScript
- Advanced Programming
- Algorithms and data structures
  - Java
- Logical and functional programming
  - Prolog, Clojure
- A lot of other programming languages
  - i.e. Python
- It's not about the language, it's about science

---

# WHAT WE WILL LEARN IN THIS PRESENTATION

- We will use `C` and `python` throughout this presentation
- Turing Completeness
  - Variables
  - Types
  - Operators
  - Branching
  - Loops
  - Arrays

---

# WHAT THIS PRESENTATION IS NOT

- A full introduction to programming
  - My goal is to introduce you to the core concepts
  - Not scare you away
- Developer terms
  - Compiling
  - Interpreting
  - Debugging

---

# WHAT THIS PRESENTATION IS NOT

- "More advanced" concepts
  - Functions
  - Memory
  - Pointers
  - Structures
  - Recursion
- Details
- Build on what you already know from high school
  - Maths
  - Programming
- Ph.D. Dejan Gjorgjevikj and M.S. Stefan Andonov
  - They will take over after this presentation

---

# ONE LAST THING

- I will not ask ("difficult") questions
  - I will avoid pressuring you as much as possible
- A funny story my colleague told me yesterday
  - An intro class, like this one
  - Determining if a number is prime
  - They spent 30 mins on a minor detail
  - I will avoid this situation

---

# A BASIC PYTHON PROGRAM

```py
x = 10
print(x)
```

```
10
```

---

# THE SAME BUT IN C

```c
#include <stdio.h>

int main() {
    int x = 10;
    printf("%d\n", 10); // WEIRD, HUH?

    return 0;
}
```

```
10
```

- That sure is a lot more code for nothing...
- You are suppose to ignore most of the code when beginning to program
  - That's totally fine

---

# VARIABLES

- A variable stores a value
- That's it
- Some complications...

---

# TYPES

- In `C`, we must explicitly state the type

```c
int x = 10;
```

- Not the case in `python`

```py
x = 10
```

- `C` is more verbose, but "faster" because of this
- `python` requires us to write less code, but tries to guess what we want

---

# TYPES

- Once we declare a type in `C`, it cannot change
  - `C` is a statically typed language

```c
int x = 10;
x = "Hello"; // ERROR!
```

- `x` is an `int`, and will always be an `int`

  - `x` cannot change its type
  - It's just how `C` works

---

# TYPES

- Not the case in `python`

```py
x = 10
x = "Hello"
```

- It's just how `python` works `:)`
- `python` is a dynamically typed language

---

# TYPES

- In `C`, we can change the value, but not the type

```c
int x = 10;
x = 20;
```

- The same in `python`

```py
x = 10
x = 20
```

---

# CONSTANTS

- `C` has a keyword that prevents changing a value of a variable

```c
const int x = 10;
x = 20; // ERROR!
```

- `python` does not have a way of defining variables constant
  - Automatically guesses and makes it for you in the background

---

# SOME OTHER TYPES

```c
bool attending = true;
float pi = 3.1415; // for illustrative reasons, not accurate
double pi = 10.123456789; // for illustrative reasons, not accurate
char my_letter = 'b';
char my_name[] = "Bojan";
```

- Again, `python` implies the types to its variables

---

# COMPARISON OPERATORS

- We can compare values
  - `<` less
  - `>` greater
  - `<=` less or equal
  - `>=` greater or equal
  - `==` `is` equal
  - `!=` `is not` not equal

---

# COMPARISON OPERATORS

- In `C`

```c
int x = 10;
int y = 20;
bool greater = x > y; // false
bool less = x < y; // true
bool equal = x == y; // false
bool not_equal = x != y; // true
bool greater_or_equal = x >= y; // false
bool less_or_equal = x <= y; // true
```

---

# COMPARISON OPERATORS

- In `python`

```py
x = 10
y = 20
greater = x > y # false
less = x < y # true
equal = x == y # false
not_equal = x != y # true
greater_or_equal = x >= y # false
less_or_equal = x <= y # true
```

---

# LOGICAL OPERATORS

- We can test logic
  - `and` `&&`
  - `or` `||`
  - `not` `!`

---

# LOGICAL OPERATORS

- In `C`

```c
bool attending = true;
bool online = false;
bool is_physically_present = attending && !online; // true
bool is_preesnt_online = attending && online; // false
bool is_doing_something = attending || online; // true
```

---

# LOGICAL OPERATORS

- In `python`

```py
attending = true
online = false
is_physically_present = attending and not online; // true
is_preesnt_online = attending and online; // false
is_doing_something = attending or online; // true
```

---

# MATHEMATICAL OPERATORS

- `+` addition
- `-` subtraction
- `*` multiplication
- `/` division
- `%` modulo

- `--` `++`
- `+=` `-=` `*=` `/=` `%=`

---

# MATHEMATICAL OPERATORS

- In `C`

```c
float x = 1.5;
float y = 2.25;
float z = x + y;
printf("%d + %d = %d\n", z); // 1.5 + 2.25 = 3.75
```

- In `python`

```py
x = 'Hello, my name is '
y = 'Bojan Milevski'
z = x + y
print(z) # Hello, my name is Bojan Milevski
```

---

# COMMENTS (WHILE WE'RE AT IT)

- Comments are just notes you leave for yourself or your colleagues
- In `C`
  - `//` for single line comments
  - `/* */` for multi line comments
- In `python`
  - `#` for single line comments
  - no multi line comments in `python`

---

# COMMENTS

- There are some really funny comments on the internet!
  - [GTA V source code](https://www.youtube.com/watch?v=QZ6rLbu4LQw)
  - [Valve games source code](https://www.youtube.com/watch?v=QZ6rLbu4LQw)
  - [The Simpsons: Hit & Run source code](https://www.youtube.com/watch?v=R_b2B5tKBUM)
  - Most of these you aren't suppose to see - they're leaks of proprietary software! `:)`

---

# COMMENTS

- [Quake III's fast inverse square root](https://en.wikipedia.org/wiki/Fast_inverse_square_root)
- Cudos [John Carmack](https://en.wikipedia.org/wiki/John_Carmack)

```c
float Q_rsqrt(float number)
{
    long i;
    float x2, y;
    const float threehalfs = 1.5F;

    x2 = number * 0.5F;
    y = number;
    i = *(long*) &y;                            // evil floating point bit level hacking
    i = 0x5f3759df - (i >> 1);                  // what the fuck?
    y = *(float*) &i;
    y = y * (threehalfs - (x2 * y * y));        // 1st iteration
 // y = y * (threehalfs - (x2 * y * y));        // 2nd iteration, can be removed

    return y;
}
```

---

# BRANCHING

- Execute a statement based on a predicate

  - If - do this, if not - do this, else - do this...

- In `C`

```c
if (10 > 5) {
    printf("10 is greater than 5");
}
```

- In `python`

```py
if 10 > 5:
    print("10 is greater than 5")
```

- What if it's less or equal, or both?

---

# BRANCHING

- Let's use our previous knowledge in practice
  - Variables

---

# BRANCHING

- In `C`

```c
int x = 0;
int y = 0;

if (x > y) {
    printf("%d is greater than %d\n", x, y);
} else if (x < y) {
    printf("%d is less than %d\n", x, y);
} else {
    printf("%d is equal to %d\n", x, y);
}
```

---

# BRANCHING

- In `python`

```py
x = 0
y = 0

if x > y:
    print(x + " is greater than " + y)
elif x < y:
    print(x + " is less than " + y)
else:
    print(x + " is equal to " + y)

```

---

# BRANCHING

- We can combine logic

- In `C`

```c
int w = 10;
int x = 20;
int y = 30;
int z = 40;

if (w > x && y > z) {
    // print something
} else if (w > x || w > y) {
    // print something else
} else if ((w == x || w == y) && (z > x && z > y)) {
    // really complicated statement
}
```

---

# BRANCHING

- In `python`

```py
w = 10
x = 20
y = 30
z = 40

if w > x and y > z:
    # print something
elif w > x || w > y:
    # print something else
elif (w is x or w is y) and (z > x and z > y):
    # really complicated statement
```

---

# LOOPS

- Useful for when we want to something multiple times

```c
int i = 1;

printf("i = %d\n", i);
i++;
printf("i = %d\n", i);
i++;
printf("i = %d\n", i);
i++;
printf("i = %d\n", i);
i++;
printf("i = %d\n", i);
i++;
```

---

# LOOPS

```py
i = 1

print("i = " + i)
i += 1
print("i = " + i)
i += 1
print("i = " + i)
i += 1
print("i = " + i)
i += 1
print("i = " + i)
i += 1
```

---

# LOOPS

- In `C`

```c
int i = 1;
const int limit = 5;

while (i <= limit) {
    printf("i = %d\n", i);
    i++;
}
```

- This is cleaner and much more readable

---

# LOOPS

- In `python`

```py
i = 1
limit = 5

while i <= limit:
    print("i = " + i)
    i += 1
```

- Uses all of the things we learned

---

# LOOPS

- There is a problem...
- The code is too verbose!
- There is a shorter way of writing this

---

# LOOPS

- In `C`

```c
const int limit = 5;

for (int i = 1; i <= limit; i++) {
    printf("i = %d\n", i);
}
```

---

# LOOPS

- In `python`

```py
limit = 5

for i in range(1, limit + 1):
    print("i = " + i)
```

---

# LOOPS

- We can skip to the next iteration of the loop
  - `continue`
- In `C`

```c
const int limit = 10;

for (int i = 0; i <= limit; i++) {
    if (i % 2 == 0) {
        continue;
    }

    printf("The number %d is odd", i);
}
```

---

# LOOPS

- In `python`

```py
limit = 10

for i in range(1, limit + 1):
    if i % 2 == 0:
        continue

    print("The number " + i + " is odd")
```

---

# LOOPS

- We can exit early out of a loop
- In `C`

```c
const int limit = 1;

for (int i = 1; i <= limit; i++) {
    if (i == 5) {
        break;
    }

    printf("%d\n", i);
}
```

---

# LOOPS

- In `python`

```py
limit = 10

for i in range(1, limit + 1):
    if i is 5:
        break

    print(i)
```

---

# ARRAYS

- A single data structure that stores multiple values
- Can be of variable length
- First element is always index `0`
  - Except in `lua`

---

# ARRAYS

- In `C`

```c
const int size = 5;
int array[size] = { 1, 2, 3, 4, 5 };
int numbers[] = { 1, 2, 3 }; // size can also be inferred
```

- In `python`
  - They're called `list`s

```py
list = [ 1, 2, 3, 4, 5 ]
```

---

# ARRAYS

- We can iterate over them
- In `C`

```c
const int size = 5;
int array[size] = { 1, 2, 3, 4, 5 };

for (int i = 0; i < size; i++) {
    printf("array[%d] = i\n", i, array[i]);
}
```

- Don't forget - the first element is of index `0`

---

# ARRAYS

- In `python`

```py
list = [ 1, 2, 3, 4, 5 ]

for i in list:
    print("list[" + i + "] = " + list[i])
```

---

# SUM OF AN ARRAY

- In `C`

```c
const int size = 5;
int array[size] = { 10, 20, 30, 40, 50 };
int sum = 0;

for (int i = 0; i < size; i++) {
    sum += array[i];
}

printf("The sum is %d\n", sum);
```

---

# SUM OF AN ARRAY

- In `python`

```py
list = [ 10, 20, 30, 40, 50 ]
sum = 0

for i in list:
    sum += i

print(sum)
```

---

# EXERCISE IN C

- Transforming a string to a number

```c
#include <stdio.h>
#include <string.h>

int main() {
  const char my_number[] = "1024";
  int multiplier = 1;
  int actual_number = 0;

  for (int i = strlen(my_number) - 1; i >= 0; i--) {
    int current_number = my_number[i] - '0';
    actual_number += current_number * multiplier;
    multiplier *= 10;
  }

  printf("%d\n", actual_number);

  return 0;
}
```

---

# DIVIDE AND CONQUER

- I used the divide and conquer method to solve a problem
  - Presenting such a difficult topic
  - I split it into smaller parts
  - I explained it as beginner friendly as possible

---

# THAT'S ALL

- ...for now
- I wish you luck on your studies
- Use the divide and conquer method
- Don't forget to think

---

<div style="font-size: 120px; text-align: center; font-weight: bold;">
QUESTIONS?
</div>
