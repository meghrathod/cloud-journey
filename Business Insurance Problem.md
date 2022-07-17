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

* These components in the system are already available and ready to use
	* Data of the insurance policies that the company already has (sql as the data is is vertically larger with data types like string for policy content, number for amount)
	* Data of all current users(noSQL databases - mongoDB: why? because this data has various types like string for names, numbers for salary, date format for date of birth, email IDs  )
* While the current system doesn't have the required capability to handle the demand, the system can be extended to handle the demand.
* Modules that currently not available are the system must be developed and tested in a span of 30 days.

### Decision on the current system

* It seems that the the current system has a few functional components that are good enough for use in the new system
* However the system is not cloud native and incapable of handling 3x loads (why ? the system runs on servers hosted in the insurance office facility and runs an ancient language(COBOL) that does not follow the 15 principle of cloud nativeness like easy maintainability, scalability, upgradibility, etc)
* So, I propose we use only the most essential modules(existing data modules) of the current  system and develop rest of the new system.

### Functional Requirements

* A module that has displays all the various insurance schemes available (assumed to be available and functional in the current system)
* A module that stores all the of these schemes
* A module for purchase of schemes
* A module to process user data before the purchase of a scheme
* A module to check validity of a claim
* A module to process the claim after checking its validity
* Modules to validate and store user data
* **Mainly a new platform that the agents can use for their clients to sell insurance and process this data faster**
* All of this modules must comply to government rules and regulations 
* These modules must be secure and the data must be properly handled

### Flow of buying an insurance policy
![[Insurance.drawio.svg]]

### What all technologies I would like to use

#### Existing tech:
* Frontend: Vanilla HTML, CSS, Javascript
* Hosting: Currently on-premise baremetal servers
* Backend: COBOL
* Database: only mySQL
* Absent: CI/CD

#### Proposed Tech with reasons:
* Reactjs
	* Why current is not correct? The vanilla frontend currently used is slow because every click required a new webpage to be loaded, there is a lot of redundancy in HTML and Javascript code
	* Reactjs uses the idea of single page application which makes loading process as smooth as possible as not all elements have to be rendered every time an action is performed
	* Reactjs also makes frontend modular as each component is treated seperately from the rest of the system
	* Repetive and redundancy in coding is minimised as the build engine takes care of it
* Hosting: Migrate from on-premise to Netlify(initially for the frontend) and Azure(for the backend), as this help remove the lower level of abstraction from a developer/Sysadmin of maintaining the server and increase the total uptime of the system, make the system more efficient and deploy content faster.
* Backend: Expressjs and Node, due to it's simplicity in maintaining APIs and efficiency in delivering requests 
>need to research on more backend technologies
* Database
	* Currently all transactions in database are SQL based, which is fine when it comes to transactions involving purchases and claims of insurance premium
	* However, user registrations must be done on a noSQL database as it has different types of field that are not relational. mongoDB happens to be one such application that can help with storing user data.
* CI/CD
	* This is one major missing point in the current system which is very essential to make the system cloud first.
	* CI or Continuous Integration is tech where every push to a repository triggers actions that can be defined by the development team. TDD or Test Driven Development is where one creates tests that evaluate the requirements of our Insurance platform before  actually creating the platform. Now whenever we make changes and push our code, the test can do security and functional checks on our code and give us updates on the performance of our applicate
	* For the purposes of our Insurance platform, I suggest we use the GitHub actions tool for CI, we can even use the ones provided by LayerCI, etc
	* CD or Continuous Delivery is the tech where we can release our platform continuosly without downtimes with new feature as they're ready. CD can also be used when we want to test a feature like insurance recommendations with only a subset of people 