# 2025_GP_29: TrustDose
## Blockchain-Based Prescription and Medication Delivery System  

**TrustDose** is a blockchain-based platform designed to enhance transparency, security, and efficiency in prescription management and medication delivery. The system connects doctors, pharmacists, logistics providers, and patients through a secure and decentralized ledger, ensuring that every stage of the medication lifecycle—from prescription issuance to patient receipt—is accurately tracked and tamper-proof.  

By integrating **IoT sensors**, TrustDose provides real-time monitoring for temperature-sensitive medications such as insulin and vaccines, ensuring they are stored and delivered under optimal conditions.  

---

## Technology Used

- **Blockchain Technology (Ethereum):**  
  Ensures the immutability and security of prescription and delivery records. Every step in the medication lifecycle — from prescription issuance by the doctor, validation by the pharmacist, to delivery confirmation — is recorded on the blockchain, providing full transparency and traceability.

- **Smart Contracts (Solidity):**  
  Automates critical processes such as prescription validation, delivery status updates, and temperature condition checks. These contracts enforce predefined rules to prevent unauthorized dispensing and ensure safe delivery of temperature-sensitive medications.

- **Truffle and Ganache:**  
  Used for developing, testing, and deploying smart contracts in a local blockchain environment, enabling rapid prototyping and validation of the system logic.

- **Web3.js / Ethers.js:**  
  Bridges the interaction between the frontend application and the blockchain, allowing users (doctors, pharmacists, and patients) to securely read and write data on the decentralized ledger.

- **Frontend (ReactJS + Tailwind CSS):**  
  Provides a user-friendly, responsive interface for patients, doctors, and pharmacists to manage prescriptions and track delivery status in real time.

- **Backend (Node.js):**  
  Serves as middleware to handle API requests, integrate with blockchain components, and manage interactions with IoT devices.

- **IoT Integration (Arduino, ESP32, DHT11 Sensors):**  
  Monitors temperature and environmental conditions during the transportation of sensitive medications, sending real-time data to the blockchain for immutable storage and alert generation when unsafe conditions are detected.

- **Development Tools:**  
  - **MetaMask:** For secure authentication and blockchain account management.  
  - **Visual Studio Code:** Main IDE for development.  
  - **GitHub:** Version control and collaborative code management.  
  - **Jira:** Project management and sprint planning.
 
    ### Setting up Local Development #### Step 1: Installation and Setup 1. **VSCode**: Download from [VSCode website](https://code.visualstudio.com/). 2. **Node.js**: Download the latest version from [Node.js website](https://nodejs.org/). After installation, verify the version by running the following command in the terminal:
bash
    node -v
3. **Git**: Download from [Git website](https://git-scm.com/downloads). Verify the version by running the following command:
bash
    git --version
4. **Ganache**: Download from [Ganache official website](https://www.trufflesuite.com/ganache). 5. **MetaMask**: Install MetaMask as a browser extension from the [Chrome Web Store](https://chrome.google.com/webstore/category/extensions) or [Firefox Add-ons store](https://addons.mozilla.org/). --- #### Step 2: Create, Compile & Deploy Smart Contract 1. **Open VSCode**: Launch VSCode and open the terminal using Ctrl + '. 2. **Clone the Project**:
bash
    git clone https://github.com/norah-mohammed/2024-25_GP_25.git
3. **Install Truffle**:
bash
    npm install -g truffle
4. **Install Project Dependencies**:
bash
    npm i
##### Project Structure Overview: - **contracts**: Contains Solidity smart contracts. The Migrations.sol contract is used for managing migrations. - **migrations**: JavaScript files to deploy the smart contracts to the blockchain. - **test**: JavaScript test files for smart contract testing. - **truffle-config.js**: Configuration file for the Truffle project, including blockchain network settings. - **package.json**: Contains project dependencies and scripts. - **package-lock.json**: Automatically generated file listing exact dependency versions. 5. **Compile the Smart Contract**:
bash
    truffle compile
6. **Deploy the Smart Contract**: - Open Ganache and create a new workspace. - Copy the RPC server address. - Update the truffle-config.js file with the Ganache RPC address. - Run the following command in the terminal to deploy the contract:
bash
     truffle migrate
--- #### Step 3: Run DApp 1. **Navigate to the supply-chain-app Folder**:
bash
    cd supply-chain-app
2. **Install All Dependencies**:
bash
    npm i
3. **Install Web3**:
bash
    npm install --save web3
4. **Run the DApp**:
bash
    npm start
The DApp will be hosted at http://localhost:3000. --- #### Step 4: Connect MetaMask with Ganache 1. **Start Ganache**: Open the Ganache application and note the RPC server URL and port number. 2. **Connect MetaMask**: - Open MetaMask in your browser and click on the network dropdown in the top-right corner. - Select "Custom RPC" and enter the Ganache RPC URL and port number. - Click "Save". 3. **Import Account**: - In Ganache, go to the "Accounts" tab, copy the private key of the first account. - In MetaMask, click on the three dots in the top-right corner, select "Import Account," and paste the private key. link to the repositry: https://github.com/norah-mohammed/2024-25_GP_25.git ---


