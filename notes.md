# Emacs Lisp Notes

Semi-colons start commets

  ;; This is a comment

nil and '() mean the same thing

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


For More information:

C-h v a-variable RET
C-h f a-function RET
C-h i m elisp RET
















