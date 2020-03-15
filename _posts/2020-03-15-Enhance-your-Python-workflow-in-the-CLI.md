---
layout: post
title: "Enhance your Python workflow in the CLI"
categories: [Python, CLI]
tags: [beginners]
---

### Improve you CLI workflow with Python

Maybe you remember some comands from documentations like:

```bash
brew upgrade && brew update
```

Yea, you see right. This command will execute `brew upgrade` and `brew update`
one after another. But did you know you can do somthing similar to get the same result?

```bash
brew upgrade; brew update
```

The difference between them is simple and has to do with status codes.

## What are Statuscodes and how can I use them?

Here is a example:

```python
# script.py
import sys
import time

def doSomething():
    for i in range(5):
        time.sleep(1)
        print("done")
    sys.exit(0)

if __name__ == "__main__":
    doSomething()
```

"ok ok... I get it... but wait!" Exactly. `sys.exit(0)` is used to exit a program and returns a status code of 0.

Try to run this command in you comand line:

```bash
python script.py && echo "finish"
```

Nothing happend...right?

Now change `sys.exit(0)` with `sys.exit(1)` and rerun it.

This is the point where you will expect to see "finish" after the "4" but `&&` is preventing the execution because of the status code of 1.

You see... status codes can help controling your workflow in the CLI.

Maybe you don`t care how your program is ending, so try this instead:

```bash
python script.py; echo "finish"
```

The semelicon is also used to execute one command after another, but our semelicon don`t care about the status of the last executed program.

## Conclusion

I think at this point the difference should be clear...

Both operators can help you preventing the executions of commands if something went wrong in your execution. Sometimes you need to know how your program has exit and sometimes you wish code get executed anyway... you decide!

_If it was usefull for you please share it with a friend and leave a comment! Thanks!_
