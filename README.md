# Zero-Knowledge Proofs (ZKP) Project

This repository contains a Zero-Knowledge Proof (ZKP) implementation using **Circom** and **SnarkJS**. The project aims to provide a secure and privacy-preserving solution for identity verification, targeting the banking and cryptocurrency sectors.

## Table of Contents

- [Introduction](#introduction)
- [Prerequisites](#prerequisites)
- [Installation](#installation)
- [Project Structure](#project-structure)
- [Usage](#usage)
- [Commands](#commands)
- [License](#license)
- [Contributing](#contributing)
- [Contact](#contact)

## Introduction

Zero-Knowledge Proofs allow one party to prove to another that a statement is true without revealing any information beyond the validity of the statement itself. This project demonstrates how to use ZKPs for identity verification while preserving user privacy.

## Prerequisites

Before you begin, ensure you have the following installed:

- [Node.js](https://nodejs.org/) (version 12 or higher)
- [npm](https://www.npmjs.com/) (Node package manager)
- [Circom](https://docs.circom.io/gettingstarted/installation/)
- [SnarkJS](https://github.com/iden3/snarkjs)

## Installation

1. Clone this repository:
   ```bash
   git clone https://github.com/tekinity-ae/zkp-app.git
   cd zkp-app

## Install dependencies:
npm install

## Project Structure
```
zkp-app/
├── circom/
│   ├── identity.circom        # Circom circuit for identity verification
│   ├── identity.r1cs          # R1CS file generated from the circuit
│   ├── identity_js/            # Contains generated JS files
├── inputs/                    # Directory for input JSON files
│   ├── input.json              # Sample input file
├── outputs/                   # Directory for output files
│   ├── witness.wtns            # Witness file generated
│   ├── proof.json              # Generated proof file
│   ├── public.json             # Public input data
├── README.md                   # Project documentation
```
## Usage

To generate a Zero-Knowledge Proof, follow these steps:

1- Setup the Powers of Tau:
``` 
    snarkjs ptn bn128 22 powersoftau_0000.ptau
    snarkjs ptc powersoftau_0000.ptau new_powersoftau.ptau
```
2- Compile the Circuit:
```
snarkjs g16s identity.r1cs new_powersoftau.ptau circuit_0000.zkey
```
3- Calculate the Witness:
```
snarkjs wc identity_js/identity.wasm inputs/input.json witness.wtns
```
4- Generate the Proof:
```
snarkjs g16p circuit_0000.zkey witness.wtns proof.json public.json
```
5- Verify the Proof:
```
snarkjs g16v verification_key.json public.json proof.json
```
## Commands

Here are some useful commands you may need during development:

1- Generate Witness:
```
    snarkjs wc identity_js/identity.wasm inputs/input.json witness.wtns
```
2- Print R1CS Statistics:
```
snarkjs ri identity.r1cs
```
3- Export Verification Key:
```
snarkjs zkev circuit_final.zkey verification_key.json
```

## License

This project is licensed under the MIT License. See the LICENSE file for details.

## Contributing

Contributions are welcome! Please feel free to submit a pull request or open an issue for any suggestions or improvements.

## Contact

For any inquiries or questions, please reach out to imtiazwaraich@hotmail.com.
