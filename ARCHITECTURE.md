# Smart Med-Shelf: System Architecture v1.0

### 1. Data Schema (The "Source of Truth")
The system uses a **Hybrid-State Model** to balance HIPAA/GDPR privacy with blockchain transparency.

| Field Name | Storage Location | Logic |
| :--- | :--- | :--- |
| `Batch_ID` | On-Chain (Compressed) | Unique identifier for the medicine lot. |
| `Patient_Data` | Local Linux Server | **NEVER** stored on-chain. Stays on your hardware. |
| `Expiry_Date` | On-Chain (Compressed) | Immutable timestamp for smart-contract alerts. |
| `Quantity_Left` | On-Chain (Compressed) | Real-time balance for the Reorder Blink. |

### 2. The "Blink" Workflow (Reorder Logic)
Instead of a complex ERP login, we use a **Solana Blink** (Action) workflow:
1. **Trigger:** Hardware sensor (or QR scan) detects low stock.
2. **Action:** Backend generates a signed `Solana Action` URL.
3. **Execution:** Hospital admin receives a Telegram/Email notification with a **one-click button** to sign the reorder transaction.
4. **Settlement:** The payment is sent to the supplier in USDC/USDG instantly.

### 3. Cost Optimization (ZK Compression)
Traditional Solana accounts cost ~0.002 SOL (RM 1.50) per entry. 
* **Our Solution:** Utilizing **ZK Compression** (State Management) in 2026 allows the hospital to store 1,000 batches for the price of 1 traditional account. 
* **Result:** 99% reduction in blockchain storage overhead.
