# Business Insurance Problem

## Given Conditions

* Currently 90% of all insurance contracts are handled by agents and only 10% are handled online.
* The given month is October.
* Currently the system that is available is only able o process 500 transactions per second(TPS) and there are 10000 units of insurace sold monthly.
* The CEO has demanded all of the transactions and the system must grow by atleast 3 times to handle the demand.

## Problems

1. CFO wants to reduce cost of the system.
2. Sales team wants to move 90% of the business online.
3. The business operations team will be reduced to 50% of the current capacity
4. All of these changes must be integrated into the system in 30 days and the current month is October.
5. The system must be ready with UAT, SIT and VAPT by the next quarter.

## What all needs to be decided?

* Should we build a new system or should we work on the current system?
* What are the functional requirements that need to be implemented?
* What are the technical requirements that need to be implemented?
* What are the business requirements that need to be implemented?

## Proposed solution

### Assumptions

* The current system has a few components which are ready to use like the policy and the client database.
* While the current system doesn't have the required capability to handle the demand, the system can be extended to handle the demand.
* Modules that currently not available are the system must be developed and tested in a span of 30 days.
