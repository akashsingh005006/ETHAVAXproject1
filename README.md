# Project Title

Expense Management Smart Contract

## Description

The Solidity code defines an expenseManagement smart contract for managing an individual's income, expenditure, and savings.The contract initializes savings to zero and designates the deployer as the owner. The owner can record income using the receiveIncome method, and expenses can be tracked using the expenditureRecord function to make sure they don't exceed savings.. The current savings balance is returned by the remainingSaving function.. Error handling mechanisms are incorporated to enforce rules and prevent unauthorized access. This smart contract promotes disciplined financial habits by maintaining strict checks on income and expenditure limits.

## Getting Started

### Installing
1.**Preparing REMIX**
- Visit [REMIX]
- Create a file name `Module1project.sol.
- insert the code and save into `Module1project.sol`.

### Executing program

1.**Compile and deploy**
- Compile the code using the "Solidity Compiler" tab.
- Deploy the contract using the "Deploy & Run Transactions" tab.

### Contract Code
```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract expenseManagement {
    address public person;
    uint public income;
    uint public expenditure;
    uint public savings;
    uint public constant Incomerequired = 5000;
     uint public constant expenditureLimit = 5000;
     uint public constant incomeLimit = 10000;

    event incomeReceived(address indexed account, uint amount);
    event ExpenditureAmount(address indexed account, uint amount);
    event SavingUpdate(uint newSavings);
    

    constructor() {
        person = msg.sender;
        savings = 0;
    }

    function receiveIncome(uint amount) public {
        require(msg.sender == person, "Unauthorized ");
        require(amount > 0, "Sufficient Money");

        if (income + amount > incomeLimit) {
            revert("Income exceeds taxless limit: Tax Applied");
        }

        income =income+ amount;
        savings = savings + amount;

        emit incomeReceived(msg.sender, amount);
        emit SavingUpdate(savings);

        assert(savings >= income);
    }

    function expenditureRecord(uint amount) public {
        require(msg.sender == person, "Unauthorized ");
        require(amount > 0, "expenditure must be positive");
        require(savings >= amount, "Insufficient savings for expenditure");

        if (expenditure + amount > expenditureLimit) {
            revert("Expenditure limits should < 5000");
        }

        expenditure = expenditure + amount;
        savings = savings - amount; 

        emit ExpenditureAmount(msg.sender, amount);
        emit SavingUpdate(savings);

        assert(savings >= 0);
    }

    function remainingSaving() public view returns (uint) {
        return savings;
    }

    function ConditionCheck() public view {

    if (msg.sender != person) {
        revert("Unauthorized access: owner has only access to this function");
    }
 if (income < Incomerequired) {
            // Case 1: Income is less than requiredIncome
            revert("no sufficient income for expenditure");
        } else if (income >= Incomerequired && income <= incomeLimit) {
            // Case 2: Income is within the valid range
            if (expenditure <= expenditureLimit) {
                revert("Operation is allowed.");
            } else if (expenditure> expenditureLimit) {
               revert ("operation not allowed");
            }
        } else if (income > incomeLimit) {
            // Case 3: Income exceeds incomeLimit
            revert("Income exceeds taxless limit.");
        } else {
            revert("unknown condition");
        }

    }      
}
    
```

## Help

Any advise for common problems or issues.
```
command to run if program contains helper info
```

## Authors
Akash Singh


## License

This project is licensed under the MIT License 

