# DecentraVote: A Decentralized Voting System Using Ethereum Blockchain

DecentraVote is a secure, transparent, and innovative voting platform that leverages the Ethereum blockchain to revolutionize how elections are conducted. By utilizing blockchain technology, DecentraVote ensures tamper-proof voting records, enabling voters to cast their ballots remotely while maintaining anonymity and preventing fraud.
![Screenshot 2024-12-16 201113](https://github.com/user-attachments/assets/3de049fd-4a32-4320-a51e-46361df64d42)

---

## Overview

DecentraVote addresses the challenges faced in traditional voting systems by eliminating intermediaries and offering a trustless, transparent voting process. It implements JWT for secure voter authentication, ensures decentralized data storage on Ethereum, and provides an intuitive user experience for both voters and administrators.

### Key Features
- **Secure Authentication**: Implements JSON Web Tokens (JWT) for voter authentication and role-based access.
- **Blockchain-Based Transparency**: Utilizes Ethereum’s blockchain to maintain an immutable and transparent ledger of votes.
- **Decentralization**: Removes the need for intermediaries, ensuring a trustless voting process.
- **Admin Management**: Provides an admin panel to manage candidates, set voting dates, and monitor results in real-time.
- **User-Friendly Interface**: Intuitive UI/UX for voters to cast their votes securely and view candidate information.

---


## Requirements

To set up and run DecentraVote, you will need the following tools:

- **Node.js**: Version 18.14.0 or later
- **Metamask**: Browser extension for managing Ethereum wallets
- **Python**: Version 3.9 or later
- **FastAPI**: Python web framework for API development
- **MySQL Database**: Running on port 3306
- **Ganache**: Local blockchain emulator

---

## Installation Guide

Follow these steps to set up the DecentraVote platform:

### 1. Clone the Repository
Open a terminal and run:
```bash
git clone https://github.com/saadhussain01306/DecentraVote.git
```

### 2. Set Up Ganache
- Download and install [Ganache](https://trufflesuite.com/ganache/).
- Create a workspace named `development`.
- In the "Truffle Projects" section, add `truffle-config.js` by clicking the "ADD PROJECT" button.

### 3. Set Up Metamask
- Download the [Metamask](https://metamask.io/download/) browser extension.
- Create a wallet (if you don’t already have one).
- Import accounts from Ganache into Metamask.
- Add a network to Metamask with the following details:
  - **Network Name**: Localhost 7575
  - **RPC URL**: `http://localhost:7545`
  - **Chain ID**: 1337
  - **Currency Symbol**: ETH

### 4. Set Up the Database
- Open MySQL and create a database named `voter_db`.
- Create a table named `voters` with the following structure:

```sql
CREATE TABLE voters (
    voter_id VARCHAR(36) PRIMARY KEY NOT NULL,
    role ENUM('admin', 'user') NOT NULL,
    password VARCHAR(255) NOT NULL
);
```
        +--------------------------------------+-------+-----------+
        | voter_id                             | role  | password  |
        +--------------------------------------+-------+-----------+
        |                                      |       |           |
        +--------------------------------------+-------+-----------+

#### Update the `.env` File
If you are using MySQL Workbench, update the `.env` file in the `Database_API` folder as follows:
```env
MYSQL_USER="root"
MYSQL_PASSWORD="your_password"
MYSQL_HOST="127.0.0.1"
MYSQL_DB="voter_db"
SECRET_KEY="any random key"
```

Add sample values to the table as required.

### 5. Install Dependencies

#### Node.js
Install Truffle globally:
```bash
npm install -g truffle
```
Navigate to the project directory and install Node.js dependencies:
```bash
npm install
```

#### Python
Navigate to the `Database_API` folder and install Python dependencies:
```bash
pip install fastapi mysql-connector-python pydantic python-dotenv uvicorn uvicorn[standard] PyJWT
```

---

## Running the Application

### 1. Compile Smart Contracts
Open a terminal in the project root directory and run:
```bash
truffle console
compile
exit
```

### 2. Bundle JavaScript Files
Run the following command to bundle `app.js`:
```bash
browserify ./src/js/app.js -o ./src/dist/app.bundle.js
```

### 3. Start the Node.js Server
Run the following command:
```bash
node index.js
```

### 4. Start the Database API
Navigate to the `Database_API` folder in another terminal and run:
```bash
uvicorn main:app --reload --host 127.0.0.1
```

### 5. Deploy Smart Contracts
Run the following command to deploy the smart contracts to the local blockchain:
```bash
truffle migrate
```

### 6. Access the Application
Open your browser and navigate to:
```
http://localhost:8080/
```

---

## Code Structure

```plaintext
## Code Structure

    ├── blockchain-voting-dapp            # Root directory of the project.
        ├── build                         # Directory containing compiled contract artifacts.
        |   └── contracts                 
        |       ├── Migrations.json       
        |       └── Voting.json           
        ├── contracts                     # Directory containing smart contract source code.
        |   ├── 2_deploy_contracts.js     
        |   ├── Migrations.sol            
        |   └── Voting.sol                
        ├── Database_API                  # API code for database communication.
        |   └── main.py                   
        ├── migrations                    # Ethereum contract deployment scripts.
        |   └── 1_initial_migration.js    
        ├── node_modules                  # Node.js modules and dependencies.
        ├── public                        # Public assets like favicon.
        |   └── favicon.ico               
        ├── src                           
        |   ├── assets                    # Project images.
        |   |   └── eth5.jpg              
        |   ├── css                       # CSS stylesheets.
        |   |   ├── admin.css             
        |   |   ├── index.css             
        |   |   └── login.css             
        |   ├── dist                      # Compiled JavaScript bundles.
        |   |   ├── app.bundle.js         
        |   |   └── login.bundle.js       
        |   ├── html                      # HTML templates.
        |   |   ├── admin.html            
        |   |   ├── index.html            
        |   |   └── login.html            
        |   └── js                        # JavaScript logic files.
        |       ├── app.js                
        |       └── login.js              
        ├── index.js                      # Main entry point for Node.js application.
        ├── package.json                  # Node.js package configuration.
        ├── package-lock.json             # Lockfile for package dependencies.
        ├── README.md                     # Project documentation.
        └── truffle-config.js                    # Truffle configuration file.
```

---

## Project SnapShots:

![Screenshot 2024-12-16 201113](https://github.com/user-attachments/assets/a3867b45-667d-463e-89d3-a7f68e939ae4)

![Screenshot 2024-12-16 201145](https://github.com/user-attachments/assets/9021baea-a2bb-4726-b5ba-7d1769506ad8)

![Screenshot 2024-12-16 201311](https://github.com/user-attachments/assets/20b72263-a139-4c20-a97e-4bec1791f5af)

![Screenshot 2024-12-16 201327](https://github.com/user-attachments/assets/df30b48c-05cf-43bd-be7e-fbaa3e9e183c)

![Screenshot 2024-12-16 201423](https://github.com/user-attachments/assets/6303047c-1658-4a8e-8af2-ac70a5e1efa3)

![Screenshot 2024-12-16 201514](https://github.com/user-attachments/assets/ee22e72e-df9e-409b-8b07-c59f2ffb7d44)

![Screenshot 2024-12-16 201608](https://github.com/user-attachments/assets/2aff543d-ef79-41f3-9ec2-eab94561af19)

---

## License

This project is licensed under the MIT License. 

---

## Acknowledgments

This project was inspired by the potential of blockchain technology to transform traditional voting systems. Special thanks to the Ethereum and FastAPI communities for their invaluable tools and resources.

---

If you found this project helpful, please give it a 🌟 on GitHub!

Thank you for exploring DecentraVote! 😊
