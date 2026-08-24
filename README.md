## **What does this program do**
This program finds an integer that, when multiplied by a specific irrational number, produces a chosen digit pattern right after the decimal point.<br>
For example, `ml2(math.sqrt(2), 10**6, 5, 1001)` finds a list of integers — for example `7979` — that, when multiplied by `sqrt(2)`, produce the decimal pattern `.01001...`

```
7979 * sqrt(2) = 11284.010014...
```

The digits right after the decimal point are `01001`, matching the target pattern.

---

## **Purpose of this program**
This is meant to help with algebraic simplification on a calculator for the Hong Kong Diploma of Secondary Education (HKDSE) exam, mimicking the well-known "substitute x = 0.01" trick.

For example, when expanding the following expression:<br>
<img width="460" height="345" alt="v4-460px-Factor-Second-Degree-Polynomials-(Quadratic-Equations)-Step-3-Version-3" src="https://github.com/user-attachments/assets/d94980f7-7740-42e3-92fd-06ae66e21b1c" /> <br>

substituting `x = 0.01` and typing `(2x+3)(3x+2)` into a calculator gives `6.1306`, which is the same as the expanded answer read off in groups of digits from right to left:
- degree-2 coefficient: 6
- degree-1 coefficient: 13
- constant term: 6

**A more difficult example** is a two-variable expression like this one, which needs to satisfy a discriminant condition (`= 0`):<br>
<img width="849" height="57" alt="Screenshot 2026-03-23 154257" src="https://github.com/user-attachments/assets/ef938f14-b5d1-4656-af61-0b7030be367e" /><br>

Expanded fully, this comes out to `576r² + 5184rk - 20736k² = 0`, i.e. `576(r - 3k)(r + 12k) = 0` — but getting there by hand involves a lot of cross terms. The single-variable `x = 0.01` trick isn't enough here because there are two variables (`r` and `k`) and terms that mix them (`rk`), so one substitution can't separate every coefficient. Instead, substitute `r = i` (the imaginary unit) and `k = 0.001` together:

```
E(i, 0.001) = -576.020736 + 5.184i
```

- The real part's integer portion, `-576`, comes from `r²` (since `i² = -1`) → the `r²` coefficient is `576`.
- The real part's decimal tail, `-0.020736`, comes from `k²` at the `10⁻⁶` scale (since `k = 0.001` → `k² = 0.000001`) → `-0.020736 × 10⁶ = -20736`, the `k²` coefficient.
- The imaginary part, `5.184`, comes from the `rk` term (since `r·k = i·k`) → `5.184 / 0.001 = 5184`, the `rk` coefficient.

A follow-up substitution with `k = 0` alone confirms this — `E(i, 0) = -576`, isolating just the `r²` term and showing the `r`, `k`, and constant terms all cancel out entirely, so nothing else needs to be accounted for.

---

## **Evaluation**
The first attempt to mimic substituting `x = 0.01` for this kind of problem runs into two issues:
1. The result before the decimal point gets too large, so the calculator runs out of display precision to show the digits after the decimal point.
2. It's more complicated than the single-variable `x = 0.01` trick — solving a degree-2 polynomial this way needs two substitutions (e.g. one with `x = sqrt(2)`, and a separate one with `x = 0` to isolate the constant term for subtraction).

---

## **Another purpose**
Another use for this program is to make it easier to memorize `cos(π/n)` for `n = 5, 6, 8, 10, 12`.

The idea: extract a number by computing `16 × cos(π/n)² × 107`, look at the digits right after the decimal point, and take the square root of that integer — `16 × cos(π/n)²` turns out to always be `a + b√3` for some small integers `a` and `b`, and this reveals `b`.

For example:
```
16 × cos(π/12)² = 8 + 4√3
16 × cos(π/12)² × 107 = 1597.32
```
Dividing `n` by 3 (`12 / 3 = 4`) tells you the coefficient of `√3` is `4`, confirming `16 × cos(π/12)² = 8 + 4√3`.

From there, solving directly gives the actual value:
```
cos(π/12) = √((8 + 4√3) / 16) = √(2 + √3) / 2 ≈ 0.9659
```
which matches `cos(15°)` exactly.

---

## Notes on the code

`ml2(a, n, k, e)` searches integers `1..n` for one where the fractional part of `i × a` lands inside the target decimal window described by `k` (number of digits) and `e` (the target digit pattern, e.g. `e = 1001` with `k = 5` means the target window is `[0.01001, 0.01002)`). It relies on the fact that for irrational `a`, the fractional parts of `i × a` are equidistributed across `[0, 1)` (Weyl's equidistribution theorem), so a match is essentially guaranteed to exist for large enough `n`.
