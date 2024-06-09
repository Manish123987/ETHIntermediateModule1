# ETH + AVAX PROOF: Intermediate EVM Course Module - 1

This module introduces the concepts of functions and error handling in Solidity, focusing on their application in Ethereum and Avalanche smart contract development.

## Description 

It is designed to provide developers with a comprehensive understanding of essential programming constructs in Solidity, focusing on functions and error handling mechanisms. This module equips learners with the skills needed to write more secure and efficient smart contracts on the Ethereum and Avalanche blockchains.

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

    constructor() public {
        owner = msg.sender;
    }

    function sendEther(address payable addr) public payable {
        require(msg.value > 0, "Amount must be greater than 0");
        require(msg.sender == owner, "Only the owner can send ether");

        uint balanceBeforeTransfer = address(this).balance;
        (bool success, ) = addr.call.value(msg.value)(""); 
        require(success);

        assert(address(this).balance == balanceBeforeTransfer - msg.value);
    }

    function withdrawEther(uint amount) public {
        assert(balances[msg.sender] >= amount);
        balances[msg.sender] -= amount;
        payable(msg.sender).transfer(amount);
    }

    function depositEther() public payable {
        balances[msg.sender] += msg.value;
        totalSupply += msg.value;
        assert(address(this).balance >= totalSupply);
    }  } 

To compile the code, click on the "Solidity Compiler" tab in the left-hand sidebar. Make sure the "Compiler" option is set to "0.8.18" (or another compatible version), and then click on the "Compile MyToken.sol" button.

Once the code is compiled, you can deploy the contract by clicking on the "Deploy & Run Transactions" tab in the left-hand sidebar. Select the "MyToken" contract from the dropdown menu, and then click on the "Deploy" button.

## Help
For any assistance or queries, feel free to reach out to the contract author via [email](rajwalmanish91@gmail.com).


## Authors
Manish Singh Rajwal


## License

This project is licensed under the MIT License - see the LICENSE.md file for details
