# Start
The expenseManagement smart contract manages income, expenditure, and savings for an individual.It has function to track income and expenses, make sure spending doesn't go over savings, and release events to promote transparency. The contract also shows how to handle unlawful transactions and gives the current savings amount.
## Description
The Solidity code defines an expenseManagement smart contract for managing an individual's income, expenditure, and savings.The contract initializes savings to zero and designates the deployer as the owner. The owner can record income using the receiveIncome method, and expenses can be tracked using the expenditureRecord function to make sure they don't exceed savings. The current savings balance is returned by the remainingSaving function. To provide transparency, events are released for registering expenses and receiving income. Furthermore, a procedure called disallowedOperation shows how to handle unauthorized operations by consistently reversing.assert() ensure savings remain consistent after transactions.
### Author
Akash Singh
