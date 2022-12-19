# Liquidation Mechanism

### What is liquidation?

Liquidation is the process that occurs when a borrower's health factor falls below 1, due to the collateral value falling short of the loan or debt value. This can happen if the value of the borrowed debt increases relative to the collateral, or vice versa. The health factor is the ratio of collateral to loan value. During a liquidation, up to 50% of the borrower's debt can be repaid, and that value plus the liquidation charge is deducted from the available collateral.

### How much is the liquidation penalty?

The liquidation penalty (or bonus for liquidators) varies depending on the asset used as collateral. The section on risk parameters contains the liquidation charge for each asset.

### Examples

Here are a few examples to illustrate how liquidation works:

#### Example 1

Bob invests 10 ETH and takes out a DAI loan for 5 ETH. If Bob's health factor falls below 1, his loan may be liquidated. Up to 50% of a single borrowed sum, or 2.5 ETH, may be repaid by a liquidator. The liquidator is only allowed to demand one type of collateral in return, which is ETH (5% bonus). In exchange for returning 2.5 ETH worth of DAI, the liquidator demands 2.5 + 0.125 ETH.

#### Example 2

Bob borrows 5 ETH worth of DAI and deposits 5 ETH worth of YFI. If Bob's health factor falls below 1, his loan can be liquidated. A liquidator can pay back up to 50% of a single loan, which is equivalent to 2.5 ETH in DAI. As the liquidator chooses to claim YFI, the liquidation bonus is higher for YFI (15%) than for ETH (5%) in return. As a result, the liquidator can claim a single collateral. In exchange for repaying 2.5 ETH to DAI, the liquidator claims YFI in the amounts of 2.5 plus 0.375 ETH.

### How can I avoid liquidation?

There are a few ways you can avoid liquidation:

* Deposit additional collateral assets
* Repay a portion of your loan
* Maintain a high health factor (e.g., above 2)

Keep in mind that repaying a loan generally raises your health factor more than depositing additional collateral does. You should also be aware of how market conditions and stablecoin price fluctuations can affect your health factor. The price discovery section has more information about price oracles.

