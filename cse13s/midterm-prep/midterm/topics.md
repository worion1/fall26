	### Pass-by-Value vs. Pass-by-Reference
Pass by value is the convention used in C which dictates that passing a variable as an argument to a function creates a completely isolated copy for the function to use, modify, etc. For example:
```C
int add_ten_to_num(int x) {
	x = x + 10;
	return x;
}

int main(void) {
	int x = 0;
	add_ten_to_num(x);
	printf("The value of x is: %d\n", x); // the value 0 will be printed
	
	return 0;
}
```
In this case, the value of `x` in main is never updated by the function call because the passed in argument is not the same variable that is used when `x = x + 10` is executed. Once `add_ten_to_num()` returns, its entire stack frame is popped and that memory is free to be used by another function, including the memory allocated for its local variable `x`.

Pass by reference, on the other hand, says that a variable passed to a function is the same variable (same memory address) used by the function. In other words, pass by reference allows functions to directly modify variables in their function body, or allow the callee to modify a variable "in place" by simply passing it to a function by reference. We can simulate this behavior in C by giving a function access to the memory address of our variable. Now the function knows where the variables lives, so it can go to its address (via the dereference operator) and modify its value directly. For example:
```C
void add_ten_to_num_in_place(int *x) {
	*x = *x + 10; // go to the address of x and add 10 to its value
	return;
}

int main(void) {
	int x = 0;
	add_ten_to_num_in_place(&x); // &x returns the memory address of x
	printf("The value of x is: %d\n", x); // the value 10 will be printed
	
	return 0;
}
```
---
### Pointer Arithmetic
```C
int a = 100;
int *p = &a;

// Ex1:
p++; // equivalent to p = p + 1; p = p + 1 * (sizeof(*p)).
	 // *p points to a varaible of type int (4 bytes), so we increment 
	 // where p is pointing to by 4 bytes.
	 
// Ex2:
(*p)++; // this goes to the address that p is pointing at (via
		// the * dereference operator), which is a, and then 
		// increments the values of a by 1, resulting in a=101.
```
___
### Graphs




---
### MCQ Answers
