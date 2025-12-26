# Business Rules & Logic

## 1. Eligibility Criteria
To initiate a self-funding request, the agent must meet the following criteria:
*   **Active Status**: The agent's account status must be `ACTIVE`.
*   **KYC Verified**: The agent must have completed full KYC verification.
*   **No Flagged History**: No fraud flags in the last 30 days.

## 2. Funding Constraints
*   **BR-01 Minimum Amount**: The minimum funding amount is **NPR 1,000**. Requests below this will be auto-rejected.
*   **BR-02 Maximum Amount**: The maximum per-transaction limit is **NPR 500,000** (Tier 1 Agents) and **NPR 2,000,000** (Tier 2 Agents).
*   **BR-03 Daily Limit**: Cumulative daily funding cannot exceed **NPR 5,000,000**.

## 3. Concurrency Control
*   **BR-04 Single Active Request**: An agent can have only **one** pending funding request at a time.
*   **BR-05 Lock Mechanism**: A database lock is applied on the Agent ID during the processing phase to prevent double-crediting.

## 4. Wallet Credit Logic
*   **BR-06 Real-Time Credit**: Funds are credited immediately upon successful debit confirmation from the source bank.
*   **BR-07 Reversal**: If the wallet credit fails after bank debit, an automatic reversal (refund) to the bank must be initiated within T+0.
