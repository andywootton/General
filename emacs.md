# emacs

### Keys
C- maps to Ctrl on a Windows keyboard  
M- maps to Alt on a Windows keyboard & Option on Mac  

'The region' is the area between 'the mark' & 'the point'  
'The mark'...  
'The point' is the current cursor position.  
## emacs line editing, including bash 
###Navigation keys
[ Think of the following 3 lines as a diagram ]

C-p (Previous)  
C-a (stArt of line) M-b (word Back) C-b (Char Back) C-f (Char Forward) M-f (word Forward) C-e (End of line)  
C-n (Next)  

C-s         (Search)  
C-r         (Reverse search)  
Tab         Indent line
C-j         New line and indent

M-w         copy region (kill-ring-save)

### Destructive editing keys
M-%         (search / replace)  
M-backspace delete word behind  
backspace   delete character behind  
C-d         Delete character ahead  
M-d         Delete word ahead (kill-word)  
C-k         Kill to end of line (kill-line)

## Other C-

C-g or C-G  Quit current command  
C-h         Help, ? for more options  
C-o         Insert newline after cursor  
C-t         Swap the 2 characters at the cursor  
C-u n char  Insert n copies of char  
C-/         Undo last command  

C-space     Set the 'mark'. Later, everything between this & 'point' is the 'region'  
C-w         Kill region  
C-y         Yank text from kill-ring

## C-x char
###windows
C-x u       Undo last command  
C-x o       switch to Other pane in split window  
C-x 0       delete current window  
C-x 1       unsplit window  
C-x 2       split window horizontally  
C-x 3       split window vertically  

###buffers

C-x b       create new Buffer (switch-to-buffer)  
C-x k enter Kill the buffer

## C-x C-
C-x C-f     open File  
C-x C-s     Save (save-file)  
C-x C-w     Write(save) to a new filename  
C-x C-c     quit emacs

C-x C-e     default - Evaluate eLisp

## Other M- {: style="page-break-before: always" }
M-y         Replace last yanked text with next item on kill ring
M-u         Uppercase word at cursor  
M-l         Lowercase word at cursor  
M-m         Move to first non-whitespace character on the line  
M-<         Move to start of buffer  
M->         Move to end of buffer  
M-/         Hippie expand; cycle through possible expansions of text before point  
M-\         Delete spaces and tabs around point  
M-g g       Go to line

##Help
C-h k key   Describe function bound to key  
C-h f       Describe function  
C-x o q     Close help windows

## Power tools

M-x         run the smex command, which prompts for a command to be run  
M-x function_name  
M-x replace-regexp

### Rectangles

C-x r ...   emacs has a set of tools to edit rectangles of text

# Packages
“Beginner’s Guide to Emacs”  
http://www.masteringemacs.org/articles/2010/10/04/beginners-guide-to-emacs/

M-x package-refresh-contents
M-x package-list-packages
M-x package-install

# Clojure
## Customisations
Modifications suggested in 'Clojure for the Brave and True'

Edit ~/.emacs.d/customizations/ui.el  
e.g. line 37 defines window size

## The REPL
### In a terminal
lein repl
### Cider
The emacs Cider package https://github.com/clojure-emacs/cider/  
Can be installed manually by emacs 'M-x package-install' then entering 'cider'.  
Open a file containing Clojure code then  
M-x cider-jack-in   
or  
C-c M-j  

This runs up 'lein repl headless' and creates a new buffer to interact with it.  

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
C-x C-e     Evaluate expression before point, to the REPL (cider-eval-last-expression)  
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