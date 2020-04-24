---
title: "Good Questions on homework 3"
date: 2020-04-24F21:07:49-08:00
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

while t <= tf
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
<img src="https://i.kym-cdn.com/photos/images/original/000/993/875/084.png">
Why it is not what we thought? Let's investigate in detail what the hell is happening in our code.
First off, our while loop eventually ternminated which means our `t` was updated properly and finally went beyond `tf`. We may prove our assumption by adding another line to print out the value of `t` after the while loop terminated:
```matlab
t = 0;
dt = 0.02;
tf = 15;
tol = 1e-6;

while t <= tf
    % your code
    if mod(t, 0.5) < tol
        fprintf("%.1f\n", t)
    end
    t = t + dt
end
fprintf("final t = %.02f\n", t);
```
The output is `final t = 15.02` which is what we expected. So, the while loop looks great. 
