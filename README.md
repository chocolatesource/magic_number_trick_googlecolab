## **What does this programe do**
this programe find an integer that multiply specific irrational number into indicated number appear after the decimal point.<br>
For example, ml2(math.sqrt(2), 10**6, 5, 1001) will find a list of integer for example 7979 that are able to multiply to sqrt(2) and output the indicated number after decimal point .01001~~~

7979 * sqrt(2) = 11284.**01001**42


---

## **Purpose of this programe**
This is to solve algebraic simplification in calculator in hong kong university entrance exam (HKDSE)<br>
and mimic the method of x = 0.01

for example, when solving the following equation<br>
<img width="460" height="345" alt="v4-460px-Factor-Second-Degree-Polynomials-(Quadratic-Equations)-Step-3-Version-3" src="https://github.com/user-attachments/assets/d94980f7-7740-42e3-92fd-06ae66e21b1c" /> <br>

by substituting x = 0.01 and typing (2x+3)(3x+2) we get the output of 6.1306 in calculator<br>
which is the same answer in simplification by reading from the right to the left:<br>
degree 2 is 6<br>
degree 1 is 13<br>
constant part is 6

---

## **Evaulation**
The first purpose of the programe is fail attempt to mimic substituting x = 0.01 as the following<br>
1. The result get too big(the number before decimal point) causes the calculator do not calculate the number after the decimal point
2. The result is more complicated than substituting x = 0.01 when solving degree 2 polynomial, the above example, need to substitute 2 time (one x = sqrt(2) for example, and must sub x = 0 to get constant part for subtraction of the degree 2 part)

---

## **Another purpose**
Another purpose of the progamee are able to more easy<br>
to memorize result with specific scope of function

for example to memorize cos(pi//n) for n = 5, 6, 8, 10, 12<br>
we are able to extract the number by multiply 16 * (cos(pi//n) ^2) * 107<br>
write down first integer of the after decimal point<br>
sqrt root the above integer<br>
then the multiply 16 * (cos(pi//n) ^2) include either 1 or 2 or 4 times the integer.<br>
for example 16 * cos(pi//12) ^2 = 8+4sqrt(3)<br>
16 * (cos(pi//n) ^2) * 107 = 1597.32<br>
Then by dividing n // 3, that is 12//3 = 4<br>
we know that the result 16 * cos(pi//12) ^2 is consist of 4sqrt(3)<br>
which we know cos(pi//12) by subtrating the respective value
