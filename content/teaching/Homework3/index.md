---
title: "Good Questions on homework 3"
date: 2020-04-24F21:07:49-08:00
draft: false
tags: ["Matlab", "CIVIL M20", "Spring 2020"]
commantable: True

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
        fprintf("%.1f\n", t);
    end
    t = t + dt;
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
        fprintf("%.1f\n", t);
    end
    t = t + dt;
end
fprintf("final t = %.02f\n", t);
```
The output is `final t = 15.02` which is what we expected. So, the while loop makes sense and then the if statement looks very suspicious. It seems our code doesn't print out the value of `t` after it is greater than or equal to 5.0. As 0 to 15 is a little bit too long, let's make our `tf` to be `5` in order to better observe what exacly happend there.      
```matlab
t = 0;
dt = 0.02;
tf = 5; % we changed it!!!
tol = 1e-6;

while t <= tf
    % your code
    fprintf("t=%.2f\tmod=%.2f\n", t, mod(t, 0.5));
    t = t + dt;
end
fprintf("final t = %.02f\n", t);
```
Here is the output:
```matlab
t=0.00	mod=0.00  % <-- looks good
t=0.02	mod=0.02
t=0.04	mod=0.04
t=0.06	mod=0.06
t=0.08	mod=0.08
t=0.10	mod=0.10
t=0.12	mod=0.12
t=0.14	mod=0.14
t=0.16	mod=0.16
t=0.18	mod=0.18
t=0.20	mod=0.20
t=0.22	mod=0.22
t=0.24	mod=0.24
t=0.26	mod=0.26
t=0.28	mod=0.28
t=0.30	mod=0.30
t=0.32	mod=0.32
t=0.34	mod=0.34
t=0.36	mod=0.36
t=0.38	mod=0.38
t=0.40	mod=0.40
t=0.42	mod=0.42
t=0.44	mod=0.44
t=0.46	mod=0.46
t=0.48	mod=0.48
t=0.50	mod=0.00  % <-- looks good
t=0.52	mod=0.02
t=0.54	mod=0.04
t=0.56	mod=0.06
t=0.58	mod=0.08
t=0.60	mod=0.10
t=0.62	mod=0.12
t=0.64	mod=0.14
t=0.66	mod=0.16
t=0.68	mod=0.18
t=0.70	mod=0.20
t=0.72	mod=0.22
t=0.74	mod=0.24
t=0.76	mod=0.26
t=0.78	mod=0.28
t=0.80	mod=0.30
t=0.82	mod=0.32
t=0.84	mod=0.34
t=0.86	mod=0.36
t=0.88	mod=0.38
t=0.90	mod=0.40
t=0.92	mod=0.42
t=0.94	mod=0.44
t=0.96	mod=0.46
t=0.98	mod=0.48
t=1.00	mod=0.00  % <-- looks good
t=1.02	mod=0.02
t=1.04	mod=0.04
t=1.06	mod=0.06
t=1.08	mod=0.08
t=1.10	mod=0.10
t=1.12	mod=0.12
t=1.14	mod=0.14
t=1.16	mod=0.16
t=1.18	mod=0.18
t=1.20	mod=0.20
t=1.22	mod=0.22
t=1.24	mod=0.24
t=1.26	mod=0.26
t=1.28	mod=0.28
t=1.30	mod=0.30
t=1.32	mod=0.32
t=1.34	mod=0.34
t=1.36	mod=0.36
t=1.38	mod=0.38
t=1.40	mod=0.40
t=1.42	mod=0.42
t=1.44	mod=0.44
t=1.46	mod=0.46
t=1.48	mod=0.48
t=1.50	mod=0.00  % <-- looks good
t=1.52	mod=0.02
t=1.54	mod=0.04
t=1.56	mod=0.06
t=1.58	mod=0.08
t=1.60	mod=0.10
t=1.62	mod=0.12
t=1.64	mod=0.14
t=1.66	mod=0.16
t=1.68	mod=0.18
t=1.70	mod=0.20
t=1.72	mod=0.22
t=1.74	mod=0.24
t=1.76	mod=0.26
t=1.78	mod=0.28
t=1.80	mod=0.30
t=1.82	mod=0.32
t=1.84	mod=0.34
t=1.86	mod=0.36
t=1.88	mod=0.38
t=1.90	mod=0.40
t=1.92	mod=0.42
t=1.94	mod=0.44
t=1.96	mod=0.46
t=1.98	mod=0.48
t=2.00	mod=0.00  % <-- looks good
t=2.02	mod=0.02
t=2.04	mod=0.04
t=2.06	mod=0.06
t=2.08	mod=0.08
t=2.10	mod=0.10
t=2.12	mod=0.12
t=2.14	mod=0.14
t=2.16	mod=0.16
t=2.18	mod=0.18
t=2.20	mod=0.20
t=2.22	mod=0.22
t=2.24	mod=0.24
t=2.26	mod=0.26
t=2.28	mod=0.28
t=2.30	mod=0.30
t=2.32	mod=0.32
t=2.34	mod=0.34
t=2.36	mod=0.36
t=2.38	mod=0.38
t=2.40	mod=0.40
t=2.42	mod=0.42
t=2.44	mod=0.44
t=2.46	mod=0.46
t=2.48	mod=0.48
t=2.50	mod=0.00  % <-- looks good
t=2.52	mod=0.02
t=2.54	mod=0.04
t=2.56	mod=0.06
t=2.58	mod=0.08
t=2.60	mod=0.10
t=2.62	mod=0.12
t=2.64	mod=0.14
t=2.66	mod=0.16
t=2.68	mod=0.18
t=2.70	mod=0.20
t=2.72	mod=0.22
t=2.74	mod=0.24
t=2.76	mod=0.26
t=2.78	mod=0.28
t=2.80	mod=0.30
t=2.82	mod=0.32
t=2.84	mod=0.34
t=2.86	mod=0.36
t=2.88	mod=0.38
t=2.90	mod=0.40
t=2.92	mod=0.42
t=2.94	mod=0.44
t=2.96	mod=0.46
t=2.98	mod=0.48
t=3.00	mod=0.00  % <-- looks good
t=3.02	mod=0.02
t=3.04	mod=0.04
t=3.06	mod=0.06
t=3.08	mod=0.08
t=3.10	mod=0.10
t=3.12	mod=0.12
t=3.14	mod=0.14
t=3.16	mod=0.16
t=3.18	mod=0.18
t=3.20	mod=0.20
t=3.22	mod=0.22
t=3.24	mod=0.24
t=3.26	mod=0.26
t=3.28	mod=0.28
t=3.30	mod=0.30
t=3.32	mod=0.32
t=3.34	mod=0.34
t=3.36	mod=0.36
t=3.38	mod=0.38
t=3.40	mod=0.40
t=3.42	mod=0.42
t=3.44	mod=0.44
t=3.46	mod=0.46
t=3.48	mod=0.48
t=3.50	mod=0.00  % <-- looks good
t=3.52	mod=0.02
t=3.54	mod=0.04
t=3.56	mod=0.06
t=3.58	mod=0.08
t=3.60	mod=0.10
t=3.62	mod=0.12
t=3.64	mod=0.14
t=3.66	mod=0.16
t=3.68	mod=0.18
t=3.70	mod=0.20
t=3.72	mod=0.22
t=3.74	mod=0.24
t=3.76	mod=0.26
t=3.78	mod=0.28
t=3.80	mod=0.30
t=3.82	mod=0.32
t=3.84	mod=0.34
t=3.86	mod=0.36
t=3.88	mod=0.38
t=3.90	mod=0.40
t=3.92	mod=0.42
t=3.94	mod=0.44
t=3.96	mod=0.46
t=3.98	mod=0.48
t=4.00	mod=0.00  % <-- looks good
t=4.02	mod=0.02
t=4.04	mod=0.04
t=4.06	mod=0.06
t=4.08	mod=0.08
t=4.10	mod=0.10
t=4.12	mod=0.12
t=4.14	mod=0.14
t=4.16	mod=0.16
t=4.18	mod=0.18
t=4.20	mod=0.20
t=4.22	mod=0.22
t=4.24	mod=0.24
t=4.26	mod=0.26
t=4.28	mod=0.28
t=4.30	mod=0.30
t=4.32	mod=0.32
t=4.34	mod=0.34
t=4.36	mod=0.36
t=4.38	mod=0.38
t=4.40	mod=0.40
t=4.42	mod=0.42
t=4.44	mod=0.44
t=4.46	mod=0.46
t=4.48	mod=0.48
t=4.50	mod=0.50  % HERE IT IS !!!!!!!!!!!!!!!!!!!!!! I FOUND IT!!!!!!!!!!!!!!!!!!!!!!
t=4.52	mod=0.02
t=4.54	mod=0.04
t=4.56	mod=0.06
t=4.58	mod=0.08
t=4.60	mod=0.10
t=4.62	mod=0.12
t=4.64	mod=0.14
t=4.66	mod=0.16
t=4.68	mod=0.18
t=4.70	mod=0.20
t=4.72	mod=0.22
t=4.74	mod=0.24
t=4.76	mod=0.26
t=4.78	mod=0.28
t=4.80	mod=0.30
t=4.82	mod=0.32
t=4.84	mod=0.34
t=4.86	mod=0.36
t=4.88	mod=0.38
t=4.90	mod=0.40
t=4.92	mod=0.42
t=4.94	mod=0.44
t=4.96	mod=0.46
t=4.98	mod=0.48
t=5.00	mod=0.50
final t = 5.02
```

The result is self-explantory. It seems after `t` is equal to 4.5, the result of operation `mod(t, 0.5)` will be `0.5` instead of `0.0`! But why is that?! Why matlab cannot even finish this simple calculation?! The answer is the precision of floatiing-point numbers. You may either google the IEEE standard for floating-point numbers or go back to watch the first half hour of discussion on week 4 to know more about how floating-point numbers are implementated in matlab.      
The problem happened in our code was that even though we saw the value of `t` is 4.5, the actual number stored in the machine was 4.49999... As a result, when matlab takes the remainder of 4.4999999... / 0.5, it realizes that 0.4999999... should be the remainder and that is the reason why our mod is 0.5 (actually it is 0.4999999).       
To prove our assumption:
```matlab
t = 0;
dt = 0.02;
tf = 5; % we changed it!!!
tol = 1e-6;

for i = 1: 225
    t = t + dt;
end
fprintf("t=%.2f\t==4.5?%d\t<4.5?%d\n", t, t==4.5, t<4.5);

>>
t=4.50  ==4.5?0	<4.5?1
```
Here we go! `t` looks 4.5, it is not equal to 4.5 and it is actually less than 4.5! Done!      
Then how do we fix this problem?          
I will recommand you to use iteration counts as the condition instead of time because integer is more reliable than floating-point numbers. So, the final code should look like:
```matlab
t = 0;
dt = 0.02;
tf = 15;
tol = 1e-6;
iterCount = 0;

while t <= tf
    % your code
    if mod(iterCount, 25) < tol
        fprintf("%.1f\n", t);
    end
    t = t + dt;
    iterCount = iterCount + 1;
end

>>
0.0
0.5
1.0
1.5
2.0
2.5
3.0
3.5
4.0
4.5
5.0
5.5
6.0
6.5
7.0
7.5
8.0
8.5
9.0
9.5
10.0
10.5
11.0
11.5
12.0
12.5
13.0
13.5
14.0
14.5
15.0
```

Yeah! Cheers!