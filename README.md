# 🃏 [Basic Blackjack](https://github.com/ATeaDaze/ateadaze.github.io/tree/main/blackjack)

### A simple blackjack app written in (mostly) native JavaScript. Uses some jQuery for cleaner syntax. No additional libraries or anything fancy

## 💻 [Desktop](https://ateadaze.github.io/blackjack) | 📱 [Mobile](https://ateadaze.github.io/blackjack/m)
![blackjack_banner](https://raw.githubusercontent.com/ATeaDaze/ateadaze.github.io/main/blackjack/images/blackjack_banner.png)

## Features
* **Play blackjack** against a computer-controlled dealer
  * **Dealer stands on all 17's**
  * **Blackjack pays 3:2** odds (150%)
* **Place bets:** $25, $50, $100, $200
* **Double down** if you're feeling lucky
* **Uses six 52-card decks**
  * All dealt cards are tracked to prevent duplicates
  * Deck is shuffled before all 312 cards have been used
* **True count** is displayed on the bottom for card counting
  * **Running count** is displayed when you hover over the true count
  * Click the true count if you'd like to hide it

## Keyboard Map (desktop)

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
// nTotalCards: total cards used by both players (per deck)
// nCardsInPlay: number of cards on the table (per hand)
// deckSize: size of all decks combined (312)
// decksLeft: number of remaining decks (1:6)
// fullDeck: array containing all six decks (0:311)

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

# TODO

## General
* [ ] [WIP] Get rid of extraneous code and optimize
  * [ ] Player strings and text: `number()`, `toLocale()`, `slice()`
  * [ ] Repeated strings/operations
  * [ ] Hideous if/else blocks
* [ ] [WIP] Clean up code with jQuery
* [x] [TEST] Make mobile version
* [ ] Add a split feature
    * [ ] This will require a 2nd game board for each player
      * Make the cards smaller, change scaling, or re-orient the game board

## Card Deck Generation
* [x] Generate 2 to 6 decks
 * [x] Combine decks into a single pool of 312
* [x] Track number of aces to subtract 10 if over 21

## Winner Checks
* [ ] Combine and clean up checks
    * `checkForWins()`
    * `checkFinalScore()`
  * [ ] Use priority order to optimize checks

## Score Calculation
* [ ] [WIP] Optimize `getCardValue()`
* [ ] Calcuate ace values with a single function
* [ ] [TEST] Check win condition for rare double bust
* [x] [TEST] Properly handle rare double blackjack
* [ ] [WIP] Handle ties better
* [x] Handle Blackjack vs regular 21 (Blackjack wins over 21)

## Dealer
* [ ] Change dealer strategy
  * [ ] Draw to 16
  * [ ] Stand on 17
   * Basic strategy: when does a dealer hit on 16?

This doesn't seem significantly different than simply drawing to 17

## Settings / Save
* [ ] Expand the settings menu (similar to help popup)
* [ ] Save settings: sound, true count visibility, bet amount (use local storage)
* [ ] Save game progress: cards, scores, money, true count, running count, flags

## User Interface
* [ ] Update UI to properly render on a wider variety of devices
  * Refresh my knowledge of CSS: viewport, vh, absolute/relative, etc. 
  * This could make the mobile port redundant if done properly 
* [x] [TEST] Display true count (card counting)
  * `True count = (running count / decks remaining)` 
* [ ] [WIP] Use images for all buttons
* [x] Add sound effects
  * [x] Add button to disable sound effects
* [x] Add help menu with instructions and rules
* [x] Make bet buttons look like casino chips
 * [ ] Lower image sizes to improve loading time
* [x] Add bet amount buttons
  * [ ] Add buttons to increase/decrease bet by X dollars
* [x] Add double down button
  * [x] Disable button with > 2 cards (standard casino rule)
* [x] Add a help menu (simple popup with hide/close buttons)

# POSSIBLE BUG

**NOTE:** Blackjack typically used 2 to 8 decks shuffled together

* [ ] (Rare) Duplicate cards are dealt when deck is shuffled (duplicates don't carry over)
  * [ ] Possible fix: force a shuffle after current hand if < X cards remain
  * [ ] Decrease `nCardOffset` by more than `4`

# 📆 Legacy Version
### The oldest _working_ copy of this app: 💻 [Desktop](https://ateadaze.github.io/blackjack/legacy/index.html)

|Version |Date   |
|--------|-------|
|Legacy  |5-15-23|
|Current |11-8-23|

![blackjack_legacy_banner](/blackjack/images/blackjack_legacy-header.png)


