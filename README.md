# ETH + AVAX PROOF: Intermediate EVM Course Module - 1

This module introduces the concepts of functions and error handling in Solidity, focusing on their application in Ethereum and Avalanche smart contract development.

## Description 

It is designed to provide developers with a comprehensive understanding of essential programming constructs in Solidity, focusing on functions and error handling mechanisms. This module equips learners with the skills needed to write more secure and efficient smart contracts on the Ethereum and Avalanche blockchains.

## ## Getting Started

### Executing program

To run this program, you can use Remix, an online Solidity IDE. To get started, go to the Remix website at https://remix.ethereum.org/.

Once you are on the Remix website, create a new file by clicking on the "+" icon in the left-hand sidebar. Save the file with a .sol extension (e.g., myToken.sol). Copy and paste the following code into the file:

// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract VariableManager {
    uint public uintVar;
    string public stringVar;
    bool public boolVar;
    address public addressVar;

    function setUintVar(uint _uintVar) public returns (uint) {
        require(msg.sender == address(0x0000000000000000000000000000000000000001), "Only the owner can set the uint variable");
        uintVar = _uintVar;
        return uintVar;
    }

    function getUintVar() public view returns (uint) {
        return uintVar;
    }

    function setStringVar(string memory _stringVar) public returns (string memory) {
        require(bytes(_stringVar).length > 0, "String cannot be empty");
        stringVar = _stringVar;
        return stringVar;
    }

    function getStringVar() public view returns (string memory) {
        return stringVar;
    }

    function setBoolVar(bool _boolVar) public returns (bool) {
        if (_boolVar == true) {
            revert("Bool variable cannot be set to true");
        }
        boolVar = _boolVar;
        return boolVar;
    }

    function getBoolVar() public view returns (bool) {
        return boolVar;
    }

    function setAddressVar(address _addressVar) public returns (address) {
        require(_addressVar != address(0), "Address cannot be zero");
        addressVar = _addressVar;
        return addressVar;
    }

    function getAddressVar() public view returns (address) {
        return addressVar;
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
