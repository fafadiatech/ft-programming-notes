# Notes on Algorithmic Trading

1. [Quantopian Tutorial](https://www.quantopian.com/tutorials/getting-started#lesson1)

## Quantopian Algorithm Building

1. Initialize context in `initialize(context)` function
	- Select Securities
	- Define Slippage Model
	- Define Commisions
1. Define Weights {How much we'd like to invest in security as %} `compute_weights(context,data)` function
1. Define Rebalancing Schedule {Things we'd like to re-align our positions} in `rebalance(context,data)`
1. Define all variables that we want to record in `record_vars(context, data)`
1. Define main logic of Algorithm in `handle_data(context, data)` function

Note: `context.portfolio.positions` is where all of our open positions are stored {Positions are our commitment to purchase quantity of security at a purchase price}
