Some examples

## With infix functions

```haskell
GHCI> paExample1 = (!!) "dog"
GHCI> paExample1 2
'g'

GHCI> paExample2 = ("dog" !!)
GHCI> paExample2 2
'g'

GHCI> paExample3 = (!! 2)
GHCI> paExample3 "dog"
'g'
```
