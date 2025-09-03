# 2025_GP_29: TrustDose
## Blockchain-Based Prescription and Medication Delivery System  

**TrustDose** is a blockchain-based platform designed to enhance transparency, security, and efficiency in prescription management and medication delivery. The system connects doctors, pharmacists, logistics providers, and patients through a secure and decentralized ledger, ensuring that every stage of the medication lifecycle—from prescription issuance to patient receipt—is accurately tracked and tamper-proof.  

By integrating **IoT sensors**, TrustDose provides real-time monitoring for temperature-sensitive medications such as insulin and vaccines, ensuring they are stored and delivered under optimal conditions.  

---

## 🛠️ Technology Used

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

---

## ⚙️ Setting up Local Development

### **Step 1: Installation and Setup**
1. **VSCode:** Download and install from [https://code.visualstudio.com](https://code.visualstudio.com)  
2. **Node.js:** Download from [https://nodejs.org](https://nodejs.org)  
   Verify installation:
   ```bash
   node -v
   npm -v
Git: Download from https://git-scm.com
Verify installation:

bash
نسخ الكود
git --version
Ganache: Download and install from https://trufflesuite.com/ganache

MetaMask: Install from the Chrome Web Store or Firefox Add-ons.

Step 2: Create, Compile & Deploy Smart Contract
Open VSCode: Launch VSCode and open the terminal using Ctrl + '.

Clone the Project:

bash
نسخ الكود
git clone https://github.com/YourUsername/2025_GP_29.git
cd 2025_GP_29
Install Truffle:

bash
نسخ الكود
npm install -g truffle
Install Project Dependencies:

bash
نسخ الكود
npm install
Compile the Smart Contract:

bash
نسخ الكود
truffle compile
Deploy the Smart Contract:

Open Ganache and create a new workspace.

Copy the RPC server address (e.g., HTTP://127.0.0.1:7545).

Update truffle-config.js with the RPC address.

Deploy the contract:

bash
نسخ الكود
truffle migrate --reset
Step 3: Run the Application
Run the Frontend
bash
نسخ الكود
cd frontend
npm install
npm start
The DApp will be hosted at: http://localhost:3000

Run the Backend
bash
نسخ الكود
cd backend
npm install
npm start
Step 4: Connect MetaMask with Ganache
Start Ganache: Open Ganache and note the RPC server URL and port.

Configure MetaMask:

Go to MetaMask → Settings → Networks → Add Network.

Enter the Ganache RPC URL and port number.

Save the settings.

Import Account:

In Ganache, copy the private key of an account.

In MetaMask, click the three dots → Import Account → Paste the private key.

Step 5: (Optional) IoT Simulation
If your project includes IoT scripts:

bash
نسخ الكود
cd iot
# Run IoT simulation scripts based on project instructions
