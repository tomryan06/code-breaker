# Statistical Decryption Model

This is a Python project from the University of Bristol that decrypts complex substitution ciphers using statistical analysis and optimization algorithms.

The main notebook (`Code Breaker.ipynb`) demonstrates the full process.

## 🚀 Key Features
* **Text Analysis**: Downloads and cleans a large text corpus (*Moby Dick*) to build a statistical model of English.
* **Plausibility Scoring**: Calculates a log-likelihood score for any given text based on bigram (character pair) frequencies.
* **Optimization Algorithm**: Implements a Metropolis (Monte Carlo) algorithm with simulated annealing to automatically search the solution space and converge on the optimal decryption key.
* **Visualization**: Includes analysis of the algorithm's convergence and the impact of its parameters.

## 🛠️ Technologies Used
* Python
* pandas
* numpy
* matplotlib
* Jupyter Notebook
