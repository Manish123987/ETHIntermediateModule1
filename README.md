# SimpleBank

## Description 

SimpleBank is a decentralized smart contract implementation of a basic banking system on the Ethereum blockchain. This contract allows users to deposit, withdraw, and transfer Ether securely while demonstrating proper error handling using Solidity's require(), assert(), and revert() statements.

## ## Getting Started

### Executing program

To run this program, you can use Remix, an online Solidity IDE. To get started, go to the Remix website at https://remix.ethereum.org/.

Once you are on the Remix website, create a new file by clicking on the "+" icon in the left-hand sidebar. Save the file with a .sol extension (e.g., myToken.sol). Copy and paste the following code into the file:

```javascript
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract SimpleBank {
    mapping(address => uint256) private balances;
    address public owner;

    constructor() {
        owner = msg.sender;
    }

    function deposit() public payable {
        require(msg.value > 0, "Deposit amount must be greater than zero");
        balances[msg.sender] += msg.value;
    }

    function withdraw(uint256 amount) public {
        require(balances[msg.sender] >= amount, "Insufficient balance");

        uint256 initialBalance = balances[msg.sender];
        balances[msg.sender] -= amount;
        payable(msg.sender).transfer(amount);

        assert(balances[msg.sender] == initialBalance - amount);
    }

    function transfer(address recipient, uint256 amount) public {
        require(recipient != address(0), "Recipient address cannot be zero");
        require(balances[msg.sender] >= amount, "Insufficient balance");

        uint256 senderInitialBalance = balances[msg.sender];
        uint256 recipientInitialBalance = balances[recipient];
        
        balances[msg.sender] -= amount;
        balances[recipient] += amount;

        assert(balances[msg.sender] == senderInitialBalance - amount);
        assert(balances[recipient] == recipientInitialBalance + amount);
    }

    function checkBalance() public view returns (uint256) {
        return balances[msg.sender];
    }

    function emergencyWithdraw(uint256 amount) public {
        if (msg.sender != owner) {
            revert("Only the owner can perform emergency withdrawal");
        }
        require(address(this).balance >= amount, "Insufficient contract balance");

        payable(owner).transfer(amount);
    }
}

To compile the code, click on the "Solidity Compiler" tab in the left-hand sidebar. Make sure the "Compiler" option is set to "0.8.18" (or another compatible version), and then click on the "Compile MyToken.sol" button.

Once the code is compiled, you can deploy the contract by clicking on the "Deploy & Run Transactions" tab in the left-hand sidebar. Select the "MyToken" contract from the dropdown menu, and then click on the "Deploy" button.

## Help
For any assistance or queries, feel free to reach out to the contract author via [email](rajwalmanish91@gmail.com).


## Authors
Manish Singh Rajwal


## License

This project is licensed under the MIT License - see the LICENSE.md file for details
