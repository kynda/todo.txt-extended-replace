# Extended Todo.txt-cli Replace

This adds some additional functionality to the base "replace" command for 
[TODO.TXT-Cli](https://github.com/ginatrapani/todo.txt-cli). Namely, this allows 
us to selectively replace only parts of a todo line based on flags for replacing
the project, context, message or entire line.

    replace ITEM# item
      -c replace only the context
      -p replace only the project
      -m replace only the message
      -d replace only the due date

## Example Usage

    cat ./todo.txt
    (A) test due:2017-01-01T10:00 due:2017-01-01T10:00 +project @context

    todo replace 1 -p +new-project
    cat ./todo.txt
    (A) test due:2017-01-01T10:00 +new-project @context

    todo replace 1 -c @new-context
    cat ./todo.txt
    (A) test due:2017-01-01T10:00 +new-project @new-context

    todo replace 1 -m "new message"
    cat ./todo.txt
    (A) new message due:2017-01-01T10:00 +new-project @new-context

    todo replace 1 -p +project -c @context -m test due:2017-01-01T10:00
    cat ./todo.txt
    (A) test due:2017-01-01T10:00 +project @context

    todo replace 1 -d due:2017-01-01T12:00
    cat ./todo.txt
    (A) test due:2017-01-01T12:00  +project @context

    todo replace 1 "new message +new-project @new-context"
    cat ./todo.txt
    (A) new message +new-project @new-context
