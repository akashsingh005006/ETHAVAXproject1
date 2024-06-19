// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract expenseManagement{
    address public person;
    uint public income;
    uint public expenditure;
    uint public savings;

   event incomeReceived(address indexed account,uint amount);
   event ExpenditureAmount(address indexed account,uint amount);
   event savingUpdate(uint newSavings);

   constructor() {
    person=msg.sender;
    savings=0;
 }

function receiveIncome(uint amount) public {
    require(msg. sender  == person, "Unauthorized");
    require(amount > 0, "Sufficient Money");

    income=income + amount;
    savings=savings + amount;

    emit incomeReceived(msg.sender,amount);
    emit savingUpdate(savings);

    assert(savings >= income);
}

function expenditureRecord(uint amount) public {
    require(msg.sender == person ,"Unauthorized");
    require(amount > 0 ,"expenditure must be positive ");
    require(savings >= amount ,"insufficient savings");

    expenditure = expenditure + amount;
    savings = savings - amount; 

    emit ExpenditureAmount(msg.sender, amount);
    emit savingUpdate(savings);

    assert(savings >= 0);
}

function remainingSaving() public view returns (uint) {
    return savings;

}

function disallowedOperation() public pure {
    revert("operation not allowed");
}

}
