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
$T(n) = T(n/13^{log_{13}(n)}) + 5log_{13}(n)$ <br>
$T(n) = T(1) + 5log_{13}(n)$ <br>
$T(n) = 1 + 5log_{13}(n)$ <br>
Since the constants aren't important asymptotically, as they won't impact the runtime tremendously like log(n) will <br>
So the $\Theta$ bound is $\Theta(log(n))$

2.
$$ T(n) =
    \begin{cases}
        1 & n \leq 1\\
        13 T\left(\frac{n}{13}\right) + 5 & n > 1
    \end{cases}
$$

My answer: 

Solve for T(n/13) and sub back in: <br>
T(n) = 13T(n/13) + 5 <br>
T(n/13) = 13T(n/169) + 5 <br>
T(n) = 13(13T(n/169) + 5) + 5 <br>
T(n) = 169T(n/169) + 70 (13*5+5 = 70) <br>

Now solve for T(n/169) (to establish a better pattern) and sub back in: <br>
T(n/169) = 13T(n/2197) + 5 <br>
T(n) = 169(13T(n/2197) + 5) + 70 <br>
T(n) = 2197T(n/2197) + 915 <br>

The pattern seems to be: <br>
$T(n) = 13^i * T(n/13^i)$ + $$\left( \sum_{j=0}^{i-1} 13^j * 5 \right)$$ <br>
To achieve the base case of 1, i needs to be equal to $log_{13}(n)$ <br>

Now we have:  <br>
$T(n) = 13^{log_{13}(n)} * T(n/13^{log_{13}(n)})$ + $$\left( \sum_{j=0}^{log_{13}(n) 13^j * 5 \right)$$ <br>
The sum can be reduced down to n/13 because the summation from 0 up until $log_{13}(n)$ -1, will be a constant number, so the summation would look like $13^0 * 5 + 13^1 * 5$ and so on until $13^{log_{13}(n) -1}$ is reached. The summation would then become some constant c plus $13^{log_{13}(n)} * 13^{-1}$ which equals n/13. <br>

Going back to T(n) we have: <br>
$T(n) = n * 1 + n/13$ <br>
Which essentially equals: <br>
T(n) = 2n <br>
And once more, because constants aren't important, the 2 can be dropped to get T(n) = n. <br>
Therefore, the $\Theta$ bound is $\Theta(n)$

3.
$$ T(n) =
    \begin{cases}
        1 & n \leq 1\\
        13 T\left(\frac{n}{13}\right) + 2n & n > 1
    \end{cases}
$$
