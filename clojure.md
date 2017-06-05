# Learning Clojure

I followed the instruction in 'Clojure for the Brave and True' to get a working emacs, CIDER & Leiningen configuration 
to hack on Clojure. I could now get a REPL by typing:  
lein repl  
but I didn't really understand how. I get why beginners may need to be protected from the complexity 
of the Clojure environment but it's not my first time at the redeo and I'm left feeling that I don't know what's going on. I'm not ready to accept that it's all done with magic. I'm not even in Lisp yet.

https://clojure.org/reference/repl_and_main tells me:  

"The simplest way to launch a Clojure repl is to use the following command line from within Clojure’s home directory:

java -cp clojure.jar clojure.main"

Where's that then? The Leiningen install script which I stored in ~/bin/leiningen seems to tell me it's put it in:  
~/.lein/self-installs
so I 'cd' there and type:  
~/.lein/self-installs$ java -cp leiningen-2.7.1-standalone.jar clojure.main

I'm working on the theory that Clojure is embedded inside the Leiningen .jar file. It works! I get a prompt:
Clojure 1.8.0  
and I got it much quicker than 'lein repl' would give it, but I've seen less output than.
I've obviously taken a shortcut.  
