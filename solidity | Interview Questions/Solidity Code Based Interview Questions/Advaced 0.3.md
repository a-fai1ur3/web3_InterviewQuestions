Solidity Technical Interview Questions: Advanced Level

1. Question: Implement a function that allows users to create a new instance of a specified contract.

        function createContractInstance(address contractAddress) public returns (address) {
            return address(new ContractInstance(contractAddress));
        }

2. Question: Write a Solidity function that implements a basic voting mechanism with unique addresses.

        contract Voting {
            mapping(address => bool) public hasVoted;
            uint256 public yesVotes;
            uint256 public noVotes;
            
            function vote(bool choice) public {
                require(!hasVoted[msg.sender], "You've already voted");
                hasVoted[msg.sender] = true;
                if (choice) {
                    yesVotes++;
                } else {
                    noVotes++;
                }
            }
        }

3. Question: Develop a Solidity function that creates a new child contract and associates it with the caller.

        contract Parent {
            mapping(address => address) public children;
            
            function createChild() public {
                address child = address(new Child(msg.sender));
                children[msg.sender] = child;
            }
        }

        contract Child {
            address public parent;
            
            constructor(address _parent) {
                parent = _parent;
            }
        }

4. Question: Create a Solidity function that performs a batch transfer of ERC-20 tokens.

        function batchTransferTokens(address tokenAddress, address[] memory recipients, uint256[] memory amounts) public {
            require(recipients.length == amounts.length, "Invalid input lengths");
            ERC20Token token = ERC20Token(tokenAddress);
            for (uint256 i = 0; i < recipients.length; i++) {
                token.transfer(recipients[i], amounts[i]);
            }
        }
5. Question: Write a Solidity function that implements a simple auction system.

        contract Auction {
            address public highestBidder;
            uint256 public highestBid;
            mapping(address => uint256) public bids;
            
            function placeBid() public payable {
                require(msg.value > highestBid, "Bid too low");
                if (highestBidder != address(0)) {
                    bids[highestBidder] += highestBid;
                }
                highestBidder = msg.sender;
                highestBid = msg.value;
            }
            
            function withdrawBid() public {
                require(msg.sender != highestBidder, "You're the highest bidder");
                uint256 amount = bids[msg.sender];
                bids[msg.sender] = 0;
                payable(msg.sender).transfer(amount);
            }
            
            function finalizeAuction() public {
                require(msg.sender == owner, "Only the owner can finalize");
                payable(owner).transfer(highestBid);
            }
        }

6. Question: Develop a Solidity function that implements a time-locked wallet, releasing funds after a specified period.

        contract TimeLockedWallet {
            address public beneficiary;
            uint256 public unlockTime;
            
            constructor(address _beneficiary, uint256 _unlockTime) {
                beneficiary = _beneficiary;
                unlockTime = _unlockTime;
            }
            
            function withdraw() public {
                require(msg.sender == beneficiary, "Only the beneficiary can withdraw");
                require(block.timestamp >= unlockTime, "Funds are locked");
                payable(beneficiary).transfer(address(this).balance);
            }
        }

7. Question: Create a Solidity function that implements a basic multi-signature wallet.

        contract MultiSigWallet {
            address[] public owners;
            mapping(address => bool) public isOwner;
            uint256 public requiredSignatures;
            
            constructor(address[] memory _owners, uint256 _requiredSignatures) {
                owners = _owners;
                requiredSignatures = _requiredSignatures;
                for (uint256 i = 0; i < _owners.length; i++) {
                    isOwner[_owners[i]] = true;
                }
            }
            
            function executeTransaction(address payable to, uint256 amount, bytes memory data) public {
                require(isOwner[msg.sender], "Not an owner");
                // Implement logic for executing a transaction with required signatures
            }
        }

8. Question: Write a Solidity function that implements a simple decentralized identity system.

        contract Identity {
            mapping(address => bool) public isVerified;
            
            function verifyIdentity(address user) public {
                require(msg.sender == owner || isVerified[msg.sender], "Not authorized");
                isVerified[user] = true;
            }
        }

9. Question: Develop a Solidity function that implements a basic subscription service, allowing users to subscribe and unsubscribe.

        contract Subscription {
            mapping(address => bool) public isSubscribed;
            uint256 public subscriptionFee;
            
            function subscribe() public payable {
                require(msg.value >= subscriptionFee, "Insufficient payment");
                isSubscribed[msg.sender] = true;
            }
            
            function unsubscribe() public {
                isSubscribed[msg.sender] = false;
                payable(msg.sender).transfer(subscriptionFee);
            }
        }

10. Question: Create a Solidity function that implements a simple decentralized marketplace for buying and selling goods.

        contract Marketplace {
            struct Product {
                address seller;
                string name;
                uint256 price;
            }
            
            mapping(uint256 => Product) public products;
            uint256 public productCount;
            
            function addProduct(string memory name, uint256 price) public {
                products[productCount] = Product(msg.sender, name, price);
                productCount++;
            }
            
            function buyProduct(uint256 productId) public payable {
                Product memory product = products[productId];
                require(msg.value >= product.price, "Insufficient payment");
                payable(product.seller).transfer(product.price);
                // Implement logic for transferring ownership
            }
        }