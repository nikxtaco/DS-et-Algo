# Methods To Print Prime Numbers:

* Brute force - Check if each number n, starting from 2 is divisible by any number between and including 2 and (n-1) and if so, it is not prime. If it is prime, then output the number.
Complexity: O(n) for N = 1. And O(n^2) for N > 1.

* Slightly better method - Check the same but only check for divisors between 2 and root n. The justification for why this works is - If a number n is not a prime, it can be factored into two factors a and b, that is, n = a * b. Now a and b can't be both greater than the square root of n, since then the product a * b would be greater than sqrt(n) * sqrt(n) = n. So in any factorization of n, at least one of the factors must be smaller than the square root of n, and if we can't find any factors less than or equal to the square root, n must be a prime.
Complexity: O(N.rootN) for N numbers.

* Sieve of Eratosthenes - Initialize a boolean array with N+1 locations and set all places to true for being prime. In the first loop, traverse from 2 to root n and check whether the given number holds the value true, and if so, assign all its multiples the value false, starting from the square of that number (same reasoning as in method 2) to N. Now the array contains a true value for all prime numbers alone. Output the same in a second loop.
Complexity: O(N.loglogN) for N numbers.

## Q. Output all prime numbers till N.

```
#include <bits/stdc++.h> 
using namespace std;

void prime_sieve(int n)
{
  bool p[n+1];
  memset(p,true,sizeof(p)); // set all locations to being true for being prime.

  for(int i=2;i*i<=n;i++)
  {
    if(p[i]==true)
      for(int j=i*i;j<=n;j+=i)
        p[j]=false;
  } // when a prime number is encountered, set its multiples to false.
  
  for(int i=2;i<=n;i++)
    if(p[i])
      cout<<i<<endl; // output all prime numbers till N.
}

int main() 
{
  int n;
  cout<<"Enter N: ";
  cin>>n;
  prime_sieve(n);

  return 0;
}
```
## Q. Output the first N prime numbers. 

(Further optimization possible.)

```
#include <bits/stdc++.h> 
using namespace std;

void prime_sieve(int n)
{
  bool p[n+1];
  memset(p,true,sizeof(p)); // set all locations to being true for being prime.
  int counter = 0, N;

  cout<<"Enter N: ";
  cin>>N;

  for(int i=2;i*i<=n;i++)
  {
    if(p[i]==true)
      for(int j=i*i;j<=n;j+=i)
        p[j]=false;
  } // when a prime number is encountered, set its multiples to false.
  
  for(int i=2;counter<N;i++)
    if(p[i])
    {
      cout<<i<<endl;
      counter++;
    } // output N prime numbers.
}

int main() 
{  
  int n = 10000; // enter maximum prime number value.
  prime_sieve(n);

  return 0;
}
```
