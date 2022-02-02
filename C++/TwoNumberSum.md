# ???Methods To Print Prime Numbers:

* Brute force - Check if each number n, starting from 2 is divisible by any number between and including 2 and (n-1) and if so, it is not prime. If it is prime, then output the number.
Complexity: O(n) for N = 1. And O(n^2) for N > 1.

* Slightly better method - Check the same but only check for divisors between 2 and root n. The justification for why this works is - If a number n is not a prime, it can be factored into two factors a and b, that is, n = a * b. Now a and b can't be both greater than the square root of n, since then the product a * b would be greater than sqrt(n) * sqrt(n) = n. So in any factorization of n, at least one of the factors must be smaller than the square root of n, and if we can't find any factors less than or equal to the square root, n must be a prime.
Complexity: O(N.rootN) for N numbers.

## Q. Output all prime numbers till N.

```
#include <vector>
using namespace std;

vector<int> twoNumberSum(vector<int> array, int targetSum) {

	vector<int> answer;
	int flag = 0, temp;
	for(int num1=0; num1<array.size(); num1++)
	{
		for(int num2=num1+1; num2<array.size(); num2++)
		{
			if((targetSum - array[num1]) == array[num2])
			{
				answer.push_back(array[num1]);
				answer.push_back(array[num2]);
				flag = 1;
				break;
			}
		}
		if(flag == 1)
			break;
	}
	
  return answer;
}
```
## Q. Output the first N prime numbers. 

(Further optimization possible.)

```
#include <vector>
using namespace std;

vector<int> twoNumberSum(vector<int> array, int targetSum) {
  
	unordered_map<int, int> count;
	vector<int> answer;
	
	for(int i=0; i<array.size(); i++)
		count[array[i]] = 0;
	
	for(int i=0; i<array.size(); i++)
		count[array[i]]++;
	
	for(int i=0; i<array.size(); i++)
	{
		if(array[i] == (targetSum - array[i]))
		{
			if(count[array[i]]>1)
			{
				answer.push_back(array[i]);
				answer.push_back(targetSum - array[i]);
				break;
			}
		}
		else if (count.find(targetSum - array[i]) != count.end()) 
		{
			answer.push_back(array[i]);
			answer.push_back(targetSum - array[i]);
			break;
		}
	}
	
  return answer;
}
```
