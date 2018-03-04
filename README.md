# Blackjack

## initial
### player1:
##### step1: draw two cards (Query)

```
(and 
(indexOf ?c1 0) 
(hasValue ?c1 ?val1) 
(indexOf ?c2 1)
(hasValue ?c2 ?val2) 
(evaluate ?ans (PlusFn ?val1 ?val2)))
```

##### step2:update currentSumP1 (Context: CardsMt; tell)
```
(currentSumP1 ans)
```

### player2: 
##### step1: draw two cards (Query)

```
(and 
(indexOf ?c1 2) 
(hasValue ?c1 ?val1) 
(indexOf ?c2 3)
(hasValue ?c2 ?val2) 
(evaluate ?ans (PlusFn ?val1 ?val2)))
```

##### step2:update currentSumP2 (Context: CardsMt; tell)
```
(currentSumP2 ans) 
```


## (draw card) optional  
### player1: 
##### step1: draw one card (Query)

```
(and (indexOf ?c1 4) (hasValue ?c1 ?val1) (currentSumP1 ?val2)
     (evaluate ?ans (PlusFn ?val1 ?val2)))
```

##### step2: update currentSumP1
```
(currentSumP1 ans)   --- (Context: CardsMt; tell)
(currentSumP1 ans*)  --- (Context: CardsMt; untell)

```

  
### Player2: 
##### step1: draw one card (Query)
```
(and (indexOf ?c1 5) (hasValue ?c1 ?val1) (currentSumP1 ?val2)
     (evaluate ?ans (PlusFn ?val1 ?val2)))
```

##### step2: update currentSumP2
```
(currentSumP2 ans)   ---(Context: CardsMt; tell)
(currentSumP2 ans*)  ---(Context: CardsMt; untell) 
```

## Result
### Player1 (true: Player1 wins; None Found: Player1 loses):
```
(and (currentSumP1 ?val1) (currentSumP2 ?val2) (winsP1 ?val1 ?val2))
```
### Player2 (true: Player2 wins; None Found: Player2 loses):
```
(and (currentSumP1 ?val1) (currentSumP2 ?val2) (winsP2 ?val1 ?val2))
```


