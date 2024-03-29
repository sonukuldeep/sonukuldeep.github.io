---
layout: home
title: Functions
parent: Solidity
---

## Function
Function in Solidity is defined using the function keyword, followed by a unique function name, a list of parameters (that might be empty), and a statement block surrounded by curly braces.

### Syntax
```c++
function function-name(parameter-list) scope returns() {
   //statements
}
```
### Example 1:
```c++
pragma solidity ^0.5.0;

contract Test {
   function getResult() public view returns(uint){
      uint a = 1; // local variable
      uint b = 2;
      uint result = a + b;
      return result;
   }
}
```

### Example 2:
```c++
// SPDX-License-Identifier: GPL-3.0

pragma solidity >=0.7.0 <0.9.0;

contract LearnFunctions {
    // function functionName(parameter-list) scope return() { logic }

    // local variable superceeds state variable
    uint256 a = 45; // state variable

    function addValues() public pure returns (uint256) {
        uint256 a = 2; // local variable
        uint256 b = 3;
        uint256 c = a + b;
        return c;
    }

    function addNewValues() public pure returns (uint256) {
        uint256 a = 1;
        uint256 b = 2;
        uint256 c = a + b;
        return c;
    }

    function multiplyCalculator(uint256 a, uint256 b)
        public
        pure
        returns (uint256)
    {
        return a * b;
    }

    function divideCalculate(uint256 a, uint256 b)
        public
        pure
        returns (uint256)
    {
        return a / b;
    }
}
```

### Calling a Function

To invoke a function somewhere later in the Contract, you would simply need to write the name of that function.

### Function Parameters
A function can take multiple parameters separated by comma.

### The return Statement

A Solidity function can have an optional return statement. This is required if you want to return a value from a function. This statement should be the last statement in a function.
```c++
pragma solidity ^0.5.0;

contract Test {
   function getResult() public view returns(uint product, uint sum){
      uint a = 1; // local variable
      uint b = 2;
      product = a * b;
      sum = a + b;
  
      //alternative return statement to return 
      //multiple values
      //return(a*b, a+b);
   }
}
```
<hr>

### Pure function
Pure functions ensure that they don't read or modify the state.<br> A function can be declared as pure. The following statements if present in the function are considered reading the state and compiler will throw warning in such cases.

    Reading state variables.

    Accessing address(this).balance or <address>.balance.

    Accessing any of the special variable of block, tx, msg (msg.sig and msg.data can be read).

    Calling any function not marked pure.

    Using inline assembly that contains certain opcodes.

Pure functions can use the revert() and require() functions to revert potential state changes if an error occurs.

Example;
```c++
pragma solidity ^0.5.0;

contract Test {
   function getResult() public pure returns(uint product, uint sum){
      uint a = 1; 
      uint b = 2;
      product = a * b;
      sum = a + b; 
   }
}
```
<hr>

## Fallback function
Fallback function is a special function available to a contract.<br> It has following features

    It is called when a non-existent function is called on the contract.

    It is required to be marked external.

    It has no name.

    It has no arguments

    It can not return any thing.

    It can be defined one per contract.

    If not marked payable, it will throw exception if contract receives plain ether without data.


Example
```c++
pragma solidity ^0.5.0;

contract Test {
   uint public x ;
   function() external { x = 1; }    
}
contract Sink {
   function() external payable { }
}
contract Caller {
   function callTest(Test test) public returns (bool) {
      (bool success,) = address(test).call(abi.encodeWithSignature("nonExistingFunction()"));
      require(success);
      // test.x is now 1

      address payable testPayable = address(uint160(address(test)));

      // Sending ether to Test contract,
      // the transfer will fail, i.e. this returns false here.
      return (testPayable.send(2 ether));
   }
   function callSink(Sink sink) public returns (bool) {
      address payable sinkPayable = address(sink);
      return (sinkPayable.send(2 ether));
   }
}
```
<hr>

## Function overload 
You can have multiple definitions for the same function name in the same scope. <br> The definition of the function must differ from each other by the types and/or the number of arguments in the argument list. You cannot overload function declarations that differ only by return type.

Following example shows the concept of a function overloading in Solidity.
Example

```c++
pragma solidity ^0.5.0;

contract Test {
   function getSum(uint a, uint b) public pure returns(uint){      
      return a + b;
   }
   function getSum(uint a, uint b, uint c) public pure returns(uint){      
      return a + b + c;
   }
   function callSumWithTwoArguments() public pure returns(uint){
      return getSum(1,2);
   }
   function callSumWithThreeArguments() public pure returns(uint){
      return getSum(1,2,3);
   }
}
```
