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
is the temperature. At every step temperature decreases with a fixed decrease rate.
Iterations stop when a fixed final temeprature is reached.

The best solution is stored in any case, so that even if the final solution is a worsening one, the best found that far is still preserved.

> ⚠️WARNING: Actual parameters in the algorithm are calibrated for finding a very good solution but it needs some time
>(~3 min for 42 cities). If a faster but a bit worse solution is desired, one or more of the following solutions may be used:
>- Decrease the steady_state parameter
>- Decrease the start_temperature parameter
>- Increase the decrease_rate parameter
>
>Using aggressively these solutions may eventually lead to a "not so nice solution"