# API Specification

## 1. Initiate Funding
**POST** `/api/v1/funding/initiate`

Validates the agent's eligibility and limits before starting the transaction.

### Request
```json
{
  "agentId": "AGT_88592",
  "amount": 50000.00,
  "currency": "NPR",
  "sourceBankId": "BANK_NIBL",
  "deviceFingerprint": "xy78-223a-cc90"
}
```

### Response (Success)
```json
{
  "status": "SUCCESS",
  "requestId": "req_123456789",
  "transactionId": "txn_998877",
  "newBalance": 150000.00,
  "message": "Wallet funded successfully."
}
```

### Response (Error - Limit Exceeded)
```json
{
  "status": "ERROR",
  "errorCode": "LIMIT_EXCEEDED",
  "message": "Requested amount exceeds daily limit of NPR 5,000,000."
}
```

## 2. Check Request Status
**GET** `/api/v1/funding/status/{requestId}`

Used for polling the status if the initial request times out.

### Response
```json
{
  "requestId": "req_123456789",
  "transactionId": "txn_998877",
  "currentState": "COMPLETED",
  "timestamp": "2023-11-01T09:30:15Z"
}
```
