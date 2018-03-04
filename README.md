# Blackjack

## initial
### player1:
##### step1: draw two cards

```
(and 
(indexOf ?c1 0) 
(hasValue ?c1 ?val1) 
(indexOf ?c2 1)
(hasValue ?c2 ?val2) 
(evaluate ?ans (PlusFn ?val1 ?val2)))
```

##### step2:update currentSumP1
```
(currentSumP1 NUM) 
```

### player2: 
##### step1: draw two cards

```
(and 
(indexOf ?c1 2) 
(hasValue ?c1 ?val1) 
(indexOf ?c2 3)
(hasValue ?c2 ?val2) 
(evaluate ?ans (PlusFn ?val1 ?val2)))
```

##### step2:update currentSumP2
```
(currentSumP2 NUM) 
```


## (draw card) optional  
### player1: 
##### step1: draw one card

```
(and (indexOf ?c1 4) (hasValue ?c1 ?val1) (currentSumP1 ?val2)
     (evaluate ?ans (PlusFn ?val1 ?val2)))
```

##### step2: update currentSumP1
```
(currentSumP1 NUM) 
```

  
### Player2: 
##### step1: draw one card
```
(and (indexOf ?c1 5) (hasValue ?c1 ?val1) (currentSumP1 ?val2)
     (evaluate ?ans (PlusFn ?val1 ?val2)))
```

##### step2: update currentSumP2
```
(currentSumP2 NUM) 
```

## Result
### Player1:
```
(winsP1 currentSumP1 currentSumP2)
```
### Player2:
```
(winsP2 currentSumP1 currentSumP2)
```


