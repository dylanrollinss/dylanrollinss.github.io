# Portfolio
---
## Probabilistic Card Game Analysis

### Ranter-Go-Round Optimal Strategy

![liza-pooor-QHutOO4jiRw-unsplash.jpg](Low-Card-Pass%20Strategy%206150e0a026db468682835fe20634a3dd/liza-pooor-QHutOO4jiRw-unsplash.jpg)

I will be using artificial intelligence and machine learning to model a simple card game—commonly referred to as screw-your-neighbor, low-card-pass, or ranter-go-round. [The game is written in C++](https://github.com/dylanrollinss/LowCardPass) but our analysis will be done in Python. My ultimate goal is to create something which I can play against and nearly always lose to: a near perfect strategy. 

One strategy I am going to attempt to use is CFR. Counterfactual Regret Minimization.
A full description of the game: 2 to N people can play. 52 cards are shuffled and 3 points are given to each of the N players. We denote the deck of cards starting at 52 as D. At the end of each round, the player(s) holding the lowest valued card (between 1-13) lose one point. One player is assigned the role of dealer, and this role is passed in circulation. Imagine a circular linked list; each person sitting at a table points to their left or rightmost neighbor (traditionally left) and after each round, the dealer role travels via the next pointer. The dealer gets the deck of cards, but none of the D cards are visible. The dealer blindly deals 1 card to each of the N players and the initial round begins. Each round starts with the player next from the dealer (using our previously defined circular iterator) Each player has the option to either trade their card with their neighbor (the next element in the circular linked list), or keep their card. There is one clause to this; once the iterator reaches the dealer (the next element is the initial state of the iterator) the dealer can not swap with their neighbor—if the dealer wishes to swap cards, they must draw one card from the top of the stack of cards. This action is binding. They must keep this card. The only case where a player can reject swapping their card is if the player is holding the highest valued card, 13 (king). My analysis hits a schism after this:

There seems to be two ways we could model this system—in table gameplay, you can see whether your opponents keep or pass their cards and you can factor your opponent’s sentiment into whether you want to swap your card or not. This adds another dimension of analysis, since you get the options of bluffing—performing a sleight of hand to trick your opponent into either swapping their card with you (which would potentially give the player 3 sub-trials instead of 2: (their initial card, which they decide whether it is too low in value(1), the player observes their neighbor, who seems content with their card, so the player may decide to attempt to deceive their neighbor into swapping cards by displaying an overly-satisfied state(2), and after this, the player can decide to keep the previous neighbor’s card or swap it with the next neighbor(3)) or not swapping (if your initial card has the value of 12, you want to keep it, but deceive the previous player into thinking it was a low-valued card, so you adopt a dissatisfied state) giving us another set of variables: something like player_card_sentiment : {extremely-satisfied, satisfied, dissatisfied, extremely-dissatisfied}. . . with their card, thereby factoring sentiment into the analysis—however, this would largely increase the possible states the game could adapt.

The other method of analysis would ignore sentiment, thereby being simpler to model and simulate, but possibly at the cost of model efficacy—ignore sentiment and only worry about the value of your card on your turn. In this method, your initial card value is meaningless if your previous neighbor decides to swap cards with you. You still need to decide whether you should pass your card or keep it, though.

The game continues on in this way with all used cards being put into a discard pile after each round until the size of the initial deck Is lower than the number of players, then the discard deck is shuffled and the game continues. The game ends when only one player remains with points.

On to counterfactual-regret-minimization: this method starts with a random strategy and then fine-tunes on each iteration based on which choices it regrets (like human regret-based learning) until it approximately converges to an optimal strategy. Here is a description of the algorithm by one of its creators: https://www.quora.com/What-is-an-intuitive-explanation-of-counterfactual-regret-minimization The algorithm has been used to approximate Nash equilibrium points for other finite games (rock-paper-scissors, etc.) and even to create one of the best poker engines so far (Pluribus). I think this algorithm would be able to able to find a good strategy in both methods of analysis.

_______________________________________



---
<center>© 2022 Dylan Rollins. Powered by Jekyll and the Minimal Theme.</center>
