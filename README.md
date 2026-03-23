This program finds integers where multiplying by any irrational number α produces a
specific decimal pattern. It scans fractional parts of n·α — which spread uniformly across
[0,1) by Weyl's theorem — and collects indices landing in a tiny target window. The demo
uses 77·√2, finding a multiplier that reveals ".77" after the decimal point.

The code is a fail attempt trying to simplify equation in HKDSE in Core or M 2

Since the calculator approved by the gov do not support simplification of equation

The above code is try to mimic the simplification of the equation inside the calculator.

--------------------------------------------------------------------------------------------------

Consider question 2020 6a in core
<img width="974" height="305" alt="image" src="https://github.com/user-attachments/assets/c76e02a3-fab6-4b9b-a052-f4556fc61563" />


By making the equation into the calculator

It can solve by sub. x into i in complex number in calculator

----

real part = degree 0

----

imaginary part = degree 1

--------------------------------------------------------------------------------------------------

Consider question 2018 11ai in m2 past paper

<img width="974" height="318" alt="image" src="https://github.com/user-attachments/assets/220e3f61-30dc-444f-82d7-e6b6e30c2d74" />

By making the equation into the calculator

it can be use to evaluate the quadratic equation fast by

----

sub x = 0 get the degree 0 part

----

sub x = i

imaginary part = degree 1

degree 0 – real part = degree 2

--------------------------------------------------------------------------------------------------

This method can also solve questions for degree 3 and follow the same procedure with

By making the equation into the calculator

----

sub x = 0 get the degree 0 part

----

hand calculate degree 3 part

----

sub x = i

degree 3 + imaginary part = degree 1

degree 0 – real part = degree 2


## --------------------------------------------------------------------------------------------------

However when encounter with X and Y variables with degree at most 2 degree

For example 2021 Q19 cii in core
<img width="974" height="65" alt="image" src="https://github.com/user-attachments/assets/44f0b243-7023-46bf-8db1-b96c9fbf853e" />


This method lose its light

Therefore, the code provided can sub Y for example into sqrt (2)

----

sub x = 0 and y = 0 get the degree 0

----

sub x = i and y = 0

imaginary part = X part

degree 0 – real part = X^2 part

----

sub y = i and x = 0

imaginary part = Y part

degree 0 – real part = Y^2 part

----

Then sub X = i and sub Y = sqrt(2)

Imaginary part * 7979 after the decimal point = XY part

--------------------------------------------------------------------------------------------------


Failure

But later this Y part can be sub. for example 0.0001 instead of sqrt(2)

Which can reduce the chance of calculator ignoring smaller digit which is better.


