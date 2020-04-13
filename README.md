# Virtual Scrabble Bag

A website I built while bored in isolation for COVID-19, inspired by [Matt Parker and Vicki Pipe discussing](https://www.youtube.com/watch?v=JaXo_i3ktwM) a more physical solution to the issue of playing Scrabble over a video call during isolation.

[To play, go to the main site.](https://tugzrida.github.io/virtual-scrabble-bag)

The code is(hopefully!) fairly simple to follow with the comments I've added, but here's the basic premise:

- One player generates a 'seed' - in this case two words - which is then entered by the other players(with a third word calculated to check that no one made a typo).
- This seed is used to initialise a [pseudorandom number generator](https://github.com/davidbau/seedrandom), which is essentially an algorithm that devices can use to generate random numbers.
- As an aside - in most uses, pseudorandom number generators (PRNGs) are seeded using a variety of random inputs, such as tiny jitters in mouse movements ([or in one notable case, lava lamps](https://www.youtube.com/watch?v=1cUUfMeOijg)) so that the output is unpredictable, however in this case all players use the same seed, and hence each player will be able to generate the same series of random numbers. For example, if the seed is `correct-horse`, the first random numbers will always be `0.455894426771904`, `0.9044395307384482`, `0.21940549760476766`, etc.
- The numbers from the seeded PRNG are used to randomise a bag of Scrabble tiles (using the [Fisher-Yates Shuffle](https://en.wikipedia.org/wiki/Fisher%E2%80%93Yates_shuffle)). This means that every player now has a bag randomised in the same order, but without knowing the order themselves.
- Now, the players can draw tiles from the virtual bag, however so that multiple people don't get the same tiles, the other players must discard the same number of tiles.

The system isn't perfect, and still requires players to trust each other, but should work nonetheless.
