# Statistical Decryption Model

A Python project that breaks encrypted messages using ideas borrowed from statistical physics. Rather than treating decryption as a linguistics puzzle, it treats it as an optimisation problem: find the key that produces the most statistically plausible English (or French, or German) text out of a large search space.

Originally built to solve a set of substitution ciphers set as a university project, it ended up going further than that.

The main notebook (`Statistical Decrypter.ipynb`) walks through the whole thing, from a basic Caesar cipher solver up to a general-purpose cipher-breaking pipeline.

## How it works

Starting point: download a large sample of English text (*Moby Dick*, via Project Gutenberg) and use it to work out what real English looks like statistically: how often each letter follows another, and so on.

From there, any candidate decryption can be scored: does it look like real English, or gibberish? A **Metropolis algorithm** (a Monte Carlo method borrowed from statistical physics) then searches for the best-scoring key by repeatedly proposing small changes and accepting or rejecting them — with **simulated annealing** used to control how much randomness is allowed early on versus late on, so the search doesn't get stuck in a bad solution before it's had a chance to explore properly.

## What it can break

* Substitution ciphers, from basic Caesar shifts up to full mono-alphabetic substitution
* Columnar transposition ciphers, by treating column order as the thing being optimised instead of the letters themselves
* Vigenère ciphers, by evolving the key directly

## Beyond the basic version

Plain bigram scoring turned out not to be enough for short messages, so the project grew a few extra pieces to handle them:

* **Trigram modelling** for a sharper (if sparser) statistical model
* **Dictionary scoring**, so the algorithm is rewarded for producing real words, not just plausible letter pairs
* **Automatic language detection**, running the same search across English, French, and German models and keeping whichever one converges on the most plausible result

Across the 12 provided ciphertexts, this got 10 fully solved — the remaining two are short enough that there isn't enough statistical signal in the text to solve them reliably, which the notebook digs into as a limitation of the approach rather than a bug.

## Technologies used

* Python
* pandas
* NumPy
* Matplotlib
* Jupyter Notebook
