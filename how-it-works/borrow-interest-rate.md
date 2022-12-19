# Borrow Interest Rate

## Monetaria Interest Rate

The Monetaria interest rate algorithm is designed to manage liquidity risk and optimize utilization. Borrow interest rates are derived from the utilization rate ($$U$$), which indicates the availability of capital within the pool.

### Utilization Rate

The interest rate model manages liquidity risk in the protocol through user incentives to support liquidity:

* When capital is available: low interest rates to encourage borrowing.
* When capital is scarce: high interest rates to encourage repayments of debt and additional supplying.

### Interest Rate Model

Liquidity risk becomes more problematic as $$U$$ approaches 100%. To address this constraint, the interest rate curve is split into two parts around an optimal utilization rate $$U_{optimal}$$. Before $$U_{optimal}$$, the slope is small, after it begins rising sharply.

The interest rate $$R_t$$ follows the model:

$$if \hspace{1mm} U < U_{optimal}: \hspace{1cm} R_t = R_0 + \frac{U_t}{U_{optimal}} R_{slope1}$$

$$​ if \hspace{1mm} U \geq U_{optimal}: \hspace{1cm} R_t = R_0 + R_{slope1} + \frac{U_t-U_{optimal}}{1-U_{optimal}}R_{slope2}$$

In the borrow rate technical implementation, the `calculateCompoundedInterest` method relies on an approximation that mostly affects high interest rates. The resulting actual borrow rate is as follows:

\$$ \text{Actual APY} = \left( 1 + \frac{\text{Theoretical APY\}}{\text{secsperyear\}} \right)^{\text{secsperyear\}} - 1 \$$

* When $$U<U_{optimal}$$, borrow interest rates increase slowly with utilization.
* When $$U \geq U_{optimal}$$, borrow interest rates increase sharply with utilization to above 50% APY if liquidity is fully utilized.

Both the variable and stable interest models are derived from the formula above with different parameters for each asset.

Alternatively, stable debts maintain their interest rate at issuance until the specific rebalancing conditions are met. In Monetaria interest models are optimised by new rate strategy parameter **Optimal Stable/Total Debt Ratio** to algorithmically manage stable rate.

$$if \hspace{1mm} ratio < ratio_{o}: \hspace{1cm} R_{t} = r_{0} + \frac{ratio - ratio_{o}}{1 - ratio_{o}}R_{base}$$

## Model Parameters

There are several factors that need to be considered when determining the interest rates for assets on Monetaria.

### Collateral Assets

First, it is important to distinguish between assets that are predominantly used as collateral (i.e., volatile assets) and need liquidity at all times to enable liquidations.

### Liquidity

The liquidity of an asset on Monetaria is also an important factor. In general, assets with higher liquidity levels should have more stable utilisation and therefore more conservative interest rates.

### Market Conditions

It is also key to consider the current market conditions for an asset. Monetaria's borrowing costs should be aligned with market yield opportunities to prevent rate arbitrage, where users may be incentivized to borrow all the liquidity on Monetaria to take advantage of higher yield opportunities.

### Liquidity Mining

With the rise of liquidity mining, Monetaria has adapted its cost of borrowing by lowering the optimal utilisation rate (Uoptimal) for certain assets. This has increased the borrow costs for these assets, which are partially offset by the liquidity reward.

## Interest Rate Model Parameters

There are two types of interest rate models on Monetaria: variable and stable. Each model has its own set of parameters that are used to determine the interest rate for a given asset.

### Variable Interest Rate Model Parameters

The following parameters are used in the variable interest rate model:

* Optimal utilisation rate ($$U_{optimal}$$)
* Base variable borrow rate
* Variable rate slope 1
* Variable rate slope 2

### Stable Interest Rate Model Parameters

The following parameters are used in the stable interest rate model:

* Optimal utilisation rate ($$U_{optimal}$$)
* Base stable borrow rate
* Stable rate slope 1
* Stable rate slope 2
* Stable to total debt ratio

### Stable Interest Rate

The stable interest rate provides predictability for the borrower, but it comes at a cost as the interest rates are higher than the variable rate. The rate of a stable loan is fixed until the following rebalancing conditions are met:

* Utilization rate: $$U_t > 95%$$
* Overall borrow rate, the weighed average of all the borrow rates: $$R_O < 25%$$
