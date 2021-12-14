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

        
## Ord

```haskell
class (Eq a) => Ord a where
    compare                 :: a -> a -> Ordering
    (<), (<=), (>=), (>)    :: a -> a -> Bool
    max, min                :: a -> a -> a
    
    compare x y | x == y    = EQ
                | x <= y    = LT
                | otherwise = GT
                
    x <= y  = compare x y   /= GT
    x < y   = compare x y   == LT
    x >= y  = compare x y   /= LT
    x > y   = compare x y   == GT
    
    -- Note that (min x y, max x xy = (x, y) or (y, x)
    max x y | x <= y    = y
            | otherwise = x
    min x y | x <= y    = x
            | otherwise = y
```

All basic datatypes except for functions, IO and IOError

## Read & Show

```haskell
type ReadS a    = String -> [(a, String)]
type ShowS      = String -> String

class Read a where
    readsPrec :: Int -> ReadS a
    readList  :: ReadS [a]
    -- ... default decl for readList given in prelude
    
class Show a where
    showsPrec   :: Int -> a -> ShowS
    show        :: a -> String
    showList    :: [a] -> ShowS
    
    showsPrec _ x s = show x ++ s
    show x          = showswPrec 0 x ""
    -- ... default decl for showList given in Prelude
```

All Prelude types, except function types and IO types.

For convenience, the Prelude provides the following auxiliary functions:

```haskell
reads   :: (Read a) => ReadS a
reads   = readsPrec 0

shows   :: (Show a) => a -> ShowS
shows   = showsPrec 0

read    :: (Read a) => String -> a
read s  = case [x | (x, t) <- reads s, ("", "") <- lex t] of
            [x] -> x
            []  -> error "PreludeText.read: no parse"
            _   -> error "PreludeText.read: ambiguous parse"
```

The function lex :: ReadS String, is also part of Prelude. It reads a single lexeme from the input, discarding initial whitespace, and returning the characters that constitute the lexeme.

## Enum

```haskell
class Enum a where
    succ, pred      :: a -> a
    toEnum          :: Int -> a
    fromEnum        :: a -> Int
    enumFrom        :: a -> [a]             -- [n..]
    enumFromThen    :: a -> a -> [a]        -- [n, n'..]
    enumFromTo      :: a -> a -> [a]        -- [n..m]
    enumFromThenTo  :: a -> a -> a -> [a]   -- [n, n'..m]
    
    -- Defautl declarations given in Prelude
``` 

* Enumeration types: (), Bool, Ordering.
* Char
* Numeric types: Int, Integer, Float, Double.

## Functor

```haskell
class Functor f where
    fmap    :: (a -> b) -> f a -> fb
```
Lists, IO, and Maybe

Instances should satisfy the following laws:
```haskell
fmap id         = id
fmap (f . g)    = fmap f . fmap g
```

## Monad

```haskell
class Monad m where
    (>>=)       :: m a -> (a -> m b) -> m b
    (>>)        :: m a -> m b -> m b
    return      :: a -> m a
    fail        :: String -> m a
    
    m >> k  = m >>= \_ -> k
    fail s  = error s
```

Lists, Maybe, and IO. fail returns [], Nothing and exception respectively
Instances should satisfy the following laws:

```haskell
return a >>= k          = k a
m >>= return            = m
m >>= (\x -> k x >>= h) = (m >>= k) >>= h
```

Instances of both Monad and Functor should additionally satisfy the law:

```haskell
fmap f xs = xs >>= return . f
```

All instances of Monad defined in Prelude satisfy these laws.

Prelude provides also the following functions.

```haskell
sequence    :: Monad m => [m a] -> m [a]
sequence_   :: Monad m => [m a] -> m ()
mapM        :: Monad m => (a -> m b) -> [a] -> m [b]
mapM_       :: Monad m => (a -> m b) -> [a] -> m ()
(=<<)       :: Monad m => (a -> m b) -> m a -> m b
```

## Bounded

```haskell
class Bounded a where
    minBound, maxBound :: a
```

Int, Char, Bool, (), and all tuples.
