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
