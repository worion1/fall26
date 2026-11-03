# CSE 13s, Some Time In The Past -- Midterm Exam

**HOWTO do this midterm** -- this is a take-home exam, to be done by just you,
with your notes, with the reading materials, and with your ability to read man
pages and search the web. Do not consult with other students, and do not ask
people other than the course staff for help!

The exam is due in 24 hours (+ accommodations), and turned in the same way
that we turn in homeworks. You must check in your materials into your
course git repository *and* upload the relevant commit ID on Canvas by then.
For most students, this is due at *A Time In The Past*. 

So make sure you check in *at least* these files into a directory called
`midterm` in your git repository:
  * your completed `honesty.md` (sign that you're doing this solo; use your name)
  * your completed `answers.txt` (answers to the multiple choice questions)
  * your completed `one.c`
  * your completed `two.c`
  * your completed `three.c`
  * your completed `four.c`
  * the provided `midterm.h` (you won't have to change this)
  * your `Makefile` for compiling the code (you won't have to change this)

For the multiple choice questions, put the corresponding letter for each
problem. For the programming problems, *your code will be checked
automatically*, so make sure to put your code in the correct file (ie, `one.c`,
`two.c`, and so on).


# multiple choice questions: 10 points

Please use the provided answer file, and check it in to your `midterm`
directory.
You can make sure that your `answers.txt` will be parsed correctly by running
the following command, if you copy `check_multiple_choice.py` into your
directory:

```
$ python3 check_multiple_choice.py
```

Note that if your `answers.txt` does not parse correctly with the provided
`check_multiple_choice.py`, you won't get credit for your multiple choice
answers, so make sure the formatting is right!

1. **What's the difference between malloc and calloc?**
  - A: malloc takes two arguments, whereas calloc takes just one
  - B: calloc goes faster than malloc
  - C: calloc gives you memory on the stack, whereas malloc gives you memory on the heap
  - D: calloc ensures that the memory you get is initialized to zero
2. **What happens if you take the address of a pointer variable with the `&` operator?**
  - A: You're emulating pass-by-value.
  - B: It's already a memory address, so you get the same address again.
  - C: Your program is likely to crash, since you're referencing memory that was allocated in a stack frame for a function that has already returned.
  - D: You get the memory address of that pointer variable; it has a memory address too.
3. **How would you go about writing a function `size_t array_length(int[] numbers)` , to determine the size of a dynamically-allocated array of ints?**
  - A: You can use sizeof() to find the size of an array.
  - B: Start at the beginning of the array and walk through the elements until you find a null element.
  - C: You can't do that, since C passes arrays as pointers to the initial element of the array.
  - D: Every pointer carries the size of the array that it points to, so you can just return `numbers->size`.
4. **Which of the following are good reasons to take the address of a variable on the stack?**
  - A: You can do this to allow other functions to change those variables, emulating pass-by-reference.
  - B: This is helpful if you need to migrate a variable from the stack to the heap.
  - C: It's never a good idea; this will result in a segmentation fault.
  - D: You can do this to use those variables after their function has returned.
5. **Say you have a pointer  int\* p = &a , and that int a is at address 0x1000.  What's the value of p+2 ?**
  - A: you shouldn't compute that -- that's asking for a segmentation fault
  - B: 0x1010 , since ints are 8 bytes on a 64-bit computer
  - C: 0x1002
  - D: depends on the size of an int on your system
6. **If you have a variable of type `int *` and you cast it to `int`, what happens?**
  - A: The type system will consider the expression as an `int`.
  - B: You'll get an overflow error, since memory addresses are very large.
  - C: You can't do that in C; that is a type error and the compiler will complain.
  - D: You get the value at that memory location (whatever the `int *` was pointing at), which is an `int`.
7. **In C, what's a void pointer?**
  - A: A pointer to nothing -- it has a value of 0.
  - B: A pointer to a function that does not return a value.
  - C: An uninitialized pointer, likely pointing off into the void.
  - D: A pointer with no defined type -- it just contains a raw memory address.
8. **If we write a recursive function and find that it's slow, but then we speed
   it up using memoization, what changed to make it go faster?**
  - A: The compiler rewrote the program with a loop, so it's now roughly as fast as using iteration.
  - B: It's avoiding doing redundant work multiple times by remembering intermediate results.
  - C: We were doing two recursive calls before, which caused an exponential slowdown -- now we're only doing one recursive call.
  - D: It is reusing stack frames, since allocating stack frames was what made the program go slow.
9. **Which of these things can you not have as a field in a struct?**
  - A: A pointer to memory on the stack.
  - B: A floating point number, since floating point math is notoriously inexact.
  - C: A field that is a struct of the same type as the struct itself.
  - D: A function pointer.
10. **Which of the following are true about numbers on your computer?**
  - A: There are a finite number of floating point numbers that we could represent with type `float`.
  - B: We can use the type `int` to represent any mathematical integer number.
  - C: There are about 65,536 different numbers possible in type `int` on most computers these days.
  - D: We can use the type `float` to represent any number on the real number line.

# programming problems: 20 points
Each of these problems is worth 5 points. They are to be implemented in their
own separate C files, and some tests are given in the corresponding test C
files. They'll be graded with different (but similar) automatic tests.

You don't have to check in the test files, but you can if you want to. Feel free
to change the tests -- but make sure you pass the ones that are given! Also,
don't worry about memory leaks right now.

It is OK, and encouraged, to add helper functions as you need them, and feel
free to reference code that you wrote from your homeworks, or that we wrote
together in the in-class demos.

## one

Write a function `int num_with_highest_square(int a, int b, int c)` that, given
three input numbers a, b and c, returns the number out of those three that has
the highest square.

For example, if you were given `a=-17`, `b=5`, and `c=0`, then you ought to
return `-17`.

If there is a tie for the highest square, return any of the tied input numbers,
and that's OK.

See `one_test.c` for examples of how this might be called.

## two

Write a function `double *exponents(int start, int end, double power)`
that takes three parameters, `start`, `end`, and `power`, and returns
a dynamically allocated array (created with `malloc` or similar) that starts
counting at `start`, and goes up to `end` (inclusive), and each element of the
array is the corresponding number, raised to the specified power.

For example, if you were given `start=5`, `end=10`, and `power=2`, then the
output array should contain the numbers [25.0, 36.0, 49.0, 64.0, 81.0, 100.0].

You are guaranteed that start <= end, but they might be equal, in which case you
should allocate an array of length 1.

As a hint, you are allowed to use `math.h`, which you might want to include in
your `two.c`, and you probably want to use the function `pow` which is in
`math.h`. (see `man 3 pow` for instructions on how to use it) Also, the tests
for `two.c` are linked with the `-lm` flag, which will make this work.

See `two_test.c` for examples of how this might be called.

## three

Recall in homework 3, we wrote a function `reduce`, which took a collection of
numbers and reduced it down to a single number, essentially a summary of that
collection.

Here we will write a version of the companion function to *reduce*, which is
called [*map*](https://en.wikipedia.org/wiki/Map_(higher-order_function)). Map
takes a function and applies that function to each element in the collection,
and returns a collection of the same shape.

In this version, we will take in a linked list of floating point numbers (see
`ll_float` in the code) and return a *new* linked list of floating point
numbers, of the same length, where each element of the new list is the result of
calling the specified function on the corresponding number in the input list.

For example, if your input list consisted of:
`[0, 1, 2, 3]`

And your specified function computed the square of the input number, then your
function would return a new linked list (you'll have to allocate each entry in
the list with `malloc` or `calloc` !) containing:
`[0, 1, 4, 9]`

See `three_test.c` for examples of how this might be called.

## four
A common concern about the English language, brought up by both native speakers
and second-language learners, is that spellings seem arbitrary and difficult to
remember.  In order to fix this, we'll propose that all words will now be
spelled in alphabetical order. The same letters that they had before will be
maintained, but each word will now be rearranged to be spelled in alphabetical
order.

Write the function `char* alphabetize_word(char *word)`, which will return a new
string that is the new alphabetized version of our input word. Don't change the
input word -- allocate a new string to return, say with malloc or strdup.

For example, for the input `"apple"`, your function should allocate and return
the string `"aelpp"`. For the input `"hypothetically"`, your function should
output `"acehhillopttyy"`.

This function only needs to work on strings containing lowercase English
letters, but if you handle other characters, that is fine.  You can just use `<`
to compare characters, and decide which ones ought to go before which other one.
Also recall that we did sorting in class, and feel free to adapt the functions
from our sorting demos (we haven't done these yet but we will soon)
for use with your code, but note that you'll have to do some adapting to work on
`char`s rather than `int`s.

See `four_test.c` for examples of how this might be called.

----

# finally

Thanks a bunch! You got this. Thanks for showing up and being interested and
asking good questions in class. Alex et al will be around on the discord to give
*clarifications*, but not hints.
