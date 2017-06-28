# Learning Clojure

I followed the instruction in 'Clojure for the Brave and True' to get a working emacs, CIDER & Leiningen configuration to develop in Clojure. I could now get a REPL by typing:

lein repl

but I didn't really understand how. I get why beginners may need to be protected from the complexity 
of the Clojure environment but it's not my first time at the rodeo so I'm left feeling I don't know what's going on. I'm not ready to accept that it's all done with magic until I'm in the Lisp environment!

https://clojure.org/reference/repl_and_main tells me:  

"The simplest way to launch a Clojure repl is to use the following command line from within Clojure’s home directory:  
java -cp clojure.jar clojure.main"

We're asking java to run the clojure.jar file in the Java Virtual Machine then run clojure.main

Where's Clojure's home directory? The Leiningen install script which I stored in

~/bin/leiningen

seems to have put things in:

~/.lein/self-installs

so I 'cd' there and type:  

~/.lein/self-installs$ java -cp leiningen-2.7.1-standalone.jar clojure.main

I'm working on the theory that Clojure is embedded inside the Leiningen .jar file. It works! I get a prompt:

Clojure 1.8.0

and I get it much quicker, but with less output. 'lein repl' gives:

nREPL server started on port 41262 on host 127.0.0.1 - nrepl://127.0.0.1:41262  
REPL-y 0.3.7, nREPL 0.2.12  
Clojure 1.8.0  
OpenJDK 64-Bit Server VM 1.8.0_131-8u131-b11-0ubuntu1.16.04.2-b11
    Docs: (doc function-name-here)  
          (find-doc "part-of-name-here")  
  Source: (source function-name-here)  
 Javadoc: (javadoc java-object-or-class-here)  
    Exit: Control+D or (exit) or (quit)  
 Results: Stored in vars *1, *2, *3, an exception in *e
 
I seem to have skipped some of Leiningen's environmental set-up.
