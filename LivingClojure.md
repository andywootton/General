# Notes on 'Living Clojure' by Carin Meier
Expressions
## Simple values / Literals
Integer 3 ;; and this is a comment  
Decimal 5.78  
Ratio 2/3, different to (/ 2 3) which is code - a function call  
String "Ball of"  
Keywords :jam  
Char \d  
Boolean true   
Nothing nil  
## Collections
All collections are immutable and persistant. Values in a collection are not changed, the structures are extended with new values, by structural sharing. 
###list '()
Lists are for collections of data you want to access from the top.  
List '(2 4 "knock at" :door) ;; can use , but it is idiomatic not to.  
(first) (rest)
(cons)  
e.g. (cons 3 nil) ;; -> (3). Lists end with nil.
###vector []
Access anywhere by position / index: vector [3 "Fred" :home]  
(nth)  
e.g. (nth ["fish" 4 :Day] 2)  
;; -> :Day  
(last) ;; both work with lists too but are faster with vectors

We have seen that collection support the sequence functions first, rest and last.  
(count [1 2 3 4]) ;; returns the size of a collection.  
(conj) ;; adds elements, using the most natural way for the data structure; to the start of lists, the end of vectors

###map {}
Maps store key-value pairs of data.  
{:jam1 "Strawberry" :jam2 "Blackberry"}

(get {:jam1 "Strawberry" :jam2 "Blackberry"} :jam2)

Provide a default if key not found:    
(get {:jam1 "Strawberry" :jam2 "Blackberry"} :jam3 "Not found")

It is more idiomatic to use the key as a function:  
(:jam2 {:jam1 "Strawberry" :jam2 "Blackberry" :jam3 "Blackcurrent"} "Not found")

(keys) and (vals) return just the keys or values of the map.  
To update maps:
(assoc)  
(dissoc)  
(merge)  
###set #{}
Useful for collections of elements with no duplicates

(clojure.set/union) /difference /intersection

(set) converts other collections to sets

(get) works, or if a keyword, then as a function call, like maps.

(contains?) checks if a set contains an element

(conj) works  
(disj) removes elements from sets
## Lists as Code
(function param1 param2)
## Symbols and Binding