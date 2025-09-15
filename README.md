# TrustDose — منصة موحّدة لإدارة الوصفات الطبية باستخدام Blockchain و IoT

[![Status](https://img.shields.io/badge/status-MVP-blue)]()
[![License](https://img.shields.io/badge/license-MIT-green)]()
[![Made with](https://img.shields.io/badge/stack-React%20%7C%20Node.js%20%7C%20Solidity%20%7C%20Ganache%20%7C%20Web3.js-lightgrey)]()

> **AR / EN** — يحتوي هذا الملف على شرح بالعربية مع أقسام إنجليزية أسفل كل عنوان عند الحاجة ليكون جاهزًا للنشر في GitHub.

---

## 📌 نظرة عامة | Overview
**TrustDose** هو مشروع يهدف إلى **تتبع صرف الوصفات الطبية** مع **تتبع حرارة الأدوية الحساسة** أثناء التوصيل، عبر دمج:
- **Blockchain (Ethereum)** لتسجيل الوصفات والعميات بشكل غير قابل للتلاعب.
- **IoT Sensors** (مثل DHT11/ESP32) لقراءة درجة الحرارة أثناء التسليم.
- **Smart Contracts** لإدارة الأدوار (Doctor / Pharmacist / Patient / Logistics) وتأكيد الصرف.
- **Web App (React + Web3.js)** لواجهات الأطباء والصيدليات والمرضى واللوجستيك.

**EN:** TrustDose secures prescription management and cold-chain monitoring by combining Ethereum-based smart contracts with IoT temperature sensors and a React web app.

---

## 🎯 الأهداف | Goals
- تقليل **تزوير/فقدان** الوصفات.
- ضمان **سلامة الأدوية الحساسة** عبر مراقبة الحرارة.
- توفير **شفافية** في رحلة الدواء: (إصدار → صيدلية → لوجستيك → مريض).
- واجهات سهلة الاستخدام لجميع الأدوار.

---

## 🧩 المزايا الرئيسية | Key Features
- تسجيل وصفة غير قابل للتعديل (Immutable prescription).  
- إدارة أدوار وصلاحيات: Doctor / Pharmacist / Patient / Logistics.  
- تتبع خطّي لحالة الوصفة والدواء (Timeline).  
- ربط IoT لإرسال قراءات الحرارة مع كل حدث في التوصيل.  
- تنبيهات عند **تجاوز درجة الحرارة** المحددة للأدوية الحساسة.  

---

## 🏗️ المعمارية | Architecture
```
React (Web UI)  ── Web3.js ──>  Smart Contracts (Solidity) ──> Ganache/Testnet
       │
       └── REST API (Node.js/Express) ── MQTT/HTTP ──> ESP32 + DHT11 (IoT)
```
**EN:** The frontend talks to smart contracts for trust & audit, while Node.js bridges IoT sensor data into the blockchain event flow.

---

## 📂 هيكلة المجلدات | Project Structure
```
trustdose/
├─ client/                  # React app (Vite/CRA)
│  ├─ src/
│  │  ├─ pages/             # Doctor/Pharmacy/Patient/Logistics
│  │  ├─ components/        # UI components
│  │  └─ web3/              # ABI, contract hooks
├─ contracts/               # Solidity contracts
│  ├─ TrustDose.sol
│  └─ Migrations.sol
├─ migrations/              # Truffle migrations
├─ scripts/                 # Deployment / utilities
├─ server/                  # Node.js (Express) for IoT bridge
│  ├─ src/
│  │  ├─ routes/
│  │  ├─ services/          # MQTT/Serial readers, validation
│  │  └─ models/
├─ iot/                     # ESP32 sketches
│  └─ esp32_dht11.ino
├─ test/                    # Contract tests (Mocha/Chai)
└─ README.md
```

---

## 🛠️ المتطلبات | Prerequisites
- Node.js 18+ و npm
- Truffle أو Hardhat (أحدهما)
- Ganache (محلي) أو شبكة اختبار (Sepolia)
- MetaMask
- Python 3 (اختياري لبعض الأدوات)
- عند استخدام MQTT: Mosquitto أو أي Broker بديل

---

## 🚀 التثبيت والتشغيل | Setup & Run

### 1) استنساخ المشروع | Clone
```bash
git clone https://github.com/<your-username>/trustdose.git
cd trustdose
```

### 2) تثبيت الحزم | Install deps
```bash
# العقود
npm i -g truffle
npm i

# الويب
cd client && npm i && cd ..

# السيرفر
cd server && npm i && cd ..
```

### 3) إعداد البيئة | Env
أنشئ ملفات `.env` في `client/` و `server/`:
```
# server/.env
PORT=4000
MQTT_URL=mqtt://localhost:1883
TEMP_THRESHOLD=8-25    # حدود مسموحة مثل 2-8 أو 8-25
CHAIN_RPC=http://127.0.0.1:7545
CONTRACT_ADDRESS=<filled after deploy>
PRIVATE_KEY=<for service signer if needed>

# client/.env
VITE_CHAIN_ID=1337
VITE_RPC_URL=http://127.0.0.1:7545
VITE_CONTRACT_ADDRESS=<after deploy>
```

### 4) البلوك تشين محليًا | Blockchain
- افتح **Ganache** وأنشئ Workspace جديد.
- حدّث `truffle-config.js` برقم الشبكة وRPC.

نشر العقود:
```bash
truffle compile
truffle migrate --network development
```

### 5) تشغيل الويب والسيرفر | Run
```bash
# في تبويب أول
cd server
npm run dev

# في تبويب ثانٍ
cd client
npm run dev
```

---

## 🔗 العقود الذكية | Smart Contracts
- `TrustDose.sol`:
  - `issuePrescription(patient, drugId, sensitive)`
  - `acceptByPharmacy(prescriptionId)`
  - `attachTemperature(prescriptionId, reading, ts)`  ← من الـ IoT Bridge
  - `markDispensed(prescriptionId)`
  - أحداث (Events) لتتبع الحالة: `Issued`, `Accepted`, `TempLogged`, `Dispensed`

**EN:** Roles can be enforced with modifiers. Sensitive meds trigger stricter checks (e.g., temperature thresholds before `Dispensed`).

---

## 🌡️ تكامل الـ IoT | IoT Bridge
- ESP32 يقرأ من DHT11 ويرسل عبر **MQTT/HTTP** إلى خادم **Node.js**.
- السيرفر يقوم بالتحقق (Validation) ثم يرسل معاملة للعقد `attachTemperature(...)`.
- من الأفضل تسجيل السجل كاملًا (Off-chain DB) + مرجع Hash على البلوك تشين.

**Pseudo HTTP Payload**
```json
{
  "prescriptionId": "0x123...",
  "celsius": 7.3,
  "timestamp": 1712345678,
  "signature": "<device-signed-optional>"
}
```

---

## 🔐 الأمان | Security
- أذونات صارمة على العقود (Modifiers / AccessControl).  
- توقيعات رقمية لأجهزة IoT (اختياري).  
- التحقق من حدود الحرارة قبل الصرف النهائي.  
- تشفير مفاتيح البيئة وعدم رفعها للمستودع.  
- حماية الواجهة والـ API (JWT/Session + Rate Limit + Input Validation).  

---

## 🧪 الاختبارات | Testing
- اختبارات Mocha/Chai لعقود Solidity.  
- وحدات Jest لطبقة Node.js.  
- اختبارات واجهة (Playwright/Cypress).  

تشغيل أمثلة:
```bash
npm run test:contracts
npm run test:server
npm run test:client
```

---

## 🗺️ خارطة الطريق | Roadmap
- [ ] دعم شبكة اختبار عامة (Sepolia/holesky).  
- [ ] لوحة مراقبة الحرارة في الزمن الحقيقي.  
- [ ] دعم APP موبايل (React Native).  
- [ ] تكامل مع أنظمة حكومية (Wasfaty API).  
- [ ] تنبيهات SMS/Push Notifications.  

---

## 📜 الترخيص | License
MIT — راجع ملف `LICENSE`.

---

## 👥 المساهمون | Contributors
- **Product/PM:** …
- **Blockchain:** …
- **IoT:** …
- **Frontend/Backend:** …

> **Screenshots**: أضف صورًا لواجهات Doctor/Pharmacy/Patient/Logistics داخل مجلد `docs/` وأشر إليها هنا.

---

## 🧾 أوامر مفيدة | Useful Scripts
```bash
# server
npm run dev        # nodemon
npm run build      # build
npm run lint

# client
npm run dev
npm run build
npm run preview
```

---

## ❓أسئلة شائعة | FAQ
- **هل تُسجّل كل البيانات على السلسلة؟**  
  لا، يتم تسجيل الحد الأدنى (الأحداث، الهاش، حالة الوصفة). البيانات التفصيلية تُحفظ Off‑chain مع مرجع على السلسلة.
- **ماذا يحدث عند تجاوز الحرارة؟**  
  تَصدر تنبيهات ويمنع العقد إنهاء الصرف حتى التحقق.
- **هل تدعم المنصة الأجهزة المتعددة؟**  
  نعم، عبر بروتوكولات موحدة (MQTT/HTTP) وتعريف لكل جهاز.

---

### 🌟 ملاحظات
- عدّل أسماء الشبكات والعناوين في ملفات الإعداد.  
- لا ترفع مفاتيح خاصة للمستودع. استخدم `.env`.  
- أضف **صور الشاشة** و**Sequence Diagrams** في `docs/` لزيادة وضوح المشروع.
