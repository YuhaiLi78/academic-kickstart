---
title: "C++ Study Note 1: const"
date: 2020-02-29T08:02:57-08:00
draft: false
tags: ["c++", "Programming Language"]

header:
  caption: "by GeeksforGeeks"
  image: "c++.png"
---

# 1. `const`
A variable or an object declared by keyword `const` is not motifiable.

# 2. Roles
(1) Declare a constant variable
```C++
const int LENGTH = 20;
```

(2) Type checking    
`const` variable is commonly confused with `#define` micro, however, they are technically different. The constant variable declared by `const` is typed, so it can be type-checked by compiler through static type checking. But the micro defined by `#define` is a typeless placeholder. It does nothing more than a string replacement while the program is compiled, so the static type checking has nothing to do with it.

(3) Foolproof    
Prevent your stupid co-workers from changing the value of a predefined constant.

bad coding style:
```c++
// This is fxxking important!!!
// DO NOT change its value, or I will KILL you!!!
int TOTAL_NUM = 100;
```
good coding style:
```c++
const int TOTAL_NUM = 100;
```

(4) Memory saving    
In the assembly language, a `const` variable is referred by a memory address, rather than a concrete value, like `#define` does. So, a `const` variable has only one copy in the memory while `#define` micro may have multiple copies.

# 3. Scope
(1) A nonconst variable can be referred in another file.
```c++
// example1.cpp
int example;
// example2.cpp
#include<iostream>
using namespace std;

extern int example;

int main(){
    cout << example << endl;
}
// g++ -o executable example2.cpp example1.cpp
// ./executable
// 0
```

(2) A variable declared by keyword `const` is local to file by default, which means if you want it to be referred in another file, you have to explicitly declare that using `extern`.
```c++
// example1.cpp
extern const int example = 100;
// example2.cpp
#include<iostream>
using namespace std;

extern int example;

int main(){
    cout << example << endl;
}
// g++ -o executable example2.cpp example1.cpp
// ./executable
// 100
```
Notice that in order to be used externally, a `const` variable has to not only be declared by `extern` but also to be initialized because its value is unmotifiable after declarition.

# 4. Utility and common mistakes
(1) Unmotifiable after declarition
```c++
const int a = 123;
a = 666; // error!
```

(2) Must be initialized
```c++
const int b; // error!
```
