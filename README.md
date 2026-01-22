# practise-smart-contract-ethereum


## Maping Practice
This is a practice mapping from an address to string

```soilidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.26;

contract MappingPractice {

    //Declare a state variable to save the value 
    mapping ( address => string) private students;

    //Declare a function to set value for students
    function setStudent (address _addr, string memory _name) public {
        students[_addr] = _name;
    }

    //Declare a function to get the value from state variable
    function getStudent (address _addr) public view returns (string memory) {
    return students[_addr];
    }

    //Drclare a function to remove the students
    function removeStudent (address _addr) public {
        delete students[_addr];
    }

}

```


First smart contract practice

``` solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.26;

// This is the contract to hash strings using keccak256
contract YongHashingString {
    // declare state varible
    bytes32 private yongString;
    // hashing the string
    function hashing (string memory _str) public {
        yongString = keccak256(bytes(_str));
    }
    //get the digest of the hasing process
    function getDigest () public view returns (bytes32) {
        return yongString;
    }    
}

```
