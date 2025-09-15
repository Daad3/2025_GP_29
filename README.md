# 2024-25_GP_XX: TrustDose  
### Blockchain & IoT Prescription Management System  

The **TrustDose** platform is a blockchain and IoT-based healthcare management system designed to enhance **security, transparency, and traceability** in prescription handling and medicine delivery. It addresses the common challenges of traditional prescription systems, such as the risk of **fraud, errors, loss of prescriptions, and inadequate monitoring of sensitive medicines** during transport.  

TrustDose provides a unified solution where **doctors, pharmacists, patients, and logistics providers** can interact seamlessly through a transparent and tamper-proof platform. Sensitive medicines such as insulin and vaccines require special care, especially with temperature monitoring during distribution. By combining blockchain immutability with IoT real-time sensor readings, TrustDose ensures that patients receive their medicines under safe and optimal conditions.  

The platform focuses on:  
- **Secure prescription management** using blockchain immutability.  
- **Automated workflows** powered by smart contracts for issuing, validating, and dispensing prescriptions.  
- **Real-time monitoring** of temperature-sensitive medicines through IoT sensors.  
- **Transparency and trust** for all stakeholders by documenting every step of the medicine’s journey: *Doctor → Pharmacy → Logistics → Patient*.  

This solution contributes to improving patient safety, reducing fraud, ensuring compliance with storage conditions, and providing a reliable, modern digital healthcare service.  

---

### Technology Used  

- **Blockchain Technology (Ethereum)**: Ensures the immutability and security of prescription records. Every transaction (from doctor issuance to pharmacy dispensing) is recorded on the blockchain, providing full traceability.  
- **Smart Contracts**: Automate processes such as issuing prescriptions, accepting them by pharmacies, updating shipment status, and validating temperature thresholds before final dispensing.  
- **Truffle and Ganache**: Tools for developing, testing, and deploying smart contracts locally.  
- **React.js & Web3.js**: For building the frontend web application and enabling interaction with the blockchain.  
- **Node.js (Middleware)**: Server-side component bridging IoT sensors with the blockchain.  
- **IoT Sensors (ESP32, DHT11)**: Devices used to continuously monitor temperature for sensitive medicines during transport.  

---

### Setting up Local Development  

#### Step 1: Installation and Setup  

1. **VSCode**: Download from [VSCode website](https://code.visualstudio.com/).  

2. **Node.js**: Download the latest version from [Node.js website](https://nodejs.org/). After installation, verify by running:  
   ```bash
   node -v
