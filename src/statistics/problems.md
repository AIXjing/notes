# Common problems

## 1 Problems about counting

**Probability that a five-card hand contains**

*a standard 52-card deck with four suits (Clubs, Diamonds, Hearts, and Spades) and thirteen ranks (2,..., 10, jack, Queen, King, and Ace)*

#ways of selecting 5 cards from 52 cards: \\(\binom{52}{5}\\)

1. the ace of diamonds

    #ways that the ace of diamonds was selected in 5 cards (i.e., select four other cards from the remaining 51 cards): \\(1 \times \binom{51}{4}\\)

    \\(P = \frac{1 \times \binom{51}{4}}{\binom{52}{5}}\\)

2. at least an ace

    Which is easier to calculate the compensate - counting #ways of no ace: \\(\binom{48}{5}\\)

    \\(P = 1 - \frac{\binom{48}{5}}{\binom{52}{5}}\\)

3. at least a diamond

    #ways of no diamond: \\(\binom{39}{5}\\)

    \\(P = 1 - \frac{\binom{39}{5}}{\binom{52}{5}}\\)

4. the probability that two cards drawn from a standard deck without replacement have the same rank

    #ways of selecting two cards: \\(\binom{52}{2}\\)

    #ways of selecting two cards in the same rank: \\(\binom{13}{1}\binom{4}{2}\\)

    \\(P = \frac{\binom{13}{1}\binom{4}{2}}{\binom{52}{2}}\\)