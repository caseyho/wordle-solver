# wordle-solver-benchmarks
Optimal gameplay benchmarks for various algorithms that can be used to solve Wordle puzzles

## Problem set
Wordle is a word guessing game available at: https://www.powerlanguage.co.uk/wordle/

The list of possible Wordle words can be determined by peeking at Wordle's source code. There are 2315 potential Wordle games, each of which is a fairly common 5-letter English words. There is also a second, larger set of 12972 words containing the majority of 5-letter words that can be found in an English dictionary from which the user can guess from.

## Benchmarks

* Total guesses = the total number of guesses required to solve all 2315 potential Wordle puzzles
* First guess = the first turn of each game is always the same because there is zero information
* Avg turns = the average number of turns required to find a solution
* Std. dev turns = the standard deviation in number of turns per game, roughly measuring consistency
* Max turns = the maximum number of guesses required to find a solution

| Algorithm  | Optimal\* | Max partitions | Max entropy | Minimax (Knuth) |
| ---------- | -------- | -------------- | ----------- | ---------------- |
| Total guesses | 7920 | 7949 | 8023 | 8245 |
| First guess | \[redacted\]\* | TRACE | SOARE | RAISE |
| Avg. turns | 3.4212 | 3.4337 | 3.4657 | 3.5616 |
| Std. dev turns | 0.6105 | 0.6355 | 0.6111 | 0.6528 |
| Max turns | 5 | 6 | 6 | 6 |
| *By Game Length* | | | | |
| 2 turn games | 96 | 78 | 45 | 67 |
| 3 turn games | 1201 | 1249 | 1240 | 1011 |
| 4 turn games | 965 | 895 | 943 | 1108 |
| 5 turn games | 53 | 87 | 81 | 123 |
| 6 turn games | 0 | 5 | 6 | 5 |

* (1) Optimal is based on a recusive search of all potential game states with aggressive pruning. There is a slight possibility that the minimum found (7920) may not represent the true minimum due to the way some game states were pruned. Regardless, the value is posted here to provide a benchmark for anyone attempting to fine-tune their own solution or also find the perfect decision tree. I will update this in the case the true minimum is found to be lower.
* (2) The best starting word is hidden for now. Don't want to spoil all the fun :)

### Hard mode benchmarks

| Algorithm  | Optimal(1) | Max partitions | Max entropy | Minimax (Knuth) |
| ---------- | -------- | -------------- | ----------- | ---------------- |
| Total guesses | TBD | 8179 | 8347 | 8496 |
| First guess | TBD | TRACE | SOARE | RAISE |
| Avg. turns | TBD | 3.5330 | 3.6056 | 3.6700 |
| Std. dev turns | TBD | 0.7982 | 0.7962 | 0.8444 |
| Max turns | TBD | 8 | 8 | 8 |
| *By Game length* | | | | |
| 2 turn games | TBD | 124 | 79 | 108 |
| 3 turn games | TBD | 1091 | 1055 | 908 |
| 4 turn games | TBD | 887 | 945 | 1014 |
| 5 turn games | TBD | 173 | 184 | 220 |
| 6 turn games | TBD | 31 | 42 | 50 |
| 7 turn games | TBD | 6 | 8 | 13 |
| 8 turn games | TBD | 2 | 2 | 1 |

* The same algorithms applied to hard mode fail to solve all words in the allotted six guesses.
* Algorithms were ported over from normal difficulty with only minor changes. Perhaps there are changes available that could increase performance?
* The optimum for hard mode will be made available at a later date once it is computed

## Algorithms

Wordle bears a close resemblance to another game, Mastermind. In both games a player makes a series of attempts to guess a hidden codeword from. For each guess the player receieves some sort of feedback on what that guess is. The player can eventually guess the codework by narrowing down the set of possible codes. Games are scored by the number of turns it takes to guess the codeword.

It is possible to write a generalized solver that finds optimal guessing startegies for both Wordle and Mastermind games.

Information on various algorithms to Mastermind algorithms can be found here: https://en.wikipedia.org/wiki/Mastermind_(board_game)#Algorithms_and_strategies

For the purposes of this solver, meta-gaming (comparing against publicly posted results from other players) is ignored.

## Code

Code for the solver will be posted at a later time


