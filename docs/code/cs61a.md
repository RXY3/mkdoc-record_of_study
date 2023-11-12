# LEC 7
## Abstraction
> Abstraction is the idea of hiding the details of how something works and only showing the user the functionality they need.
>

## Recursion
> Recursion is a method of solving problems that involves breaking a problem down into smaller and smaller subproblems until you get to a small enough problem that it can be solved trivially.
Example: Factorial
```python
def factorial(n):
    """Return the factorial of N, a positive integer."""
    if n == 1:
        return 1
    else:
        return n * factorial(n - 1)
```
TODO
