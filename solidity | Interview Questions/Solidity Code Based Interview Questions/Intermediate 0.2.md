Solidity Technical Interview Questions: Intermediate Level

1. Question: Implement a modifier onlyOwner that restricts a function's execution to the contract owner.

        modifier onlyOwner() {
            
            require(msg.sender == owner, "Only the owner can call this");
            
            _;
        }

2. Question: Write a Solidity function that returns the balance of a specific address.

        function getAddressBalance(address account) public view returns (uint256) {
            
            return account.balance;
        }

3. Question: Develop a Solidity function to transfer ERC-20 tokens from the contract to a recipient.

        function transferTokens(address tokenAddress, address recipient, uint256 amount) public {
           
            ERC20Token(tokenAddress).transfer(recipient, amount);
        }

4. Question: Create a Solidity function that retrieves the name and symbol of an ERC-20 token.

        function getTokenInfo(address tokenAddress) public view returns (string memory, string memory) {
         
            ERC20Token token = ERC20Token(tokenAddress);
         
            return (token.name(), token.symbol());
        }

5. Question: Write a Solidity function that returns the current block's timestamp.

        function getCurrentTimestamp() public view returns (uint256) {
           
            return block.timestamp;
        }

6. Question: Develop a Solidity function to send Ether to multiple addresses with equal distribution.

        function distributeEther(address[] memory recipients, uint256 amount) public {
            
            require(address(this).balance >= amount * recipients.length, "Insufficient balance");
            
            for (uint256 i = 0; i < recipients.length; i++) {
            
                payable(recipients[i]).transfer(amount);
            
            }
        }

7. Question: Create a Solidity function that returns the hash of a given string.

        function getStringHash(string memory input) public pure returns (bytes32) {
         
            return keccak256(abi.encodePacked(input));
        }

8. Question: Write a Solidity function that generates a random number using block information.

        function getRandomNumber() public view returns (uint256) {
            
            return uint256(keccak256(abi.encodePacked(block.difficulty, 
            
            block.timestamp, block.coinbase)));
        }

9. Question: Develop a Solidity function that calculates the average of an array of integers.

        function calculateAverage(uint256[] memory numbers) public pure returns (uint256) {
            
            uint256 sum = 0;
            
            for (uint256 i = 0; i < numbers.length; i++) {
            
                sum += numbers[i];
            }
           
            return sum / numbers.length;
        }

10. Question: Create a Solidity function that returns the current Ethereum network's chain ID.

        function getChainId() public view returns (uint256) {
            
            return block.chainid;
        }