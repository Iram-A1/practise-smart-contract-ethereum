# Practise-smart-contract-ethereum

### Struct working with Array


```solidity

// SPDX-License-Identifier: MIT
pragma solidity ^0.8.26;

contract StructArrayPractice {

    // Declare a structure for student
    struct Student {
        string name;
        bool isRegistered;
    }

    // Declare an array for the registered students
    Student[] private students;

    // Declare an internal function to register a student into the array
    function _registerStudent (string memory _name) internal {
        students.push(Student({
            name: _name,
            isRegistered: true
        }));
    }

    // Declare an external function to register for external account
    function registerStudent (string calldata _name) external {
        _registerStudent(_name);
    }

    // Declare a function to get a student by using the student index
    function getStudentById(uint256 _id) external view returns (string memory, bool) {
        return (students[_id].name, students[_id].isRegistered);
    }

    // Declare a function to get all the registered students
    function getAllStudents() external view returns (Student[] memory) {
        return students;
    }

    // Declare a funtion to remove/pop up the last student
    function popUplastStudent() external {
        students.pop();
    }

    // Declare a funtioon to return the length of the students' array
    function getArrayLength() external view returns (uint256) {
        return students.length;
    }
}


```

## Mapping from address to struct

```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.26;

contract MappingStructPractice {

// Declare a student structure having 3 attributes
struct Student {
    string name;
    string email;
    bool isAttended;
}

// Declare a mapping from address to Struct Students
mapping (address => Student) private students;

// Declare a function to set student attendance
function setStudentAttendance(address _addr, string memory _name, string memory _email, bool _isAttended) public {
    students[_addr] = Student ( {
        name: _name,
        email: _email,
        isAttended: _isAttended
    });
    }    

    // Declare a function to get students attendance information
    function getStudentAttendance(address _addr) 
    public view returns (string memory, string memory, bool) {
        return (students[_addr].name,
                students[_addr].email,
                students[_addr].isAttended
        );
    }

    // Declare a function to toggle the student attandance
    function toggleStudentAttendance (address _addr) public {
        students[_addr].isAttended = !students[_addr].isAttended;
    }

    // Declare a function to update student email
    function modifyStudentEmail (address _addr, string memory _email) public {
        students[_addr].email = _email;
    }
}


```

## Nested Mapping Practice

```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.26;

contract NestedMappingPractice {

    // Declare a state variable as nested mapping datatype
    mapping (address => mapping (string => bool)) private attendanceSheet;

    // Declare a funciton to set values for a student
    function setAttendance (address _addr, string memory _name, bool _isPresent) public {
        attendanceSheet[_addr][_name] = _isPresent;
    }

    // Declare a function to get the value for a student
    function getAttendance (address _addr, string memory _name) public view returns (bool) {
        return attendanceSheet[_addr][_name];
    }

    // Declare a function to toggle the value for a student
    function toggleAttendance (address _addr, string memory _name) public {
        attendanceSheet[_addr][_name] = !attendanceSheet[_addr][_name];
    }
}

```

## Mapping Practice
This is a practice mapping from an address to string

```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.26;

contract MappingPractice {

    // Declare a state variable to save the value
    mapping (address => string) private students;

    // Declare a function to set value for a student
    function setStudent (address _addr, string memory _name) public {
        students[_addr] = _name;
    }

    // Declare a function to show/get the value from state varialbe
    function getStudent (address _addr) public view returns (string memory) {
        return students[_addr];
    }

    // Declare a function to remove the student
    function removeStudent (address _addr) public {
        delete students[_addr];
    }
}

```


## First smart contract practice

``` solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.26;

// This is the contract to hash strings using keccak256
contract iramHashingString {
    // declare state varible
    bytes32 private iramString;
    // hashing the string
    function hashing (string memory _str) public {
        iramString = keccak256(bytes(_str));
    }
    //get the digest of the hasing process
    function getDigest () public view returns (bytes32) {
        return iramString;
    }    
}

```
