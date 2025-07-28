---
title: Avoiding Overflow Condition
description: How to Avoid Overflow Condition
tags:
  - utility
---

> Checking for overflow conditions have always been tedious to remember logic. Lets deep dive !

## Condition for Not Overflowing

$$
(number \times 10) + unit\_digit < \text{INT\_MAX}
$$

## But,  
- But if you're storing `number x 10 + unit_digit` in a variable , at some point the variable will overflow. 
	- If there is a continuous addition to the LHS of this equation. 
- Question we are trying to answer here is :- 
	- Can we apply some kind of `CHECK` to avoid this overflow.
- Well we can just apply some maths and the above equation can be written like this :-

$$
number \lt \frac{\text{INT\_MAX} - unit\_digit}{10}
$$

>[!success]	Well ! Now
>- Now before storing the answer of `number x 10 + unit_digit`  a check can be introduced. 
>- This would make sure, the condition is `NOT OVERFLOWED`

