# Instances
- Monad Complex
- Monad Identity
- Monad First
- Monad Last
- Monad Down
- Monad First
- Monad Last
- Monad Max
- Monad Min
- Monad Dual
- Monad Product
- Monad Sum
- Monad STM
- Monad NoIO
- Monad Part1
- Monad ReadP
- Monad ReadPrec
- Monad IO
- Monad NonEmpty
- Monad Solo
- Monad []
- Monad m => Monad (WrappedMonad m)
- ArrowApply a => Monad (ArrowMonad a)
- Monad (ST s)
- Monad (Either e)
- ... Etc. TODO

A simple example

```haskell
toStr :: Int -> [Char]
toStr 0 = "Cero"
toStr 1 = "Uno"
toStr _ = "Muchos"

GHCI> [1] >>= toStr
"Uno"
```


