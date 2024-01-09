Project 3: SimpleMarketSimulator

Introduction
The economy is an indispensable fact of our lives. In real life, for buying and selling things, we use some printed or virtual assets, called money. However, your money does not have any difference with paper in your pocket. It gains its value only in a marketplace.

In this project, you are going to implement a basic marketplace model. This model consists of traders, wallets, transactions, currencies, and the market. For simplicity, we have two currencies in the market: dollar and PQoin(Priority Queue Coin). Traders can give buying or selling orders to the market if they can afford them.

In our market model, there are two priority queues for storing orders. In a priority queue, elements having the highest priority serve before. The priority rules are written in the next sections. With these rules, your market implementation should make transactions if these two priority queues’ tops overlap.

Input/Output
The first line of the input file specifies the random seed that you have to use to generate random numbers in the project: A

The second line of the input file specifies the initial transaction fee of the marketplace, the number of users, and number of queries: B C D

The next C lines represent the initial dollars and PQoins asset in each trader’s wallet.

<dollar_amount> <PQoin_amount>
<dollar_amount> <PQoin_amount>
...
<dollar_amount> <PQoin_amount>
<dollar_amount> <PQoin_amount>
The next D lines are the queries. There are exactly 14 types of events.

Trader specific queries:

➔ 10: Give buying order of specific price

10 <trader_id> <price> <amount>


➔ 11: Give buying order of market price

11 <trader_id> <amount>


Note: This is similar to Query#10, but it takes the current selling price as price. Note: If there is no current selling price then increment the number of invalid queries.

➔ 20: Give selling order of specific price

20 <trader_id> <price> <amount>


➔ 21: Give selling order of market price

21 <trader_id> <amount>


Note: This is similar to Query#20, but it takes the current buying price as price.

➔ 3: Deposit a certain amount of dollars to the wallet

3 <trader_id> <amount>


➔ 4: Withdraw a certain amount of dollars from the wallet

4 <trader_id> <amount>


➔ 5: Print wallet status

5 <trader_id>


Prints “Trader : <trader_s_dollars>$ <trader_s_PQoins>PQ” to the output file.

System Queries
➔ 777: Give rewards to all traders

777


When this query is read, the system creates and distributes random amounts of PQoins to all traders. For each trader add myRandom.nextDouble()*coins to the trader’s wallet.

➔ 666: Make an open market operation

666 <price>

When this query is read, the system compensates buying or selling orders in order to set the price of PQoin to the given price.

This query can increase or decrease the total amount of PQoin in the market.

➔ 500: Print the current market size

500


Prints “Current market size: <total_$_in_buying_pq> <total_PQoin_in_selling_pq>” to the output file.

➔ 501: Print number of successful transactions

501


Prints “Number of successful transactions: <num_of_successful_transaction>” to the output file.

➔ 502: Print the number of invalid queries

502


Prints “<number_of_invalid_queries>” to the output file.

Note: If a trader is unable to satisfy the query’s liabilities, then the number of invalid queries is incremented by one.

➔ 505: Print the current prices

505


Prints “Current prices: <cp_buying> <cp_selling> <cp_average>” to the output file. Note: If one of the PriorityQueues is empty then the price related to it, is not included in the average current price.

➔ 555: Print all traders’ wallet status

555


Prints “<trader_s_dollars>$ <trader_s_PQoins>PQ” of all traders.
