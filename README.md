# 🃏 Card Shuffling — Shannon Entropy Analysis

This project explores a simple question : **is there a best way to shuffle a deck of cards ?**

To answer it, we compare several shuffling methods using **Shannon entropy** as a measure of randomness. The higher the entropy, the more unpredictable the deck — and the better the shuffle.

## Methods compared

| Method | Description |
|---|---|
| **Overhand shuffle** | Small packets are repeatedly moved from top to bottom |
| **Riffle shuffle (GSR)** | The deck is cut in two and the halves are interleaved (Gilbert-Shannon-Reeds model) |
| **Fisher-Yates** | Algorithmic reference — produces a perfectly uniform random permutation in O(n) |
| **My shuffle** | A contiguous block is extracted from the middle and redistributed alternately to the top and bottom |

## Entropy measure

For each shuffling method, we run a **Monte-Carlo simulation** : starting from a fresh sorted deck, the shuffle is repeated $N$ times. For each card $c$, we estimate the empirical distribution of its final position $p_c(j)$, then compute its Shannon entropy :

$$H(c) = -\sum_{j=0}^{51} p_c(j) \log_2 p_c(j)$$

The global entropy of the deck is the average over all 52 cards. It ranges from **0 bits** (no shuffling, deck stays sorted) to **log₂(52) ≈ 5.70 bits** (perfectly random).

## Project structure

```
.
├── card_shuffling.ipynb   # Main notebook — full analysis and visualizations
└── README.md
```

## Requirements

```bash
pip install numpy matplotlib
```