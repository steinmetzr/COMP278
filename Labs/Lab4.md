# Lab 4: Midterm review
The midterm for this course will be on Friday, October 18 or Monday, October 21, depending on your section. The midterm will involve solving problems of number conversion, binary arithmetic, truth table construction, conversion to Boolean expressions, simplification using Boolean algebra, and multiplexer construction. During the midterm, you will not have a calculator, but you will have the laws of Boolean algebra for reference.

In this lab, complete the following exercises borrowed from midterms in prior years.

## Number representation
Perform the following conversions. It helps to know your powers of two.

1. Convert 0o33662575655 to binary.
2. Convert 0o33662575655 to hexadecimal.
3. Convert 170 to binary.
4. Convert 170 to octal.

## Binary arithmetic
Perform the following arithmetic operations. Don't forget about two's complement!

1. Convert 0b110110110 to decimal.
2. Find the two's complement of 0b110110110. Show the place values for the two's complement number and verify that you negated it properly.
3. Add 0b10110101011 and 0b100100111.
4. Perform 0b110110-0b10011001.

## Circuit design
Given a 4 bit number A, design a circuit that outputs whether the number of bits set to 1 equals the number of bits set to 0. For example, 0010 has three bits set to 0 and one bit set to 1. Thus, for 0010, the circuit outputs 0 to show that the number of 0 bits is not equal to the number of 1 bits.

1. Draw the truth table for this circuit. Label inputs as A3, A2, A1, A0, and label the output as f.
2. Write the Boolean expression for f.
3. Simplify f using the laws of Boolean algebra.
4. Implement the circuit with a 4-1 MUX. Label input and selector lines.
