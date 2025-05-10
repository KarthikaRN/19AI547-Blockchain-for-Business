
### Experiment 1: Decentralized Certificate Verification
## Name: M Sathish kumar
## Reg no: 212222040150
## Aim:
  To develop a smart contract for issuing and verifying academic certificates on Ethereum, preventing forgery and ensuring authenticity.
## Algorithm:
1. Define a smart contract to issue certificates, storing student details and a unique certificate hash.  
2. Restrict certificate issuance to authorized institutions using address-based access control.  
3. Store only the certificate hash on-chain to protect privacy and reduce gas costs.  
4. Provide a verification function to compare submitted hashes with on-chain records.  
5. Use Ethereum’s immutable ledger to ensure certificates remain tamper-proof and authentic.
## Program:
```
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.20;
contract CertificateVerification {
address public university;
mapping(bytes32 => bool) public certificates; // Store hashed certificates
event CertificateIssued(bytes32 indexed certHash);
constructor() {
university = msg.sender; // University deploys the contract
}
function issueCertificate(string memory studentName, string memory degree, uint256 year) public {
require(msg.sender == university, "Only university can issue certificates");
bytes32 certHash = keccak256(abi.encodePacked(studentName, degree, year));
certificates[certHash] = true;
emit CertificateIssued(certHash);
}
function verifyCertificate(string memory studentName, string memory degree, uint256 year) public view returns (bool) {
bytes32 certHash = keccak256(abi.encodePacked(studentName, degree, year));
return certificates[certHash];
}
}
```
# Expected Output
![Screenshot 2025-04-16 091254](https://github.com/user-attachments/assets/de5d4b62-e608-411e-8404-dedb0c6cdb2a)

```
1. Ensures authenticity of academic certificates through blockchain’s immutability.  
2. Prevents forgery and tampering with certificates using cryptographic verification.  
3. Enables instant, transparent, and trustless verification by employers and institutions.  
4. Reduces administrative overhead and paperwork in certificate issuance and validation.  
5. Provides a permanent, decentralized record accessible from anywhere.
```
# Result:
A smart contract on Ethereum ensures secure, tamper-proof, and globally verifiable academic certificates.
