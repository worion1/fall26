---

---
---
### Functions in C
Call by value: passing in a variable as arg to a function doesn't change the passed variable. e.g.
`` int x = 12
`` y = process(x)
And `x` is still 12.
You can simulate call by reference by passing in `&x` into the function. e.g.
`int x = 12`
`y = process(&x)`
And `x` is the return value of `process()`.