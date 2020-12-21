# What are functors?

* Introduction
* Functors
* Going forward
* Resources

## Introduction
In Haskell a functor is a functional representation of different Types which can be mapped over. It is a high level concept of implementing polymorphism. According to Haskell developers, all the Types such as List, Map, Tree, etc. are the instance of the Haskell Functor.

## Functors
The functor typeclass is basically for things that can be mapped over. To understand how it works here is it's implementation below.
```Haskell
class Functor f where  
    fmap :: (a -> b) -> f a -> f b  
```

This class defines fmap where f is not a concrete type (Int, Bool or String), but a type constructor that takes one type parameter. 

Let's look at some examples to understand better. fmap is similar to the map class, map :: (a -> b) -> [a] -> [b] which takes a list of one type and returns a list of another type. This map class is in fact a functor, it is simply an fmap that works only on lists. Here is another example:
```Haskell
    instance Functor [] where  
        fmap = map  
 ```
 
Since for lists, fmap is just map, we get the same results when using them on lists.
    ```Haskell
    map :: (a -> b) -> [a] -> [b]  
    ghci> fmap (*2) [1..3]  
    [2,4,6]  
    ghci> map (*2) [1..3]  
    [2,4,6]
    ```

Another instance of a functor could come from replacing f with Maybe and we get the following signature for fmapL

    fmap :: (a -> b) -> Maybe a -> Maybe b

    instance Functor Maybe where
        fmap f Nothing  = Nothing
        fmap f (Just x) = Just (f x)
    

Maps from Data.Map can also be a functor because they hold values. In the case of Map k v, fmap will map a function v -> v' over a map of type Map k v and return a map of type Map k v'.

## Going forward
With the Functor typeclass, we've seen how typeclasses can represent higher-order concepts. And with that congratulations! You made it through these 10 blogs regarding Haskell and functional programming. I hope you have learned some interesting new things along the way, were challanged, and ultimately are excited to continue expanding your understanding of functional programming even more.

## Resources
* http://learnyouahaskell.com/making-our-own-types-and-typeclasses#the-functor-typeclass
* https://wiki.haskell.org/Functor
* http://www.haskellforall.com/2012/09/the-functor-design-pattern.html
* https://en.wikibooks.org/wiki/Haskell/The_Functor_class