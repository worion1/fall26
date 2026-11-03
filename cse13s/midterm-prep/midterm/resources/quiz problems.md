#### p3
`int orbs = 15;`  
`int wizards = 29;`

`// two wizards can ponder one orb`  
`if ( (wizards != 0) && ((orbs * 1.0) / wizards) >= 0.5) {`  
  `printf("we have enough orbs, the wizards can share\n");`  
`}` 
Why does it matter that this code does short-circuiting?

- it's more efficient this way -- we're avoiding running the code inside the if block
- otherwise, if there were 0 wizards, then we would have a divide by 0
- having short-circuiting lets us improve performance through better branch prediction
- it lets us parallelize the code on the GPU
---
#### p4
What's this code do?
`#include <stdio.h>`

`void swap(int x, int y) {`  
  `int tmp = x;`  
  `x = y;`  
  `y = tmp;`  
`}`

`int main(void) {`  
  `int alan = 14;`  
  `int beth = 97;`

  `swap(alan, beth);`

  `printf("alan: %d, beth: %d\n", alan, beth);`

  `return 0;`  
`}`

- alan is now 14, beth is now 97
- alan is now 97, beth is now 14
- we've taken the average -- they are both now 55.5
- what??
---
#### p5
How many distinct floating point numbers are there, for the C type `float` ?

- 4294967296 or so
- uncountably infinitely many
- countably infinitely many
- what??
---
#### p6
Where might we find the _implementation/definition_ of cos, if we want to do some trigonometry?

- math.h
- /usr/lib/x86_64-linux-gnu/libm-2.39.a
- somewhere else
- what??
---
#### p7
Take a look at this Makefile here...

`all: send_emails`

`send_emails: send_emails_main.o email.o network.o`

        `clang send_emails_main.o email.o network.o -o send_emails`

`send_emails_main.o: send_emails_main.c email.h`

        `clang -c send_emails_main.c`

`email.o: email.c email.h network.h`

        `clang -c email.c`

`network.o: network.c network.h`

        `clang -c network.c`

Imagine we have already built everything.

Now, we change network.c and run "make" -- how many things will be rebuilt with clang when we run make?

- network.o, email.o and send_emails (in that order)
- just the final binary, send_emails
- everything in the whole program
- just network.o and the final binary (in that order)
- what??
---
#### p8
Here's some code!

`int main(void) {`

  `int a = 100;`  
  `int *p = NULL;`  
  `p = &a;`  
  `printf("here's a value: %d\n",  a);`  
  `p++;`  
  `printf("here's a value now: %d\n", a);`  
  `return 0;`

`}`

what does it do?
- prints 100 and then prints 100 again
- prints 100 and then crashes
- prints 100 and then prints 101
- what??
---
#### p9
Here is some code!

`int *allocate_a_number(int val) {`  
  `int output;`  
  `output = val;`

  `return &output;`  
`}`

`int main(void) {`  
  `int *space;`  
  `space = allocate_a_number(27);`  
  `*space = 100;`

  `return 0;`  
`}`

What's going on here?

- we just made some space where we can store an integer. This will work.
- you've made a terrible mistake, please do not do that
- what??
---
#### p10
Here's a data structure definition for you:

`typedef struct linkedlist_int {`  
  `int value;`  
  `struct linkedlist_int next;`  
`} linkedlist_int;`

What do you think about this?

- looks good to me, ship it
- inefficient -- we could make it go faster if we make sure it's on the stack
- this actually won't compile
- you don't have to name the struct if you're doing a typedef anyway
---
#### p11
What's the difference between The Stack (the call stack) and a stack?

- The Stack is a specific stack, the one on which your program runs its functions
- C programs don't have a call stack; that's a feature added by Java
- The Stack is actually not a stack as such -- it's a misnomer
- what??
---
#### p12
Take a look at this code:

`int x = 12;`

`int *p;`

`p = &x;`

`(*p)++;`

What's going on here?

- x is now 13
- can't do this -- program will crash
- p is now greater by 1
- p is now greater by 4
---
#### p14
If we write a recursive function and find that it's slow, but then we speed it up using *memoization*, what changed to make it go faster?

- Memoization lets us avoid doing work multiple times.
- The compiler rewrote the program with a loop, so it goes fast.
- what??
- It's reusing stack frames -- allocating stack frames was what made the program slow.
---
#### p16 FRQ
What do we need to know about and/or keep track of while we're doing breadth-first search?

---
 