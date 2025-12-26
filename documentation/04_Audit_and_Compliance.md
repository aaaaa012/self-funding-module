# Audit & Compliance

## 1. Audit Logging
Every step of the funding process must be logged to an immutable audit trail.

| Data Point | Description | Purpose |
| :--- | :--- | :--- |
| **Request Timestamp** | Precise time of initiation | SLA tracking, Dispute resolution |
| **Agent ID** | Unique identifier of the user | Identification |
| **IP Address & Device ID** | Network origin | Fraud detection |
| **Pre-Balance** | Wallet balance before credit | Reconciliation |
| **Post-Balance** | Wallet balance after credit | Reconciliation |
| **Bank Reference** | External Ref ID from Core Banking | Inter-system reconciliation |

## 2. Fraud Detection
The system integrates with the Risk Engine to monitor for:
*   **Velocity Checks**: >3 failed attempts in 10 minutes blocks the account.
*   **Pattern Recognition**: Clean round numbers (e.g., 100,000) repeatedly requested are flagged for review.
*   **Location Mismatch**: Requests from IP addresses outside the authorized geolocation are blocked.

## 3. Reporting
*   **Daily Reconciliation Report**: Auto-generated at EOD (23:59), matching Total Debits (Bank) vs. Total Credits (Wallet).
*   **Exception Report**: Lists all FAILED or REVERSED transactions for manual operations review.
