# Last Digit of a^b for Large Numbers [https://www.geeksforgeeks.org/problems/find-last-digit-of-ab-for-large-numbers1936/1]

You are given two integer numbers, the base a and the index b. You have to find the last digit of ab.

## Example

Input:

a = "3", b = "10"

Output:

9

Explanation:

310 = 59049. Last digit is 9.


## Approach

- We're using `BigInteger` because the input numbers could be very large, beyond the capacity of primitive data types like `int` or `long`.
- `BigInteger` allows us to perform arithmetic operations on arbitrarily large integers.
- In this problem, we need to find the last digit of \( a^b \), where \( a \) and \( b \) are large numbers represented as strings.
- We use `modPow()` method of `BigInteger` to efficiently calculate \( a^b \mod 10 \), which gives us the last digit.
- Finally, we convert the resulting `BigInteger` to an `int` to return the last digit.

## Using BigInteger

- **Constructors**: You can create a `BigInteger` object from a string representation of a number using the constructor `new BigInteger(String)`. For example: `BigInteger bigInteger = new BigInteger("12345678901234567890");`
- **Arithmetic Operations**: `BigInteger` supports arithmetic operations such as addition, subtraction, multiplication, and division using methods like `add()`, `subtract()`, `multiply()`, and `divide()`.
- **Modular Arithmetic**: To perform modular arithmetic, you can use `mod()` method to find the remainder when dividing by another `BigInteger`.
- **Exponentiation**: For exponentiation, `BigInteger` provides `pow()` method. However, for this specific problem, `modPow()` method is more suitable as it efficiently calculates the power modulo a given integer.
- **Conversion**: You can convert a `BigInteger` to an `int` or `long` using `intValue()` or `longValue()` methods respectively. Be cautious of potential loss of precision if the `BigInteger` value is too large to fit in the primitive data types.

These are some basic operations and considerations when using `BigInteger` for handling large numbers in Java.

```
class Solution {
    static int getLastDigit(String a, String b) {
        // code here
         return new BigInteger(a).modPow(new BigInteger(b), BigInteger.TEN).intValue();
    }
};
```
