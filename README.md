# [Basic Blackjack](https://github.com/ATeaDaze/ateadaze.github.io/tree/main/blackjack)

### A simple blackjack app written in (mostly) native JavaScript. Uses some jQuery for cleaner syntax. No additional libraries or anything fancy

* [**Source Code**](https://github.com/ATeaDaze/ateadaze.github.io/blob/main/blackjack/scripts/main.js) (main.js)
* [**README**](https://github.com/ATeaDaze/ateadaze.github.io/blob/main/blackjack/README.md)

README and source code are linked so I can host the website on my main repo (I'm still learning the details of GitHub)

## [Desktop](https://ateadaze.github.io/blackjack) || [Mobile](https://ateadaze.github.io/blackjack/m)
![blackjack_banner](https://github.com/ATeaDaze/ateadaze.github.io/raw/main/blackjack/images/blackjack_banner.png)

## Features
* **Play Blackjack** against a computer-controlled dealer
  * **Dealer stands on all 17's**
  * **Blackjack pays 3:2** odds (150%)
* **Place bets:** $25, $50, $100, $200
* **Double Down** if you're feeling lucky
* **Uses two 52-card decks:** no duplicate cards drawn

# Desktop 💻 [ateadaze.github.io/blackjack](https://ateadaze.github.io/blackjack)
![blackjack_screenshot.png](https://github.com/ATeaDaze/ateadaze.github.io/raw/main/blackjack/images/blackjack_screenshot.png)

## Keyboard Map

Key|&nbsp;|Description
---|:--|:--
|**` S `**|Stand| Stop dealing cards to the player and let the dealer play their hand
|**` H `**|Hit| Deal 1 card to the player
|**` D `**|Double down| Double your bet, deal 1 more card, and stand
|**` N `**|Deal| Start a new hand

# 📱 [Mobile](https://ateadaze.github.io/blackjack/m/)
![mobile_screenshot](https://github.com/ATeaDaze/ateadaze.github.io/raw/main/blackjack/images/blackjack-mobile_screenshot.png)

# BUGS

* [ ] Tie at 21 doesn't evaluate until you stand
* [ ] Mobile rendering is inconsistent (but playable)
* [x] ~~Some sounds are muted in specific browsers~~
  * Each browser handles JavaScript sound differently
  * Some are stricter than others or only play sounds tied to user input

# FIXES

* [x] Occasionally froze when looking for a unique card
  * **Cause:** crashed on `shuffleDeck()` if `nTotalCards > 51`
  * **Fix:** created offset to limit range of the check

```javascript
// nTotalCards (number of cards used)
// nCardsInPlay (number of cards on the table)
nCardOffset = (52 - ncardsInPlay) - 4

if(nTotalCards > nCardOffset) {
  swapDecks(currentDeck);
  shuffleDeck(currentDeck);
}
```

## Full list of tasks, bugs, and fixes can be found on the main [README](https://github.com/ATeaDaze/ateadaze.github.io/tree/main/blackjack)
