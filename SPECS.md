# Technical Specifications: Smart Med-Shelf v1.0

### 1. System Overview
A high-integrity SaaS layer built on **Solana** to modernize pharmaceutical supply chains. The system transitions legacy "manual-entry" inventory into an automated, blockchain-verified audit trail using **Solana Actions (Blinks)** for real-time operations.

---

### 2. Core Technical Fields
| Component | Technology | Implementation Detail |
| :--- | :--- | :--- |
| **Blockchain Layer** | Solana Mainnet | Utilizing **ZK Compression** for high-volume batch tracking. |
| **Interface Pattern** | Solana Actions / Blinks | 1-click "Restock" and "Verify" buttons triggered by physical QR/NFC scans. |
| **Storage Engine** | Hybrid (On-Chain/Local) | Metadata on-chain; HIPAA-sensitive data on local Linux-Edge servers. |
| **Development Stack** | TypeScript / Node.js | Next.js 14+ for dashboard; Express.js for the Blink API. |

---

### 3. Smart Contract & Data Schema
To minimize costs, the system uses a **Compressed Account** model to track medication units.

* **Global State (On-Chain):**
    * `Batch_ID`: Unique UUID for the medicine lot.
    * `Expiry_Timestamp`: Immutable date for automated shelf-life alerts.
    * `Location_Hash`: Cryptographic proof of current hospital/ward location.
    * `Quantity_Compressed`: Current stock level tracked via ZK-State.
* **Private State (Local Database):**
    * `Supplier_Contact_Info`: Private vendor details.
    * `Patient_Assignment_Logs`: Local-only records to maintain HIPAA compliance.

---

### 4. Integration & Deployment
* **Linux-Edge Gateway:** Deployed via **Docker** on hospital hardware to ensure secure, low-latency communication with the Solana RPC (Helius/Jito).
* **Security:** Multi-signature authorization for high-value medication reorders (Schedule II drugs).
* **API Layer:** RESTful endpoints for integrating with existing Hospital Information Systems (HIS).

---

### 5. Roadmap
* **Phase 1:** MVP Dashboard + Blink-enabled QR reordering.
* **Phase 2:** ZK-Proof verification for temperature-sensitive supply chains.
* **Phase 3:** Integration with decentralized physical infrastructure (DePIN) for cold-storage tracking.

---
**Developed by Akram Moni** *Senior Full-Stack Architect (7+ Years Experience)*
