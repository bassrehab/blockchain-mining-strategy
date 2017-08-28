At initialization, every miner begins with the same genesis block and is assigned a number of
parameters, including its “hash rate”. The proof of work is simulated in the sense that if a miner has
X% of the global hash power, it will be able to find X% of blocks.

The simulator runs in steps, where each step represents 1 second. 

There two main types of events:
- at every step, a new transaction will be generated and immediately distributed to all miners.
- about every 600 steps (Poisson arrivals with rate of 1 block per 600 steps), a miner will find a
block.

The “winning” miner will be randomly selected according to the hash power
distribution--a miner with X% of the global hash power will find ~X% of blocks.
When a miner finds a block, it does not have to immediately publish the block. It can strategically wait
before releasing the block to other miners (as in selfish mining). When it does publish the block, the
simulator will introduce a randomized delay of 10-30 steps (seconds) before it actually reaches other
miners. In essence, miners make three fundamental decisions: which block to extend, which
transactions to include when mining, and when to publish a block that’s been found.
There is a simplified model of transactions: a transaction just has a ID, an input address, and a
transaction fee. So the idea of a transaction graph, for instance, doesn’t make sense. The input
address and transaction fee may be useful because some strategies may whitelist or blacklist
transactions based on those fields.