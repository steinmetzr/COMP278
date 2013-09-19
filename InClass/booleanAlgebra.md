# Boolean algebra

Law                | Form                        | Dual form
------------------ | --------------------------- | -----------
Properties of 0, 1 | 0' = 1                      | 1' = 0
Properties of 0, 1 | a * 0 = 0                   | a + 1 = 1
Properties of 0, 1 | a * 1 = 1                   | a + 0 = 0
Commutative        | a * b = b * a               | a + b = b + a
Associative        | (a * b) * c = a * (b * c)   | (a + b) + c = a + (b + c)
Distributive       | a * (b + c) = a * b + a * c | a + (b * c) = (a + b) * (a + c)
Idempotence        | a * a = a                   | a + a = a
Absorption         | a + a * b = a               | a * (a + b) = a
Complementarity    | a * a' = 0                  | a + a' = 1
DeMorgan's         | (a + b)' = a' * b'          | (a*b)' = a' + b'

# Exercises

1. Show (a * b)' * (a' + b) * (b' + b) = a'
2. Show c + (b * c)' = 1
3. Show (a + c) * (a * d + a * d') + a * c + c = a + c
4. Simplify a' * (a + b) + (b + a * a) * (a + b')