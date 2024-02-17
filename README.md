[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-24ddc0f5d75046c5622901739e7c5dd533143b0c8e959d652212380cedb1ea36.svg)](https://classroom.github.com/a/8KYthzwp)
# Recurrent Recurrences

Give big $\Theta$ bounds for the following recurrence relations.

1.
$$ T(n) =
    \begin{cases}
        1 & n \leq 1\\
        T\left(\frac{n}{13}\right) + 5 & n > 1
    \end{cases}
$$

My answer: 

Solve for T(n/13) and sub back in: <br>
T(n) = T(n/13) + 5 <br>
T(n/13) = T(n/169) + 5 <br>
T(n) = T(n/169) + 5 + 5 <br>
T(n) = T(n/169) + 10 <br>

Now solve for T(n/169) (to establish a better pattern) and sub back in: <br>
T(n/169) = T(n/2197) + 5 <br>
T(n) = T(n/2197) + 5 + 10 <br>
T(n) = T(n/2197) + 15 <br>

The pattern seems to be: <br>
$T(n) = T(n/13^i) + 5 * i$ <br> 
To achieve the base case of 1, i needs to equal $log_13(n)$ <br>
Now we have: <br>
$T(n) = T(n/13^{log_13(n)}) + 5log_13(n)$ <br>
$T(n) = T(1) + 5log_13(n)$ <br>
$T(n) = 1 + 5log_13(n)$ <br>
Since the constants aren't important asymptotically, as they won't impact the runtime tremendously like log(n) will <br>
So the $/Theta$ bound is $/Theta(log(n))$

2.
$$ T(n) =
    \begin{cases}
        1 & n \leq 1\\
        13 T\left(\frac{n}{13}\right) + 5 & n > 1
    \end{cases}
$$

3.
$$ T(n) =
    \begin{cases}
        1 & n \leq 1\\
        13 T\left(\frac{n}{13}\right) + 2n & n > 1
    \end{cases}
$$
