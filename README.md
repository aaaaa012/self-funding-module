# self-funding-module for Payout Agent

## Overview
The Self-funding-module enables the agents to initate funding transactions directly through their panel.
It ensures that only validated agents can perform funding, introduces minimum funding rules, avoids duplicate or overlapping transactions.

## Business Objectives
- Simplify and automate the agent funding process.
- Reduce dependency on manual finance team intervention.
- Ensure secure validation before processing financial transactions.

## Workflow Summary
1. Agent initiates a self-funding request:
   The Agent logs into the agent panel and initiates a self-funding request.
2. Bank Validation :
   If this is the first self-funding request from that particular agent, their bank details are validated at our end through the designated validation switch.
3. Receivable Amount Check:
   Onve validation passes, the system checks if the agent's receivable balance is greater then or equal to NPR.1000(Minimum funding threshold).
4. Pending Request Check:
   The system ensures there are no existing pending funding requests for the same agent. Only one active is allowed at a time.
5. Transaction Creation and Routing:
   If all the checks pass, a new transaction record is created.
    The system then determines the route based on the agent's creditor bank and forwards the transaction accordingly.
6. API Response and Final Settlement:
   Depending on the routed API response:
    If the response is success for all the expected API hits, the transaction is then marked as paid and updated in the system.
    If the response is failure for any of the expected API hits, the transactions remains at processing status,and the agents are notified accordingly about the issue.

## Business Analyst Responsibilites
- Gathered and analyzed requirements for self funding workflow.
- Defined validation rules, minimum thresholds. and sequencing logic.
- led UAT testing, covering validation failures, edge cases, and success scenarios.
- Created test cases, SQL Validation scripts, and functional documnetation.

## Outcome
- Reduced manual intervention by automating funding validation.
- Ensured compliance through rule-based validation checks.
- Improved operational efficiency and agent satisfaction.
