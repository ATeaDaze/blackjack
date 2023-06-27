# [Basic Blackjack](https://github.com/ATeaDaze/ateadaze.github.io/tree/main/blackjack)

### A simple blackjack app written in (mostly) native JavaScript. Uses some jQuery for cleaner syntax. No additional libraries or anything fancy

* [**Source Code**](https://github.com/ATeaDaze/ateadaze.github.io/blob/main/blackjack/scripts/main.js) (main.js)
* [**README**](https://github.com/ATeaDaze/ateadaze.github.io/blob/main/blackjack/README.md)

### README and source code are linked so I can host the website on my main repository (I'm still learning GitHub). It has a more complete list of tasks, bugs, and fixes

## [Desktop](https://ateadaze.github.io/blackjack) || [Mobile](https://ateadaze.github.io/blackjack/m)
![blackjack_banner](https://raw.githubusercontent.com/ATeaDaze/ateadaze.github.io/main/blackjack/images/blackjack_banner.png)

## Features
* **Play Blackjack** against a computer-controlled dealer
  * **Dealer stands on all 17's**
  * **Blackjack pays 3:2** odds (150%)
* **Place bets:** $25, $50, $100, $200
* **Double down** if you're feeling lucky
* **Uses six 52-card decks**
  * All dealt cards are tracked to prevent duplicates
  * Deck is shuffled when all 312 cards have been used
* **True count** is displayed on the bottom for card counting
  * Click on the true count if you'd prefer to hide it

## Keyboard Map (desktop only)

&nbsp;|Description|&nbsp;|Bet Amount
---|:--|---|:--
|**` S `** |**Stand:** stop drawing cards and let the dealer play|**` 1 `** |$25
|**` H `** |**Hit:** draw 1 more card|**` 2 `** |$50
|**` D `** |**Double down:** double bet, draw 1 card, and stand|**` 3 `** |$100
|**` N `** |**New hand:** deal a new hand|**` 4 `** |$200

# 💻 [Desktop](https://ateadaze.github.io/blackjack)
![blackjack_screenshot.png](https://raw.githubusercontent.com/ATeaDaze/ateadaze.github.io/main/blackjack/images/blackjack_screenshot.png)

# 📱 [Mobile](https://ateadaze.github.io/blackjack/m/)
![mobile_screenshot](https://raw.githubusercontent.com/ATeaDaze/ateadaze.github.io/main/blackjack/images/blackjack-mobile_screenshot.png)

### Key:
* [TEST] = Added, needs more testing
* [WIP] = Work in progress
* ~~Strikethrough~~ = Fixed or Cancelled

# BUGS

* [x] ~~Occasionally freezes when shuffling deck~~
* [x] ~~Tie at 21 doesn't evaluate until you stand~~
* [x] ~~Some sounds are muted in specific browsers~~

Each browser handles JavaScript sound differently. Some are stricter than others or only play sounds tied to user input
* Firefox on Windows plays all SFX (with audio site permission)
* Chromium-based browsers play all SFX except "card_shuffle.mp3" on page load
* Firefox on Android plays all SFX except "card_flip.mp3" on `hit()`

* [ ] Mobile rendering is inconsistent (but playable)
 

# FIXES

* [x] Occasionally froze when looking for a new card
  * **Cause:** crashed on `shuffleDeck()` if `nTotalCards > 311`
  * **Fix:** created offset to limit range of the check

```javascript
// nTotalCards: number of used cards
// nCardsInPlay: number of cards on the table
// deckSize: size of all decks combined (312)
// decksLeft: number of remaining decks (rounded down to nearest integer)
// fullDeck: array containing all six decks (cards 0:311)
nCardOffset = (deckSize - nCardsInPlay) - 4;

if(nTotalCards > nCardOffset) {
  nTotalCards = 0;
  decksLeft = 6;
  shuffleDeck(fullDeck);
}

```

* [x] [TEST] Ties did not evaluate until `stand()` was called
 * **Cause:** condition was set before `checkFinalScore()` was called
 * **Workaround:** added tie check on `checkForWinners()`

This is a lazy workaround until I completely remake the winner checks and merge `checkFinalScore()` with `checkForWinners()`

