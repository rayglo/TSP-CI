# Travelling Salesman Problem

By Marco Riggio (s292515)

Proposed solution uses a Simulated Annealing approach. At every iteration, two random cities are swapped, with 100% of
probability. If the new solution is better than the old one, the new solution is used for following iterations. If the
new solution is worse, there's a probability to accept it in any case for following iterations.

For the first iterations, a more exploratory approach is used, and as iterations go on, exploitation is what drives more
the algorithm. Probability of negative worsening is given by the following formula

```
p = exp(-(S'-S)/t)
```

Where S is the cost of the actual solution, S' is the cost of the new solution and t
is the temperature. As iterations go on, temperature decreases with a fixed decrease rate.
Iterations stop when a fixed final temeprature is reached.

Temperature is decreased only when a mutation is applied, else
it would remain the same. Even if it is a variation from the original algorithm, I found to have better results, since it tries
to give more solution instead of staying on the same solution. This comes with a drawback: if the optimal solution is found, the algorithm may
not terminate, since the temperature is never decreased. For this reason I've added a steady state detection mechanism, that must be set to an high
value in order not to limit the algorithm in finding the solution and have an early termination.

The best solution is stored in any case, so that even if the final solution is a worsening one, the best found that far is still preserved.

> ⚠️WARNING: Actual parameters in the algorithm are calibrated for finding a very good solution but it needs some time
>(~12 min for 42 cities). If a faster but a bit worse solution is desired, one or more of the following solutions may be used:
>- Removing Indentation at line 131, which will decrease temperature at every cycle
>- Decrease the steady_state parameter
>- Decrease the start_temperature parameter
>- Increase the decrease_rate parameter
>
>Using aggressively these solutions may eventually lead to a "not so nice solution"