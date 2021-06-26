# 🧬 Genetic Algo_Re

- Genetic algorithms are inspired by natural selection -> evolutionary algorithms @https://en.wikipedia.org/wiki/Evolutionary_algorithm
- optimization and search are primary cases, rely on mutation, crossover, and selection (inspired by biology)
    - genetic representation: bitstrings
    - fitness (function and evaluations) as F
    - genetic recombination (crossover of bitstring)
    - mutation rate (flipping bits) as M
- first works by creaeting fixed size of random bitstrings (almost like initialization), one iteration is an evolutionary generation or per epoch
- new algorithms or parent algos based on their fitness -> F(x) = O(x^i for i in len[candidate solutions])
- hyperparameter 'k' involves picking k-best out of population and creating tournament-style groups based on random generation *natural selection
- the parents are used for generating NG of candidate points through recombination -> 2 parent algos = 2 child algos using crossover operation
    - Crossover: select random split point of bit string, then create child with bits up to split point from P1 + after split point of P2 for C1, vice_versa for C2
    - P1 = 00000
    - P2 = 11111
    - if split point = idx(2)
        - C1 = 00011
        - C2 = 11100
- ^ above is called one-point, but you can have multiple point crossovers and applied probabilitically for each pair of parents
    - copies of parents are taken as children instead of recombination operator/crossover
    - crossover can be controlled with hyperparameter of percent to indicate likeliness (80-90%)
- creating artificial mutations involves flpping bits -> M = 1/L where M is mutation rate and L is length of btstring 
    - each bit has small probability of being flipped, or 1 mutation per child
- the goal is to essentially optimize some function to map an input to an output (tuning)
- turning the function needs to become some sort of representation that can be tuned, need to optimize the cost function landscape to get to the global minimum essentially
- genetic algorithm is sampling the potential parameters to get to an optimal position (think monte carlo)

TLDR: Genetic algorithms are a way to search a high-dimensional parameter space to optimize a model once you have a set of known parameters that can be finetuned with a desired output
- you want to sort the candidate inputs by their cost function (best to worst) and then use that objective function to determine which candidates will pass through in the next gen. 

## Choosing Genetic Operations
1. Elitism: choose the best candidate with the highest fitness/lowest cost function value and only keep that to copy over
2. Replication: similar to elitism but random selection from probability
3. Crossover: take two high-performing candidates and cross their values at a split-point to create 2 new children candidates (crossing over strengths and removing weakenesses)
4. Mutation: take any candidate and swap a bit value(s) randomly and then evaluate the fitness 

* mutation is exploratory in parameter space whereas crossover is better at converging through exploitation

- the goal is to have a good mix of all of these functions -> have a rate per each operation and decide which operations will occur
- after operations, use probability based on fitness to then choose new candidates and the cycle repeats -> pick best performers and map
- the mixture of these operations allows you to have a more exploratory or exploitary diretion at certain parts 
