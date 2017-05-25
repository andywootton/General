# Developing Clojure with emacs and CIDER
### Keys
C- maps to Ctrl on a Windows keyboard  
M- maps to Alt on a Windows keyboard & Option on Mac  
## Customisations
Make the modifications suggested in 'Clojure for the Brave and True'

Edit ~/.emacs.d/customizations/ui.el  
e.g. line 37 defines window size

## The REPL
### In a terminal
lein repl

### In emacs with Cider
The emacs Cider package https://github.com/clojure-emacs/cider/  
can be installed manually by emacs 'M-x package-install' then entering 'cider'.  

Open a file containing Clojure code, file-type .clj then:  
M-x cider-jack-in   
or  
C-c M-j  

This runs up 'lein repl :headless' and creates a new buffer inside emacs to interact with it.  

#### paredit-mode
A minor mode to handle parentheses, double quotes & brackets  
It can be toggle on/off with M-x paredit-mode  

M-(         Wrapping surrounds expression after point with parentheses  
C-RightArrow  
            Slurping - move right-parenthesis an expession right  
C-LeftArrow  
            Unslurping / Barfing - move right-parenthesis an expression left  
C-M-f       Move forward to opening parenthesis (like M-F for word)
C-M-b       Move back to closing parenthesis (like M-b for word)

### Clojure & Cider
C-x C-e     (cider-eval-last-expression) Evaluate expression before point, to the REPL  
C-u C-x C-e Print the result of the evaluation, after point  

C-c M-n     Sets the name-space as listed at the top of current file, changing the prompt in the REPL window.  

C-c C-k     Compile current i.e 'load (eval)' buffer, within the REPL session  
C-c C-l     Load (eval) file  
C-c C-d C-d Display documentation for symbol under point  
C-c C-d C-a Apropos search; find arbitrary text across function names and documentation  
M-. & M,    Navigate to source code for symbol under point and return to original buffer  

###In Cider REPL:  
C-upArrow  
C-downArrow cycle through REPL history (a problem on Mac because mapped to Mission Control)

C-enter     close dangling parentheses and evaluate expression