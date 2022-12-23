# Portfolio
---
## Probabilistic Card Game Analysis

### Ranter-Go-Round Optimal Strategy

![liza-pooor-QHutOO4jiRw-unsplash.jpg](Low-Card-Pass%20Strategy%206150e0a026db468682835fe20634a3dd/liza-pooor-QHutOO4jiRw-unsplash.jpg)

I will be using artificial intelligence and machine learning to model a simple card game—commonly referred to as screw-your-neighbor, low-card-pass, or ranter-go-round. The game is written in C++ but our analysis will be done in Python. My ultimate goal is to create something which I can play against and nearly always lose to: a near perfect strategy. 

One strategy I am going to attempt to use is CFR. Counterfactual Regret Minimization 

**Classes:**

LowCardPass()

Contains 

**Functions:**

Questions:

How deterministic is this game? How can we quantify determinism in games? How does a normal player determine which card to keep and which card to swap?

The axioms:

The last play is almost purely probabilistic.

The players can make useful inferences on what to play by observing other players. This is done simply by allowing each player to access a dataset called the play. This poses opportunity for advantage and disadvantage. The dealer swaps each round(play), so could there possibly be correlation with being chosen as dealer and winning? Is the dealer chosen by random chance? What is the expected value, or amount of plays for a single win? How can we determine this numerically? Or could we break the whole system down and model it analytically? 

Revision: the dealer can also access the full remaining deck of cards if the card if their card is unsatisfactory.

Strategies:

Monte-Carlo simulation potentially. Analyze the data to plot it and try to make a rough estimate of its distribution? How will the distribution be? What is the expected distribution of a standard deck of cards? I imagine it would be uniformly distributed. How much of an impact does the simple binary comparison have on whether or not you win the game?

How can we quantify the impact that these choices have on ones’ probability of winning? How can we model the system?

_______________________________________



---
<center>© 2022 Dylan Rollins. Powered by Jekyll and the Minimal Theme.</center>
