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
1. [CppCon 2017: Carl Cook “When a Microsecond Is an Eternity: High Performance Trading Systems in C++”](https://www.youtube.com/watch?v=NH1Tta7purM&feature=youtu.be)

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

## Typical Architecture of Algorithmic Trading System

1. Market Feed {This is where Data Management is done}
    - [MongoDB](https://www.mongodb.com/) seem to be a good option for storing time series data
    - [Apache Arrow](https://arrow.apache.org/) also gets mention
1. Complex Event Processing {CEP, Event driven architecture seems pretty popular. This is the heart of the entire system and this is where all strategires are runned}
    - [Apache Kafka](https://kafka.apache.org/) is typically used in this setting {Provides Pub-Sub Mechanism}
    - [Protocol Buffer](https://developers.google.com/protocol-buffers/docs/pythontutorial) is used for data serialization
    - [Apache Spark](https://spark.apache.org/docs/latest/streaming-programming-guide.html) is used for data processing {it fits with Kafka. So aggregation is done by Kafka and Computation is done by Spark}
1. Order Management {This is where Risk Management is also typically implemented}
    - This is also know as Order Routing System
    - [FIX](https://en.wikipedia.org/wiki/Financial_Information_eXchange) protocol is typically used
1. Post Trading {P/L statement generator, Reconsilation etc}

## Typical Tasks for Algorithmic Trading System include:

1. Research
    - Core Research
    - Data Research
    - Data Labs
1. Data Management
1. Signal Generation
1. Order Management
1. Post Trading

## Video Talks

1. [Algorithmic Trading with Python](https://www.youtube.com/watch?v=dDMptG5YYyY)
1. [Realtime Risk Management Using Kafka, Python, and Spark Streaming](https://www.youtube.com/watch?v=5XB-T4hzV00)
1. [Dr Jessica Stauth: Portfolio and Risk Analytics in Python with pyfolio](https://www.youtube.com/watch?v=BCLgXjxYONg)
1. [Futures Market Explained](https://www.youtube.com/watch?v=CC9VeHrI3Es)
1. [Nicole Carlson | A Quickstart Guide to PyMC3](https://www.youtube.com/watch?v=rZvro4-nFIk)

## Blog Posts

1. [How is complex event processing integrated into trading systems? How is this data being used within firms?](https://www.quora.com/How-is-complex-event-processing-integrated-into-trading-systems-How-is-this-data-being-used-within-firms)
1. [Decoding the Black Box running Trading Systems](https://www.quantinsti.com/blog/decoding-black-box-running-trading-systems/)
1. [Research Backtesting Environments in Python with pandas](https://www.quantstart.com/articles/Research-Backtesting-Environments-in-Python-with-pandas)
1. [Introduction to Backtesting with Python and Pandas](https://s3.amazonaws.com/quantstart/media/powerpoint/an-introduction-to-backtesting.pdf)
1. [Baysien Cone](https://blog.quantopian.com/bayesian-cone/)

## Tools


### Tools from Quantopian

1. [Pyfolio](https://github.com/quantopian/pyfolio) - this is Performance and Risk analytics engine
1. [Zipline](https://github.com/quantopian/zipline) - this is Backtesting engine written in Python
