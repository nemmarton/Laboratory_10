# Laboratory_10

Tasks:

->Arithmetic sequence

->Fibonacci

->Printing text

->Array forwards and backwards

->Numeral system

->Pretty print numbers

# Memo: Recursion
---

## 1. What is Recursion?

- **Recursion**: when a function calls itself (directly or indirectly).
- Every recursive function needs:
  1. **Base case** → the condition where recursion stops.
  2. **Recursive step** → the part where the function calls itself with a smaller/simpler input.
It is a bit similar to loops...

Example:
```c
int factorial(int n) {
    if (n == 0) return 1;       // base case
    return n * factorial(n-1); // recursive step
}```

2. How Recursive Calls Work

When a function is called:

    The program stores the function’s parameters, local variables, and return address on the call stack.

    Each recursive call creates a new stack frame.

    When the function returns, its frame is removed from the stack.

You can imagine that as a tower of building blocks. The connection between them is the parameter and the reutrn value (the glue).

The fucntion always work in its own block (sandpit if you like:)

Example (factorial of 3)

Call sequence:
```c
factorial(3)
 → factorial(2)
   → factorial(1)
     → factorial(0) //stop condition reached, so that one start to return (remove itself from the tower)

Return sequence:

factorial(0) returns 1
factorial(1) returns 1 * 1 = 1
factorial(2) returns 2 * 1 = 2
factorial(3) returns 3 * 2 = 6
```
3. The Call Stack

    The call stack is a memory area that keeps track of active function calls.

    Each call gets a stack frame:

        Parameters

        Local variables

        Return address


4. Tail Recursion

    Tail recursion: recursive call is the last operation in the function.

    Some compilers can optimize tail recursion to avoid creating new stack frames.

Example:
```c
int factorial_tail(int n, int acc) {
    if (n == 0) return acc;
    return factorial_tail(n-1, n*acc);  // tail recursive
}
```
5. Common Pitfalls

    Missing base case → infinite recursion, stack overflow.

    Too deep recursion → stack overflow (e.g., very large input). There are programming languages that has a limited recursion depth. In C you just experience slow run or apparently frozen behavior.

    Inefficient recursion → repeated work (e.g., naive Fibonacci).

6. When to Use Recursion

    Problems that can be broken down into smaller, similar subproblems:

        Factorials, Fibonacci numbers.

        Tree traversal. //later

        Divide-and-conquer algorithms (quicksort, mergesort). 

Reminder:
Recursion is powerful but must be used with care. Always ensure:

    A clear base case.

    Progress towards the base case.

    Awareness of the call stack and its limitations.

