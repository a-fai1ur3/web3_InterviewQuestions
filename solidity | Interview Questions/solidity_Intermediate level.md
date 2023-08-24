# Solidity Interview Questions: Intermediate Level

1. What is the purpose of the view and pure keywords?
* Answer: view is used for functions that do not modify state, and pure is used for functions that do not read or modify state. They enable better optimization and gas cost estimation.

2. How is gas consumption managed in Solidity?
* Answer: Gas is used to measure computation and storage costs on the Ethereum network. Proper coding practices and avoiding unnecessary operations help manage gas consumption.

3. Explain the concept of inheritance in Solidity.
* Answer: Inheritance allows a contract to inherit properties and methods from another contract. It enables code reuse and structuring contracts in a modular way.

4. What are modifiers? How do they enhance function behavior?
* Answer: Modifiers are reusable code snippets that can be applied to functions to modify their behavior. They are often used for access control and code reuse.

5. How does the msg.sender and msg.value work?
* Answer: msg.sender refers to the address that called the current function, and msg.value contains the amount of Ether sent in the transaction.

6. What is the difference between memory and storage?
* Answer: memory is used for temporary data storage within function execution, while storage is used to store data between function calls and persists across transactions.

7. How can you prevent integer overflow and underflow vulnerabilities?
* Answer: Using appropriate data types (uint256), performing range checks, and using libraries like OpenZeppelin can help prevent such vulnerabilities.

8. What is the purpose of the selfdestruct function?
* Answer: The selfdestruct function allows a contract to destroy itself and send remaining Ether to a specified address. It's commonly used for upgrading contracts or returning funds.

9. What are libraries in Solidity?
* Answer: Libraries are reusable pieces of code that can be linked to contracts. They enable sharing code and reducing deployment costs.

10. How can you secure your Solidity smart contracts?
* Answer: Use secure coding practices, perform thorough testing, use well-audited libraries, implement access controls, and consider utilizing formal verification tools.