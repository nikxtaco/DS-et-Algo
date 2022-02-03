# ???Methods To Print Prime Numbers:

* Brute force - Check if each number n, starting from 2 is divisible by any number between and including 2 and (n-1) and if so, it is not prime. If it is prime, then output the number.
Complexity: O(n) for N = 1. And O(n^2) for N > 1.

* Slightly better method - Check the same but only check for divisors between 2 and root n. The justification for why this works is - If a number n is not a prime, it can be factored into two factors a and b, that is, n = a * b. Now a and b can't be both greater than the square root of n, since then the product a * b would be greater than sqrt(n) * sqrt(n) = n. So in any factorization of n, at least one of the factors must be smaller than the square root of n, and if we can't find any factors less than or equal to the square root, n must be a prime.
Complexity: O(N.rootN) for N numbers.

## Q. Output all prime numbers till N.

```
using namespace std;

bool isValidSubsequence(vector<int> array, vector<int> sequence) {
  
	int i,j;
	
	for(i=0, j=0; i<array.size() && j<sequence.size(); i++)
	{
		if(array[i] == sequence[j])
			j++;
	}
	
	if(j == sequence.size())
		return true;
	else
	  return false;
}
```
