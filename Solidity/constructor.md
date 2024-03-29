---
layout: home
title: Constructor
parent: Solidity
---

## Constructor
Constructor is a special function declared using constructor keyword. It is an optional funtion and is used to initialize state variables of a contract. Following are the key characteristics of a constructor.

* A contract can have only one constructor.

* A constructor code is executed once when a contract is created and it is used to initialize contract state.

* After a constructor code executed, the final code is deployed to blockchain. This code include public functions and code reachable through public functions. Constructor code or any internal method used only by constructor are not included in final code.

* A constructor can be either public or internal.

* A internal constructor marks the contract as abstract.

* In case, no constructor is defined, a default constructor is present in the contract.

```c++
pragma solidity ^0.8.0;

contract Test {
   constructor() {}
}
```
In case, base contract have constructor with arguments, each derived contract have to pass them.

Base constructor can be initialized directly using following way −
```c++
pragma solidity ^0.8.0;

contract Base {
   uint data;
   constructor(uint _data) public {
      data = _data;   
   }
}
contract Derived is Base (5) {
   constructor() {}
}
```
Base constructor can be initialized indirectly using following way −
```c++
pragma solidity ^0.8.0;

contract Base {
   uint data;
   constructor(uint _data) {
      data = _data;   
   }
}
contract Derived is Base {
   constructor(uint _info) Base(_info * _info) {}
}
```
Direct and Indirect ways of initializing base contract constructor is not allowed.

If derived contract is not passing argument(s) to base contract constructor then derived contract will become abstract.
