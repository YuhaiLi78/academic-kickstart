---
title: ""
date: 2020-04-24T21:07:49-08:00
draft: false
tags: ["Matlab", "CIVIL M20", "Spring 2020"]

header:
  caption: ""
  image: "m20-header.png"
---
# What is wrong with mod(t, 0,5)?
In the specification of problem 1, students are asked to print their results every 0.5s. So, the skeleton of someone's implementation looks like:
```matlab
t = 0;
dt = 0.02;
tf = 15;
tol = 1e-6;

while t < tf
    % your code
    if mod(t, 0.5) < tol
        fprintf("%.1f\n", t)
    end
    t = t + dt
end
```
The code looks good and is logically correct. As a result, we should expect a sequence of numbers from 0.0 to 15.0 with increment 0.5 to be printed on the screen. However, there is always a gap between dream and reality. It turns out we got:
```matlab
>>0.0
0.5
1.0
1.5
2.0
2.5
3.0
3.5
4.0
```
<img src="https://www.google.com/url?sa=i&url=https%3A%2F%2Fknowyourmeme.com%2Fmemes%2Fconfused-nick-young&psig=AOvVaw0ec2QwdfETDCgJEFbPoFiu&ust=1587827702895000&source=images&cd=vfe&ved=0CAIQjRxqFwoTCKjxoKatgekCFQAAAAAdAAAAABAD">
Why it is not what we thought?