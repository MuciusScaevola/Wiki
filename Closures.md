A closure (lexical closure, function closure), is a technique for implementing lexically scoped name binding.
Operationally, a closure is a record storing a function with an environment.

_From: https://wiki.haskell.org/Closure_
A closure, the oposite of a [Combinator](Combinator), is a function that make use of free variables in it definition. It 'closes' around some portion of its environment.
E.G.:
```haskell
f x = (\y -> x + y)
```
f returns a closure, because the variable x, which is bound outside the lambda abstraction is used inside its definition.
An interesting side note: the context in which x was bound shouldn't even exist anymore, and wouldn't, had the lambda abstraction not closed around x.

```hakell
f x = (\y -> y * x)
f 4 5
-- 20

-- or
g x = (\y -> y * x) 4           -- x = 4
g 5                             -- y = 5 
-- 20
```
