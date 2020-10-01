# Dynamic-Programming

## Standard DP Problems.

1. 0-1 Knapsack

```c++

#include <bits/stdc++.h>
using namespace std ;

int dp[310][10010] ;
int wt[310] ;

int main () {

   int W ;
   cin >> W ;
   int n ;
   cin >> n ;
   for (int i = 1 ; i <= n ; ++i) {
       cin >> wt[i] ; 
   }
   for (int i = 1 ; i <= n ; ++i) {
       for (int j = 1 ; j <= W ; ++j) {
           if (wt[i] <= j) { // I compared this becasue j-wt[i] might become < 0
               dp[i][j] = max(dp[i-1][j] , dp[i-1][j-wt[i]] + wt[i]) ; // taking max of (take this weight and don't take it)
           } else {
               dp[i][j] = dp[i-1][j] ; // I don't take the item, hence, it is same as making this weight with previous values
           }
           
       }
   }
   cout << dp[n][W] ;

   cout << "\n" ;
   return 0 ;
}

```

2. Fibonacci Problem.

```c++

#include<bits/stdc++.h>

using namespace std ;

#define vi vector <int>
#define MAX 100

// Normal fibonacci sequence ::
int fib_normal(int n)
{
	if (n <= 1)
	   return n ;
	return fib_normal(n-1) + fib_normal(n-2) ;
}

// fibonacci sequence by memoization(top-down) ::

vi memo(MAX , -1) ;

int fib_memoization(int n)
{
	if (memo[n] == -1)
	{
		if (n <= 1)
		    memo[n] = n ;
		else
		    memo[n] = fib_memoization(n-1) + fib_memoization(n-2) ;
	}
	return memo[n] ;
}

// fibonacci sequence by tabulation(bottom-up) ::

int fib_tabulation(int n)
{
	int f[n+1] ;
	f[0] = 0 ;
	f[1] = 1 ;
	for (int i = 2 ; i < n+1 ; i++)
	{
		f[i] = f[i-1] + f[i-2] ;
	}
	return f[n] ;
}

int main()
{
	int a = 40 ;
	cout << fib_tabulation(a) ;
	return 0 ;
}

```
