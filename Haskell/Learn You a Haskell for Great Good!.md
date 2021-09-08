TARGET DECK: Main Deck

What is referential transparency? #fc 
An [expression](https://en.wikipedia.org/wiki/Expression_(programming)) is called referentially transparent if it can be [replaced](https://en.wikipedia.org/wiki/Rewriting "Rewriting") with its corresponding value (and vice-versa) without changing the program's behavior.
<!--ID: 1626656261042-->


What is the command to open up the haskell command prompt: #fc
`ghci`
<!--ID: 1626656261048-->


Boolean `and` in haskell: #fc 
`&&`
<!--ID: 1626656261054-->


Boolean `or` in haskell: #fc 
`||`
<!--ID: 1626656261059-->


Boolean `not` in haskell: #fc
`not`
<!--ID: 1626656261065-->

How to get the successor of a number (Haskell)? #fc 
`succ 8`
<!--ID: 1626695413891-->


What has highest precidence in Haskell? #fc
Prefix function application. ie.
`succ 9*10` -> `100`
<!--ID: 1626695413897-->


How to turn a prefix function with two arguments into an infix function (Haskell)? #fc 
Add two back ticks: `div 100 10` -> 100 \`div\` 10
<!--ID: 1626695413903-->


How to get the nth element out of a list `L` (Haskell)? #fc
`L !! n`
<!--ID: 1626695413909-->


Return a reversed version of a list (Haskell)? #fc
`reverse L`
<!--ID: 1626695413915-->


Return the length of a list (Haskell)? #fc 
`length L`
<!--ID: 1626695413919-->


If statement in (Haskell)? #fc
Must have an else clause:
`if <condition> then <effect1> else <effect2>`. Note that `<>` braces are not actually used in code
<!--ID: 1626695413924-->


How to concatenate lists in Haskell? What do you have to be careful of here? #fc 
`L1 ++ L2`. eg. `[1,2,3,4] ++ [5]`. This could take a long time for a long L1, because haskell has to walk all the way to the end of `L1`
<!--ID: 1626695413929-->

How to check if a list is empty in Haskell? #fc 
`null []` -> True. `null [1,2,3]` -> False
<!--ID: 1626696276362-->



How are strings represented in Haskell? #fc 
As lists of chars. All list methods can be used on them
<!--ID: 1626695413933-->


How to add an element to the beginning of a list in Haskell? #fc 
`5: [1,2,3,4,5]`
<!--ID: 1626695413938-->


When can lists be compared using `<, <=, >, >=` in Haskell? #fc
If the elements they contain can be compared
<!--ID: 1626695413942-->


What do the function `head`, `tail`, `last` and `init` do in Haskell? #fc 
`head`: return the first element of the list
`tail`: Chop the head off and return what is left (of the list)
`last`: Get the last element
`init`: Takes a list and returns everything but the last element
<!--ID: 1626695413947-->

What do `take`, `drop`, and `elem` do to a list in Haskell? #fc 
`take 2 [1,2,3,4,5,6]` -> `[1,2]`: extracts `n` elements from the beginning of `L`
`drop 2 [1,2,3,4,5,6]` -> `[3,4,5,6]`: drops `n` elements from the beginning of `L` and returns the result
`elem 4 [1,2,3,5]` -> `False`: returns if `n` is an element in `L`.
<!--ID: 1626696276368-->


How to make a list of the numbers from 20 to 1 in reverse order in haskell? #fc 
`[20, 19 .. 1]` 
<!--ID: 1626696276374-->


How to make an alphabet string in Haskell? #fc 
`['a'..'z']`
<!--ID: 1626696276379-->


How to get the first `24` multiples of `12` in haskell (use infinite list ranges)? #fc 
`take 24 [12,24..]` (remember Haskell is lazy, so it doesn't have to actually create the infinite list)
<!--ID: 1626696276384-->


What do `cycle` and `repeat` do in Haskell? #fc 
`cycle [1,2,3]` -> `[1,2,3,1,2,3, ...]` cycles a list infinitly many times.
`repeat 1` repeats an element in a list infinitly may times
<!--ID: 1626696276390-->


What does `replicate` do in haskell? #fc 
`replicate 3 10` -> `[10, 10, 10]`
<!--ID: 1626696276395-->

Get all even numbers greater than `12` and less than or equal to `20` using a list comprehension in Haskell. #fc
`[x | x <- [1..20], (mod x 2) == 0, x > 12]`
<!--ID: 1626706959103-->





