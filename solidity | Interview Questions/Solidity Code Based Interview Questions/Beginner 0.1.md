# Solidity Technical Interview Questions: Beginner Level -

1. Question: Write a Solidity function to add two numbers and return the result.

        function addNumbers(uint256 a, uint256 b) public pure returns (uint256) {
            return a + b;
        }

2. Question: Create a Solidity function to set a state variable name to a given value.

        contract NameContract {
            
            string public name;

            function setName(string memory newName) public {
               
                name = newName;
            }
        }

3. Question: Write a Solidity function that returns the balance of the contract.

        function getContractBalance() public view returns (uint256) {
            
            return address(this).balance;
        }

4. Question: Develop a Solidity function to transfer Ether from the contract to a specified address.

        function transferFunds(address payable recipient, uint256 amount) public {
            
            require(address(this).balance >= amount, "Insufficient balance");

            recipient.transfer(amount);
        }

5. Question: Create a Solidity function that increments a state variable counter whenever it's called.

        contract CounterContract {
            
            uint256 public counter;
            
            function incrementCounter() public {
                
                counter++;
            }
        }

6. Question: Write a Solidity function to return the length of a given array.

        function getArrayLength(uint256[] memory arr) public pure returns (uint256) {
            
            return arr.length;
        }

7. Question: Develop a Solidity function to concatenate two strings and return the result.

        function concatenateStrings(string memory a, string memory b) public pure returns (string memory) {
            
            return string(abi.encodePacked(a, b));
        }

8. Question: Create a Solidity function that checks if a given address is the same as the contract creator.

        function isContractCreator(address creator) public view returns (bool) {
            
            return msg.sender == creator;
        }

9. Question: Write a Solidity function that returns the square root of a given number.

        function sqrt(uint256 x) public pure returns (uint256) {
            
            return x**0.5;
        }

10. Question: Develop a Solidity function that transfers ownership of the contract to a new address.

        contract Ownable {
            
            address public owner;
            
            constructor() {
               
                owner = msg.sender;
            }
            
            function transferOwnership(address newOwner) public {
               
                require(msg.sender == owner, "Only the owner can transfer ownership");
               
                owner = newOwner;
            }
        }