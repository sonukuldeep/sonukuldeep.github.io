---
layout: home
title: Conditional
parent: Solidity
---

## Conditional
Solidity supports conditional statements which are used to perform different actions based on different conditions.
* if
* if... else
* if.. else if 

#### if
Syntax:
```c++
if (expression) {
   Statement(s) to be executed if expression is true
}
```

#### if.. else
Syntax:
```c++
if (expression) {
   Statement(s) to be executed if expression is true
}
else {
   Statement(s) to be executed if expression is false
}
```

#### if.. else if

Syntax:
```c++
if (expression 1) {
   Statement(s) to be executed if expression 1 is true
} else if (expression 2) {
   Statement(s) to be executed if expression 2 is true
} else if (expression 3) {
   Statement(s) to be executed if expression 3 is true
} else {
   Statement(s) to be executed if no expression is true
}
```

Example:
```c++
// SPDX-License-Identifier: GPL-3.0
 
pragma solidity >=0.7.0 <0.9.0;
 
contract DecisionMaking {
    uint256 orange = 5;
 
    // one = sign assign value
    function validateOrange() public view returns (bool) {
        if (orange == 6) {
            // 2 = signs equivalates value
            return true;
        } else {
            return false;
        }
    }
}
```