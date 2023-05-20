# TODO

```
Key: [x]=Done, [t]=Added, needs more testing, [w]=WIP, [o]=Needs optimization, [-]=Cancelled

[w] Bet buttons
[x] Make bet buttons look like casino chips (CSS circles or images)
[ ] Generate 2 decks: deck2 = deck1, shuffle(deck2)
[t] Track number of aces to subtract 10 if over 21
[t] Push when both scores are 21 but not blackjack
[ ] Add values for card counting
[x] Add double down button
  [x] Disable double down with >= 3 cards

[ ] Add 2 to 5 more decks
[ ] Get rid of extraneous code
  [ ] Cleaning card strings/text
  [ ] Repeated strings/operations
  [ ] Combine and clean up winner checks
    [ ] checkForWins()
    [ ] checkFinalScore()

[ ] Change dealer strategy: draw to 16, stand on 17
  [ ] When to hit on 16?
[-] Add bet amount buttons (+10/-10, +50/-50)
[w] Clean up code with jQuery
[ ] Add split function

[w] Evaluate
  [o] Check for win conditions
  [t] Handle ties better
  [t] Test evaluation for double blackjack
  [t] Handle Blackjack vs regular 21 (Blackjack wins over 21)

[w] Make mobile version (smaller screen)

```

# BUGS

```
[ ] Tie at 21 doesn't evaluate until you stand
[ ] Infrequent freezes when looking for new card
  [ ] Need to optimize fineUniqueCard()
  [ ] Clean up the card check
  [ ] Possibly hitting an out-of-range array value
```


# Function Outline

## Main
```
mainGameLoop()
  generateCardDeck()
  getKeyboardInput()
  shuffleCardDeck()
```
## Deal Card and Find Value
```
drawPlayerCard()
drawDealerCard()
  findUniqueCard()
  cleanCardString()
  getCardValue()
```
### Update Score and Game Board
```
updateScore()
updateCards()
```
#### Check for Winners
```
  checkForWins()
  checkFinalScore()
```
## Player Actions
```
doubleDown()
stand()
  endCurrentRound()
```
## Miscellaneous
```
restartGame()
  clearScoreboard()
reloadPage()
```

# COLOR LIST
```
card deck red:    #FF5555
card deck black:  #333333

red:              #ff0000
pale red:         #ff3232

indianred:        #cd5c5c
pale indianred:   #f26d6d

chartreuse:   
pale chartreuse:   #afff60
```
