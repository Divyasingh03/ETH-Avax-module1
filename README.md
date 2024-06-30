# Implementation of Require(), Assert() and Revert()

This Solidity program demonstrates the basic syntax and functionality of the Solidity programming language.
## Description

This project features a simple Solidity smart contract designed to demonstrate the use of the require(), assert(), and revert() statements for error handling. The contract includes functions to set a number and then double that number, with built-in validations to ensure proper usage. The setValue function allows setting a new value while ensuring the input is not equal to zero using the require() statement. The getValue function retrieves the stored value and employs the assert() statement to ensure the value has been set and is not equal to zero. The simulateError function simulates the invalid operation, using the revert() statement to prevent double of number if the value is equal to zero. This contract provides a clear and practical example of implementing error handling mechanisms in Solidity to create robust and secure smart contracts.
The Functions_Errors smart contract is a Solidity-based contract designed to perform basic arithmetic operations while demonstrating error handling techniques. It includes functions to double values to a cumulative result (double), retrieve the current result (number*2). The double function requires the input value to be non zero, ensuring valid input with a require statement. The checkNumber function employs an assert statement to guarantee the number is non-zero, reflecting an internal consistency check. The simulateError function reverts the transaction if any invalid operation occurs, showcasing the use of the revert statement to handle exceptional conditions. The contract is a straightforward example of how to implement and manage state while incorporating Solidity's error handling mechanisms to ensure reliable and predictable behavior.
## Getting Started

### Executing program

// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract ErrorHandlingExample {
    uint public number;
    address public owner;

    constructor() {
        owner = msg.sender;
    }

    // Function to set a number, requires caller to be the owner
    function setNumber(uint _num) public {
        require(msg.sender == owner, "Only the owner can set the number");
        number = _num;
    }

    // Function to double the number, reverts if the number is zero
    function doubleNumber() public {
        require(number != 0, "Number must be non-zero");
        number *= 2;
    }

    // Function to get the number
    function getNumber() public view returns (uint) {
        return number;
    }

    // Function to simulate an assertion: Ensures number is not zero
    function checkNumber() public view returns (bool) {
        assert(number != 0);
        return true;
    }

    // Function to simulate a revert: Simulates an invalid operation
    function simulateError() public pure {
        revert("Invalid operation occurred");
    }
}
