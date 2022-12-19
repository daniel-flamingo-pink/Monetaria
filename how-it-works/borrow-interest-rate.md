# Borrow Interest Rate

## Monetaria Interest Rate

The Monetaria interest rate algorithm is designed to manage liquidity risk and optimize utilization. Borrow interest rates are derived from the utilization rate (UU), which indicates the availability of capital within the pool.

### Utilization Rate

The interest rate model manages liquidity risk in the protocol through user incentives to support liquidity:

* When capital is available: low interest rates to encourage borrowing.
* When capital is scarce: high interest rates to encourage repayments of debt and additional supplying.

### Interest Rate Model

Liquidity risk becomes more problematic as UU approaches 100%. To address this constraint, the interest rate curve is split into two parts around an optimal utilization rate (U\<sub>optimal\</sub>). Before U\<sub>optimal\</sub>, the slope is small, after it begins rising sharply.

The interest rate (R\<sub>t\</sub>) follows the model:

\$$ \begin{cases} R\_t = R\_0 + \frac{U\_t}{U\_{optimal\}} R\_{slope1} & \text{if } U < U\_{optimal} \ R\_t = R\_0 + R\_{slope1} + \frac{U\_t-U\_{optimal\}}{1-U\_{optimal\}}R\_{slope2} & \text{if } U \geq U\_{optimal} \end{cases} \$$

In the borrow rate technical implementation, the `calculateCompoundedInterest` method relies on an approximation that mostly affects high interest rates. The resulting actual borrow rate is as follows:

\$$ \text{Actual APY} = \left( 1 + \frac{\text{Theoretical APY\}}{\text{secsperyear\}} \right)^{\text{secsperyear\}} - 1 \$$

* When U < U\<sub>optimal\</sub>, borrow interest rates increase slowly with utilization.
* When U >= U\<sub>optimal\</sub>, borrow interest rates increase sharply with utilization to above 50% APY if liquidity is fully utilized.

Both the variable and stable interest models are derived from the formula above with different parameters for each asset.
