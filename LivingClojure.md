# Notes on 'Living Clojure' by Carin Meier
# 1. The Structure of Clojure
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
Without a prefix quote, in a Lisp, the first element in a list is treated as an operator or function (IFn.) Other elements are considered data for the operator.

All Clojure code is made of lists. Code is data.

## Symbols and Binding
Clojure uses symbols to represent data, as other languages use variables. Clojure symbols refer to values. 

The (def) function allows us to give something a name, via a var, globally.

Vars are different to variables as their values are not expected to change during the course of the program.  

(def developer "Ada")  
creates a var object in the default namespace, user, for the symbol, developer.

The REPL will evaluate developer to "Ada". We could reference the symbol by its namespace, user/developer but don't need to in this case because user is the default namespace for the REPL.

To make a var that isn't global and is temporary, use (let [symbol value])
"What happens in a let, stays in the let"

(defn) creates vars for functions. It takes the name of the function, a vector of parameters and the body of the function. If there are no parameters, the vector is left empty.

An anonymous function can be expressed with the fn operator. It can be called again by surrounding with parens. There is a shorthand of replacing the fn [] by a # in front of the parens and using numbered percent signs for the parameters.

## Organize Symbols in Namespaces
You create your own namespace and switch to it using ns. Vars created will now be with this namespace.
*ns* tells you the current namespace. It is shown between earmuffs, <>, a convention for things that are intended for rebinding (to change.)

Clojure libs are made up these names and symbols associated with namespaces.

There are 3 ways to use libs using require
(require 'clojure.set)  
(require '[alice.favfoods :as af])
(ns wonderland (require '[alice.favfoods :as af]))
(ns wonderland (require '[alice.favfoods :refer :all]
                        '[alice.favfoods :refer :all])) but risky
 
Most code will use :as, except clojure.test when common to use directly with namespace being tested.

:refer :all is preferred but use is still acceptable.

"we will take this structure of code and make it move and flow with functional transformations.
# 2. Flow and Functional Transformations
Expressions - code that can be evaluated for a result  
Forms - a valid expression that can be evaluated. "it specifies a correct syntax by being valid."

## Controlling Flow with Logic
Clojure has boolean data types true and false.

(class true) tells us they are java.lang.Boolean

We can test (true? true)
(false? false) or (nil? 1)

nil is logically false in tests

# 3. State and Concurrency

# 4.
# 5.
# 6. Communication with core.async

# 7. Creating Web Application with Clojure
Creat a Clojure project with Leiningen  
Use a Clojure library called Compojure.

## Creating a Web Server with Compojure
It provides routing for a lower level web application library called Ring.  
Ring allows web apps to be built in modular components. There is not 1 particular web app framework used in Clojure.  

lein new compojure cheshire-cat
~/Dropbox/Products/cheshire-cat
cd cheshire-cat

It creates a resource/public directory for the web app's images, CSS and JavaScript files and a source and test file, handler.clj

There is a project.clj as well as handler.clj

To start a web server for the application, run:

~/Dropbox/Products/cheshire-cat$ lein ring server
2017-09-07 14:50:04.443:INFO:oejs.Server:jetty-7.6.13.v20130916
2017-09-07 14:50:04.672:INFO:oejs.AbstractConnector:Started SelectChannelConnector@0.0.0.0:3000
Started server on port 3000

and on http://localhost:3000/, the message "Hello World" is written to a browser window.

Leiningen created a Compojure template called src/cheshire_cat/handler.clj

defroutes creates a sequence of HTTP routes called app-routes which the web app will handle.

GET creates an HTTP get route for the base URL, / and returned the string "Hello World".

Also:route/not-found for a basic 404 handler.

App uses handler/site on all routes. Sets up middleware to handle resource files.  
There are many options. See the Ring Defaults library github.com/ring-clojure/ring-defaults

The project.clj ties everything together  
The lein-ring plugin automates common Ring tasks, like starting the web server.

The :ring :handler key tells the startup web server task where to find the main app routes

## Using JSON
There is a Clojure library called Cheshire that creates JSON out of Clojure data strustures.
