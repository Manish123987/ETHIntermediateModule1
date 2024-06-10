# Ether Vault Project

## Description 

Ether Vault is a secure Ethereum wallet contract that allows users to deposit and withdraw Ether safely. It features functionalities for users to deposit Ether, withdraw Ether, and for the contract owner to send Ether to any specified address. The contract ensures the balance integrity using assertions and provides safe fund management through require checks and safe transfer methods.

## ## Getting Started

### Executing program

To run this program, you can use Remix, an online Solidity IDE. To get started, go to the Remix website at https://remix.ethereum.org/.

Once you are on the Remix website, create a new file by clicking on the "+" icon in the left-hand sidebar. Save the file with a .sol extension (e.g., myToken.sol). Copy and paste the following code into the file:

```javascript
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract ExampleContract {
    address private owner;
    uint public balance;
    mapping(address => uint) public balances;
    uint public totalSupply;

    constructor() {
        owner = msg.sender;
    }

    function depositEther() public payable {
        balances[msg.sender] += msg.value;
        totalSupply += msg.value;
        assert(address(this).balance >= totalSupply);
    }

    function withdrawEther(uint amount) public {
        require(balances[msg.sender] >= amount, "Insufficient balance");
        balances[msg.sender] -= amount;
        if (!payable(msg.sender).send(amount)) {
            revert("Failed to send funds");
        }
    }

    function sendEther(address payable addr) public payable {
        require(msg.value > 0, "Amount must be greater than 0");
        require(msg.sender == owner, "Only the owner can send ether");

        uint balanceBeforeTransfer = address(this).balance;
        (bool success, ) = addr.call{value: msg.value}("");
        require(success, "Transfer failed");

        assert(address(this).balance == balanceBeforeTransfer - msg.value);
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
