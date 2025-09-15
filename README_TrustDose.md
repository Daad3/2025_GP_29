# 2024-25_GP_XX: TrustDose  
### Blockchain & IoT Prescription Management System  

**TrustDose** is a blockchain and IoT-based healthcare system designed to secure and track medical prescriptions, especially for sensitive medicines such as insulin and vaccines.  
The platform facilitates interactions between doctors, pharmacies, patients, and logistics providers, ensuring transparency and safety in medicine delivery.  
Each prescription and its status are recorded on the blockchain, while IoT sensors continuously monitor storage and delivery conditions.  

---

### Technology Used  

- **Blockchain Technology (Ethereum)**: Provides immutability and transparency for prescription and transaction records.  
- **Smart Contracts**: Automates processes such as issuing prescriptions, pharmacy acceptance, temperature logging, and medicine delivery.  
- **Truffle and Ganache**: For developing, testing, and deploying smart contracts locally.  
- **React.js & Web3.js**: Frontend development and blockchain interaction.  
- **Node.js (Middleware)**: Acts as a bridge between IoT devices and blockchain.  
- **IoT Sensors (ESP32, DHT11)**: For real-time temperature monitoring of sensitive medicines.  

---

### Setting up Local Development  

#### Step 1: Installation and Setup  

1. **VSCode**: Download from [VSCode website](https://code.visualstudio.com/).  
2. **Node.js**: Download from [Node.js website](https://nodejs.org/). Verify installation:  
   ```bash
   node -v
   ```  
3. **Git**: Download from [Git website](https://git-scm.com/downloads). Verify installation:  
   ```bash
   git --version
   ```  
4. **Ganache**: Download from [Ganache official website](https://trufflesuite.com/ganache/).  
5. **MetaMask**: Install as a browser extension from [Chrome Web Store](https://chrome.google.com/webstore/category/extensions) or [Firefox Add-ons](https://addons.mozilla.org/).  

---

#### Step 2: Create, Compile & Deploy Smart Contract  

1. **Open VSCode** and open the terminal (`Ctrl + '`).  

2. **Clone the Project**:  
   ```bash
   git clone https://github.com/your-username/trustdose.git
   cd trustdose
   ```

3. **Install Truffle**:  
   ```bash
   npm install -g truffle
   ```

4. **Install Project Dependencies**:  
   ```bash
   npm i
   ```

##### Project Structure Overview:  
- **contracts**: Contains Solidity smart contracts.  
- **migrations**: JavaScript files for contract deployment.  
- **test**: Smart contract test files.  
- **truffle-config.js**: Truffle configuration file for blockchain networks.  
- **client/**: React frontend for doctor/pharmacy/patient/logistics dashboards.  
- **server/**: Node.js middleware to connect IoT devices with blockchain.  

5. **Compile the Smart Contract**:  
   ```bash
   truffle compile
   ```

6. **Deploy the Smart Contract**:  
   - Open Ganache and create a new workspace.  
   - Copy the RPC server address.  
   - Update `truffle-config.js` with the Ganache RPC address.  
   - Deploy contracts:  
     ```bash
     truffle migrate
     ```

---

#### Step 3: Run DApp  

1. **Navigate to the client Folder**:  
   ```bash
   cd client
   ```

2. **Install Dependencies**:  
   ```bash
   npm i
   ```

3. **Run the DApp**:  
   ```bash
   npm start
   ```
   The app will run at `http://localhost:3000`.  

---

#### Step 4: Connect MetaMask with Ganache  

1. **Start Ganache**: Note the RPC server URL and port.  

2. **Connect MetaMask**:  
   - Open MetaMask and select the network dropdown.  
   - Choose "Custom RPC" and enter Ganache RPC URL.  
   - Save the configuration.  

3. **Import Account**:  
   - In Ganache, copy the private key of an account.  
   - In MetaMask, select "Import Account" and paste the private key.  

---

📌 **Repository Link**: [TrustDose Repo](https://github.com/your-username/trustdose.git)  
