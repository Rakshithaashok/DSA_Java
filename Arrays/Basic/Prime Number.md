# Prime Number Checker [https://www.geeksforgeeks.org/problems/prime-number2314/1]

## Description
This Java program checks whether a given number is prime or not.

## Code Explanation
```
class Solution {
    static int isPrime(int N) {
        // If N is less than or equal to 1, it's not prime
        if (N <= 1) {
            return 0;
        }
        
        // Iterate from 2 to the square root of N
        for (int i = 2; i * i <= N; i++) {
            // If N is divisible by i, it's not prime
            if (N % i == 0) {
                return 0;
            }
        }
        
        // If no factors other than 1 and N itself are found, N is prime
        return 1;
    }
}
```

## Optimization Explanation
- We only need to iterate up to the square root of `N` for factor checking.
- Therefore, by the time we reach the square root of `N`, we've already encountered all possible factors of `N`. Continuing to iterate beyond this point would involve redundant checks.
- For example, in the case of `N = 36`, after checking factors up to `6`, no number greater than `6` (e.g., `7`, `8`) would be a factor of `N`.
