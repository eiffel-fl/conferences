Debugging concurrent program in golang
======================================

It is really hard to debug concurrent programs.
To debug sequential program, you use breakpoints and go steps by steps.
Sadly concurrent programs do not have forcefully the same behavior while giving the same output a given set of inputs.
Particularly with golang, as you have the userspace thread known as ``goroutine``.

It can be useful to print how golang schedules th thread with ``DEBUG=schedtrace=5000`` environment variable.
You can print ``channels`` current state and also set breakpoints in ``goroutine``.
Sadly, you cannot send value to channel from ``delve``.
``delve`` has the ``goroutine`` keyword which will print in which ``goroutine`` you are right now.

You can also use ``pprof`` labels to help you in this task.
``pprof`` is a golang package normally used to profile source code.
Then, in ``delve`` you can filter ``goroutines`` based on these labels.

To use ``gdb`` you need to use the ``nocompressdwarf`` ``ldflags``.

There is deadlock detection in ``golang`` is for example all ``goroutines`` are sleeping on a lock.
You can also use ``-race`` golang building flag to use the ``golang`` data race detector.
