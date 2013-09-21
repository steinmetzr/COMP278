# Boolean algebra

Some of these laws of Boolean algebra are common with algebra on integers and reals (common laws are in bold), but most do not.

Law                | Form                        | Dual form
------------------ | --------------------------- | -----------
**Identity**       | a * 1 = a                   | a + 0 = a
**Commutative**    | a * b = b * a               | a + b = b + a
**Associative**    | (a * b) * c = a * (b * c)   | (a + b) + c = a + (b + c)
Identity           | a * 0 = 0                   | a + 1 = 1
Distributive       | a * (b + c) = a * b + a * c | a + (b * c) = (a + b) * (a + c)
Idempotence        | a * a = a                   | a + a = a
Absorption         | a + a * b = a               | a * (a + b) = a
Complement         | 0' = 1                      | 1' = 0
Complement         | a * a' = 0                  | a + a' = 1
Involution         | a'' = a                     |
DeMorgan's         | (a + b)' = a' * b'          | (a * b)' = a' + b'

# Exercises
In git, pull a copy of my remote repository into your local repository.

	cd COMP278
	git pull upstream master
	start .

Complete the following exercises inside of Lab3solution.txt. Use a text editor such as Notepad++ or Sublime to complete these (not Word or WordPad!).

Use the laws above to simplify expressions. Label the laws that you apply as you apply them (no more than one law per line).

1. Show (a * b)' * (a' + b) * (b' + b) = a'
2. Show c + (b * c)' = 1
3. Show (a + c) * (a * d + a * d') + a * c + c = a + c
4. Simplify a' * (a + b) + (b + a * a) * (a + b')

Complete the following exercises using Logisim. Open Lab3solution.circ in this folder.

1. Implement the majority circuit using a 4-1 multiplexer.
2. Implement a full adder (a + b + cin) using two 4-1 multiplexers (one for each output).

When you are done, save your work and do the following:

	git commit -am "Lab 3 complete."
	git push --all origin
