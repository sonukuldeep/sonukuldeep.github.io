---
layout: home
title: View functions
parent: Solidity
---

## View Functions
View functions ensure that they will not modify the state. A function can be declared as view. The following statements if present in the function are considered modifying the state and compiler will throw warning in such cases.

    Modifying state variables.

    Emitting events.

    Creating other contracts.

    Using selfdestruct.

    Sending Ether via calls.

    Calling any function which is not marked view or pure.

    Using low-level calls.

    Using inline assembly containing certain opcodes.

Getter method are by default view functions.

See the example below using a view function.
Example
```c++
pragma solidity ^0.5.0;

contract Test {
   function getResult() public view returns(uint product, uint sum){
      uint a = 1; // local variable
      uint b = 2;
      product = a * b;
      sum = a + b; 
   }
}
```