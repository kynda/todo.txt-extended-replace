# Advanced Todo.txt-cli Replace

This adds some additional functionality to the base "replace" command for 
[TODO.TXT-Cli](https://github.com/ginatrapani/todo.txt-cli). Namely, this allows 
us to selectively replace only parts of a todo line based on flags for replacing
the project, context, message or entire line.

    replace ITEM# item
      -c replace only the context
      -p replace only the project
      -m replace only the message 

## Example Usage

    cat ./todo.txt
    (A) test +project @context

    todo replace -p +new-project
    cat ./todo.txt
    (A) test +new-project @context

    todo replace -c @new-context
    cat ./todo.txt
    (A) test +new-project @new-context

    todo replace -m "new message"
    cat ./todo.txt
    (A) new message +new-project @new-context

    todo replace -p +project -c @context -m test
    cat ./todo.txt
    (A) test +project @context

    todo replace "new message +new-project @new-context"
    cat ./todo.txt
    (A) new message +new-project @new-context
