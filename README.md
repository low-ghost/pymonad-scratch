# pymonad-scratch
just some notes for monad implementation in python

##Monoids
mappend infix is <>
Sum + Product for integer
First and Last for Maybe monad:
example:
```haskell
Last Nothing <> Last (Just 2)
-- Last {getLast = Just 2}
```
###laws
```haskell
-- left identity
mappend mempty x = x
-- right identity
mappend x mempty = x
-- associativity
mappend x (mappend y z) = mappend (mappend x y) z
mconcat = foldr mappend mempty
```

### more examples:
```haskell
(Sum 1 <> Sum 2) <> (Sum 3)
-- Sum {getSum = 6}
-- mconcat same as foldr mappend mempty:
mconcat [Sum 1, Sum 2, Sum 3]
-- Sum {getSum = 6}
```

Any and all
```haskell
All True <> All False
-- All {getAll = False}
Any True <> Any False
-- Any {getAny = True}
```
