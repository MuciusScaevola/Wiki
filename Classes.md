# Classes

    ![Classes](./images/haskell_classes.png)
    
## Eq

```haskell
class Eq where
    (==), (/=) :: a -> a -> Bool
    
    x /= y = not (x == y)
    x == y = not (x /= y)
```

All basic datatypes except for functions and IO
