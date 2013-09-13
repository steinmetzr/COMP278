# Lab 2: Logic representations

## Background

Read chapter 2 of the [Science of Computing](http://lawrancej.github.io/COMP278/Resources/ScienceOfComputing.pdf).

## Overview: There's more than one way to do it

In this lab, we will learn how to convert among truth tables, logic expressions, Venn diagrams, logic circuits, function tables and MUX configurations.

![Representations of NAND](http://lawrancej.github.io/COMP278/Images/logic-representations.svg)

## Boolean constants
Remember: 0 is false, and 1 is true. Never mix these up.

## Truth tables

A **truth table** is a unique, tabular representation of a Boolean logic function. All cells in a truth table consist of the values $0$ or $1$ (except for column labels).

A truth table consists of four quadrants:

Boolean variables    | Logic expression on variables
-------------------- | ---------------------------------
Variable assignments | Evaluate expression for each row

To build a truth table, build up each quadrant from left to right, top to bottom. Label variables in the top left quadrant, then write out the expression in the top right quadrant. To generate all possible variable assignments, treat columns (variables) as digits in a binary number. Count in binary from zero to 2^n - 1, where n is the number of Boolean variables in the top left quadrant. To fill the bottom right quadrant, we can treat the variable assigments as the inputs to the logic expression listed in the upper right quadrant.

Suppose a and b are Boolean variables, and a * b is a function of these variables. This is the truth table.

a   | b   | a * b
--- | --- | -----
0   | 0   | 0
0   | 1   | 0
1   | 0   | 0
1   | 1   | 1

Complete this truth table.

a   | b   | If a is true, then b; if a is false, then a.
--- | --- | --------------------------------------------
0   | 0   | 
0   | 1   | 
1   | 0   | 
1   | 1   |

English is cumbersome, which is why we use compact and unambiguous logic expressions.

## Logic expressions

A *logic expression* is a symbolic representaton of functions on Boolean variables. Logic expressions consist of: Boolean variables (e.g., a,b,c,x,y,z), constants (e.g., 0,1), parenthesized expressions or operations on expressions.

You have seen logic expressions in C++ already.

    // Boolean variables and constants
    bool a = true;
    bool b = false;
    // Logic expression
    bool f = !a && b || a && !b;

Logic expression notation in electronics differs from C++.

Operation | C++         | Electronics    | Meaning
--------- | ----------- | -------------- | --------------------------------
Buffer    | `a`         | a              | **Identity**: just a
AND       | `a && b`    | a * b          | **Conjunction**: Are both a and b true?
OR        | `a || b`    | a + b          | **Disjunction**: Are either a or b (or both) true?
XOR       | `a ^ b`     | (a &oplus; b)  | **Exclusive or**: Is a not equal to b?
NOT       | `!a`        | a'             | Invert a (flip the bit)
NAND      | `!(a && b)` | (a * b)'       | Either a or b (or both) are false
NOR       | `!(a || b)` | (a + b)'       | Are both a and b false?
XNOR      | `!(a ^ b)`  | (a &oplus; b)' | **Equality** Is a equal to b?

The truth tables for these expressions are below.

a   | b   | a   | a * b | a + b | a &oplus; b
--- | --- | --- | ----- | ----- | ----------- 
0   | 0   | 0   | 0     | 0     | 0
0   | 1   | 0   | 0     | 1     | 1
1   | 0   | 1   | 0     | 1     | 1
1   | 1   | 1   | 1     | 1     | 0

a   | b   | a'  | (a * b)' | (a + b)' | (a &oplus; b)'
--- | --- | --- | -------- | -------- | ----------- 
0   | 0   | 1   | 1        | 1        | 1
0   | 1   | 1   | 1        | 0        | 0
1   | 0   | 0   | 1        | 0        | 0
1   | 1   | 0   | 0        | 0        | 1

Logic expressions borrow notation from algebra. We intentionally write out AND as a * b, since AND corresponds to multiplication on single bits. Interestingly, this does not apply for OR: 0 + 1 = 1, but 1 + 1 = 2, not 1, which is why we read a + b as "a OR b", not "a plus b".  Buffer may seem pointless, but it can serve a purpose in designing circuits.

Logic operators also borrow order of operations from algebra.Remember PEMDAS? In logic, it's PNAO. 

Mnemonic  | Operation             | Remarks
--------- | --------------------- | ---------------------------
Please    | Parenthesis           | Group operations
Note      | NOT                   | NOT is like a negative sign
And       | AND, NAND             | AND is 1-bit multiplication
Order     | OR, NOR, XOR, XNOR    | OR is almost addition

In logic expression a+b*c', we have three operations, and we evaluate NOT c first, then AND that with b, and finally OR with a. 

## Venn Diagrams

Each row in a truth table corresponds to an area in a Venn diagram.

![Venn diagram, truth table, and logic expressions](http://lawrancej.github.io/COMP278/Images/venn-diagram.svg)

We can represent logic operations with Venn diagrams. Compare Venn diagrams between the left and right sides. What do you notice? Union and intersection are set operations: what logic operations do these correspond to?

![Compare Venn diagrams between the left and right sides.](http://lawrancej.github.io/COMP278/Images/venn-diagram-operations.svg)

## Logic gates

Logic gates correspond to logic operations. In each gate, inputs are to the left and outputs are to the right. Compare gates on the left and right sides. Bubbles (circles) mean NOT (invert).

![Logic gates](http://lawrancej.github.io/COMP278/Images/gates.svg)

To convert a logic expression to a circuit diagram.

1. List all variables vertically on the left hand side.
2. Evaluate the next operation in the expression by order of operations.
3. Place the corresponding logic gate to the right.
4. Wire the inputs to relevant subexpressions.
5. Label the output with the corresponding subexpression.
6. Repeat steps 2-5 until done evaluating the expression.

## Expression to circuit diagram
In Logisim, draw this expression as a circuit: x+y*z'

* This is **Right**:
 ![What you should see](http://lawrancej.github.io/COMP278/Images/logicly-diagram-right.png)
* This is **Wrong**:
 ![What you shouldn't see](http://lawrancej.github.io/COMP278/Images/logicly-diagram-wrong.png)

## Function tables
A **function table** is like a truth table; however, cells in the lower right quadrant can be logic expressions.

For example, here's the truth table for a &oplus; b:

a   | b   | a &oplus; b
--- | --- | -----------
0   | 0   | 0
0   | 1   | 1
1   | 0   | 1
1   | 1   | 0

We can condense this down to this function table, by freeing variable b:

a   | a &oplus; b
--- | -----------
0   | b
1   | b'

Study this function table carefully in relation to the truth table above. We shrank down a truth table without losing information by noticing that a &oplus; b is the same as b if a is false, and a &oplus; b is the inverse of b if a is true.

## Exercises
Complete the following exercises inside of Lab2solution.txt

1. Convert 1590 to binary.
2. Convert 0b101110110 to decimal.
3. Convert convert 0b1100 0000 0001 1010 0001 0101 1011 1010 1101 to hexadecimal.
4. Convert 0b100 001 101 101 to octal and to decimal.
5. Convert 0xBADF00D to binary and then to decimal.
6. Convert 6157 to binary and then to decimal.
7. Write the truth table for the majority circuit. Assume it takes 3 inputs, a, b, c, and produces a decision about whether most of those bits are on.
8. Convert the truth table into a logic expression.
9. What is the truth table for adding two bits together? Convert to a logic expression.
10. What is the truth table for adding two bits together with a carry bit? Convert to a logic expression.


Complete the following exercises inside of Lab2solution.circ:

1. Draw the majority circuit. Label each subexpression.
2. Draw the the adder circuit and label each subexpression.