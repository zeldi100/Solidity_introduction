# Introduction to Smart Contracts using Solidity

## 1. Overview
The purpose of this exercise is and introduction to programming smart contracts with Solidity, by building 3 profit splitter contracts. These contracts will do several things:
 * Pay your employees quickly and easily (Level 1)
 * Distribute profits to different tiers of employees (Level 2)
 * Distribute company shares for employees in a "deferred equity incentive plan" automatically (Level 3).

The following tools are used to build the Solidity contracts:
 * Ganache - Ganache is a personal blockchain for rapid Ethereum distributed application development. 
 * Remix IDE - Remix is a powerful, open source tool that helps you write Solidity contracts straight from the 
   browser
 * Metamask - MetaMask is a Google Chrome extension for the browser which makes it easy for web applications to 
   communicate with the Ethereum blockchain. 



## 3. Level 1: `AssociateProfitSplitter` Contract
This contract will accept ether into the contract, and divide it evenly among associate-level employees. This will allow the human resources department to pay employees quickly and efficiently.

The following is a summary of steps in the contract:
   * Defined public variables 
   * Created a constructor
   * Created 3 functions: </br>
        a. Balance function which returns the contract's current balance, which should always be '0' </br>

        b. Deposit function must ensure only the owner can call the function and that any remainder after division of the deposited amount, needs to be sent back to the owner, </br>

        c. Fallback function which ensures that the logic in the deposit function is executed if ether is sent directly to the contract, which prevents Ether being locked in the contract. </br>


Images of code and steps performed:

Code in Solidity for AssociateProfitSplitter: </br>
![APS](./Images/L1_APS_0_SolidityCode.png)

Deploy code in Remix with 0 Ether, for which there is a fee charged to the account:

![APS](./Images/L1_APS_3_Deploy.png)

Test functionality by transfering 45ETH
![APS](./Images/L1_APS_4_Deposit.png)

Ganache screenshots before and after showing the 15ETH increase in 3 accounts:

|![APS](./Images/L1_APS_2_Compile_Ganache.png)|![APS](./Images/L1_APS-5_Deposit_Ganache.png)|
|:---:|:---:|
| Account Value Pre-AssociateProfitSplitter | Account Value Post-AssociateProfitSplitter |

## 4. Level 2: `TieredProfitSplitter` Contract
This contract will distribute different percentages of incoming ether to employees at different tiers/levels. For example, the CEO gets paid 60%, CTO 25%, and Bob gets 15%.

The following is a summary of steps modified in the contract:
   * Deposit function: Calculating the points per employee representing a percentage which will be used to calculate the amount to be sent to each employee, with the remainder being sent to the employee with the highest percentage.</br>

Images of code and steps performed:

Code in Solidity for TieredProfitSplitter: </br>
![TPS](./Images/L2_TPS_0_SolidityCode.png) 

Compile and deploy code with 0ETH, with fee charged: </br>
![TPS](./Images/L2_TPS_3_Deploy.png)

Deposit 30ETH, which is allocated as per percentages: </br>
![TPS](./Images/L2_TPS_4_Deposit.png)

Ganache screenshots before and after showing the 30ETH divided into 3 accounts with starting balance 110.67ETH increasing with 18ETH, 7.5ETH and 4.5ETH respectively:

|![APS](./Images/L2_TPS_2_Compile_Ganache.png)|![APS](./Images/L2_TPS_5_Deposit_Ganache.png)|
|:---:|:---:|
| Account Value Pre-TieredProfitSplitter | Account Value Post-TieredProfitSplitter |
</br>

## 5. Level 3: `DeferredEquityPlan` Contract
This contract will be managing an employee's "deferred equity incentive plan," in which 1000 shares will be distributed over four years to the employee. There is no need to work with ether in this contract, but amounts will be stored that represent the number of distributed shares the employee owns, and enforcing the vetting periods automatically.

The following is a summary of steps modified in the contract:
   * Set human resources in constructor as they will deploy the contract
   * Total shares of 1000 allocated per employee, payable over 4 years, 250 per year
   * Set start_time as Now
   * Create distribute function which distributes shares if a year has passed and ensures maximum of 1000 is allocated over 4 years

For purposes of testing locally a test file was created, DeferredEquityPlan_test.sol in which a new variable was added 'fakenow'. Fakenow is used in conjunction with a Fastforward function, that adds 100 days to the contract period. By fastforwarding 4 times, one can then distribute and test the code.

Images of steps performed for testing locally:

Link to DeferredEquityPlan_test:
![DEP](./Solidity_code/xxx.png) 

Deploy code in local test environment:
![DEP](./Images/L3_DEP_test_1_deploy.png)






