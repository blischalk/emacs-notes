# Emacs Lisp Notes

Press q to quit out of the debugger

## Helpful Emacs lisp stuff

	http://www.emacswiki.org/emacs/EmacsLispIntro
  
  

## Emacs Lisp Intro
	C-h i
 
 	Then Click on:
 
 	Emacs Lisp Intro: (eintr).
 
 	Or eval:
 
 	(info "(eintr) Top")
 
 

## Comments

Semi-colons start commets

;; This is a comment


Commenting out a whole sexp:

C+M+Space to select expression and then M+;

## Truth

nil and '() mean the same thing

false == nil or '()
true = t

Store a Variable:

	(setq my-variable "A String")

Insert a value into the buffer where the cursor is:

	(insert "This is inserted")

Define a function:

	(defun my-function (my-arg) (insert "some text " my-arg))

Switch to a new buffer in another window:

	(switch-to-buffer-other-window "*test*")

Combine multiple sexps together:

	(progn
		(switch-to-buffer-other-window "*test*")
		(hello "you"))

Erase a buffer with:

	(erase-buffer)

Go back to other window:

	(other-window 1)

## Let

variables are bound to nil if they are not initialized.

	(let ((birch 3)
		   pine
	       fir))

pine and fir are bound to nil

Bind a local variable:

	(let ((local-name "you"))
		(insert local-name))

Format a string:

	(format "Hello %s\n" "you")

Read from the mini buffer:

	(read-from-minibuffer "Enter your name: ")

Create a list:

	(setq my-list '("first" "second" "third"))

Get the head of a list:

	(car my-list)

Get the tail of a list:

	(cdr my-list)

Add to the front of a list (destructive):

	(push "new value" my-list)

Map a function over a list:

	(mapcar 'some-funk my-list)

Goto the beginning of a buffer:

	(goto-char (point-min))

While loop:

	(while (something-is-true)
		(do-something))

Search for a string:

	(search-forward "The String" nil t)

- use nil to saythe search is not bound to a position.
- use t to say silently fail when nothing is found

Search using a regular expression:

	(re-search-forward "Bonjour \\(.+\\)!" nil t)

Add some properties to text:

	(add-text-properties (match-beginning 1)
	(match-end 1)
	(list 'face 'bold))


To concat strings:

	(concat "abc" "def")

To find a substring:

	(substring "The quick brown fox jumped." 16 19)

To turn a number into a string:

	(number-to-string 10)

To use multiple arguments in a function:

   ?????

Send a message to the user in the echo area:

	(message "This message appears in the echo area!")

The message can be formatted

	(message "The name of this buffer is: %s." (buffer-name))


	(message "There are %d %s in the office!"
		(- fill-column 14) "pink elephants")


	(message "He saw %d %s"
              (- fill-column 32)
              (concat "red "
                      (substring
                       "The quick brown foxes jumped." 16 21)
                      " leaping."))


`buffer-name` is a variable set to the current buffers name.


## Setting variables with set and setq

With set you must quote both arguments unless you want them evaluated.

	(set 'flowers '(rose violet daisy buttercup))


setq makes it so you don't have to quote

	(setq carnivores '(lion tiger leopard))

	(setq trees '(pine fir oak maple)
		  herbivores '(gazelle antelope zebra))))

## Printing in the scratch instead of the echo area

	C-u C-x C-e instead of the echo area

## Get the current buffer

	(current-buffer)

## Most recently selected buffer

	(other-buffer)

## switch-to-buffer

  To switch to another buffer

## Different keystrokes cause the lisp interpreter to run different functions

	C-x b t

Tells emacs to run the function switch-to-buffer

## Current buffer name

	(buffer-name)

## Current buffer file name

	(buffer-file-name)

## Get the size of the current buffer

	(buffer-size)

## Current position of the cursor is called the point

	(point)

## point-min and point-max

Minimum and maximum permissible value of point in the current buffer.  point-min is generally 1 unless "narrowing" is in effect.


## A special form doesn't evaluate its arguments in the usual manor

## To learn about a function use:

	C-h f
	(describe-function)


## To make a function interactive

Placing a list that begins with the special form `intractive` immediately after the documentation

	(defun my-funk
	  (number)
	  "This is my documentation"
	  (interactive "p")
	  (message "The result is %d" (* 7 number)))

Use C-u and then a value to pass that as an argument to the function.

The "p" tells emacs to use the C-u supplied argument as the functions argument.

use M-x function-name to test a function

There are more than 20 chars that can be supplied to interactive.

Each letter should be separated by a \n character


## To keep code around, put it in your .emacs / init.el file or in separate files and load them

## Loading Files

(load "~/emacs/slowsplit")

Loads the slowsplit.el file or byte compiled slowsplit.elc

Instead of loading a single file, you can add a directory to the loadpath:

(setq load-path (cons "~/emacs" load-path))

(load-library) is an interactive version of load.


## To replace a key binding

You must unset the previous key binding and reset

     (global-unset-key "\C-x2")
     (global-set-key "\C-x2" 'split-window-quietly)

## Eval a current buffer

M eval-buffer


## if then else

	(if (some-test)
		(do-this)
		(otherwise-this))

## save-excursion

Saves the location of point and mark, executes the body of the
function and then restores point and mark

- Point is immediately before the character that the cursor is on top of.
- The "mark" is a position which is set by C-<SPC>.  You can use C-x C-x (exchange-point-and-mark)
to move the cursor to the mark.  You can set multiple marks.

## `(push-mark)` / `(push-mark (point))`

Set a mark at the current position of the cursor.


## `(goto-char (point-min))`

Move cursor to the minimum point in the buffer (the beginning of the
buffer or the beginning of the accessible portion of the buffer if it
is narrowed.


## let*

Is used when variables later in the var list use variables earlier in the variable list.










For More information:

Read the tutorial in Emacs (Not the reference docs).

C-h v a-variable RET
C-h f a-function RET
C-h i m elisp RET
















