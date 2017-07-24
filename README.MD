# Compile and run (Linux)

Run the following in the terminal. (Ctrl+Alt+T)

```
g++ deriver.cpp -o deriver
./deriver
```

# Compile and run (Windows)

Run the following in CMD.

```
g++ dervier.cpp -o deriver.exe
deriver.exe
```

# Example input/output

```
x             # input (try typing it!)
f(x)  = x     # input interpretation (prints the operation tree)
f'(x) = 1     # computed derivative of the input

1/x + x*x - 3             # supports all basic operations (+, -, *, /)
f(x)  = ((1) / (x) + ((x * x) - 3))                    # operation tree
f'(x) = (((-1 * 1)) / ((x * x)) + (x + x))             # derivative

3*x^(2) + 4*x + 6     # there is a quirk that ^ must have following ()
f(x)  = ((3 * x^2) + ((4 * x) + 6))                    # operation tree
f'(x) = ((3 * (2 * x)) + 4)                            # derivative

sin(x) * cos(x)       # supports trig functions sin(x) and cos(x)
f(x)  = (sin(x) * cos(x))                              # operation tree
f'(x) = ((cos(x) * cos(x)) + (sin(x) * (-1 * sin(x)))) # derivative

exp(3 * cos(x))         # also supports exp(x) and composite functions
f(x)  = e^((3 * cos(x)))                               # operation tree
f'(x) = ((3 * (-1 * sin(x))) * e^((3 * cos(x))))       # derivative

log(x)                 # also supports log(x), the natural logarithm
f(x)  = log(x)                                         # operation tree
f'(x) = (1) / (x)                                      # derivative
```

# How it works

1. A line of user input is captured as a string of characters.

2. String is broken into an array of tokens, atomic elements with
meaning. For example "x" is a token that represents the variable,
"123" is a token that represents a number and "+", "-", "*", "/"
are tokens that represent arithmetic operators.

3. Tokens are structured in an operation tree, taking into account
precedence of operators, parethesis, function arguments. This is
the full semantic representation of the user input.

4. The derivative is calculated recursively by calling the derivative
function in the root node of the operation tree. The derivative
of each primitive function - sin, cos, exp and log - and rules of
derivation - multiplication rule, division rule - are coded into
the program and recursion takes care of the rest.
