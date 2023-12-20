# linear-optimization

## Revised simplex and short step dual barrier

## Revised Simplex Method

### Initial Basis: slack variables

Dantzig's Pivoting Rules

  - Enter: the smallest negative reduced cost
  - Leave: min-ratio, if tie, the smallest index

Bland's Pivoting Rules

  - Enter/Leave: Among valid, the smallest variable index

### Initial Basis: Random 

Dantzig's Pivoting Rules

Bland's Pivoting Rules

### Indicate the path traced by the simplex method and compare the strategies for different initial bases

## Short Step Dual Barrier Method (Interior Point method)
### dual_barrier
Input
  - A, b, c: the LP data
  - p0: the initial dual solution
  - mu0: the initial path parameter
  - alpha: the decrease rate of the path parameter
  - tol: the optimality tolerance
  - K: the number of Newton steps per path parameter

Output
  - p: the optimal dual solution
  - objvals: the objective values $b^Tp^{(i)}$
  - pvecs: the feasible solutions $p^{(i)}$ across iterations

### Newton
Input: A, b, c, mu, p, K

Output: p

This function is called inside of dual_barrier()


Note that Simplex method is mathematically simpler while computationally more complicated than Short Step Dual Barrier method. 

Also, note that Short Step Dual Barrier method is faster in Large LPs, but should switch to Simplex when we resolve the LP. 
On the other hand Simplex method is faster in small LPs, and it is easy to update solution, but it is sensitive to degeneracy. 

It is recommended that find initial solution using simplex, and with that initial solution, go to Short Step Dual Barrier, fininally switch to Simplex again if we need to resolve. 
