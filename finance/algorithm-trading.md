# Notes on Algorithmic Trading

## References

1. [Wikipedia: Algorithmic Trading](https://en.wikipedia.org/wiki/Algorithmic_trading)
1. [Quantitative Finance Articles List](https://www.quantstart.com/articles)
1. [Quantopian Tutorial](https://www.quantopian.com/tutorials/getting-started#lesson1)
1. [Python for Finance](https://www.datacamp.com/community/tutorials/finance-python-trading#gs.7SPpyLc)
1. [Algorithmic trading in less than 100 lines of Python code](https://www.oreilly.com/learning/algorithmic-trading-in-less-than-100-lines-of-python-code)
1. [Basics of Algorithmic Trading: Concepts and Examples](http://www.investopedia.com/articles/active-trading/101014/basics-algorithmic-trading-concepts-and-examples.asp)
1. [Algorithmic Trading Glossary](http://www.automatedtrader.net/glossary/)
1. [A - Z List of Trading Strategies](http://www.optionstrading.org/strategies/a-z-list/)
1. [How Trading System Functions](https://www.quantinsti.com/blog/trading-systems-architecture/)

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
