core dump file analysis
=======================


1 how to use gdb to analyze core dump file
------------------------------------------

You just need a binary (with debugging symbols included) that is
identical to the one that generated the core.

First set and verified the `ulimit`

```sh
ulimit -c unlimited
```
Then you can run
```sh
gdb path/to/the/binary path/to/the/core
```
to debug it.

When it starts up, you can use

```sh
bt # (for backtrace)
# For detailed backtrace use bt full
```
to get a stack trace from the time of the crash.

In the backtrace, each function invocation is given a number. You can
use
```sh
# (replacing number with the corresponding number in the stack trace)
frame number
```
to select a particular stack frame.

You can then use
```sh
list
```
to see code around that function, and
```sh
info locals
```
to see the local variables.

You can also use
```
# (replacing "name_of_variable" with a variable name)
print name_of_variable
```
to see its value.

Typing
```sh
help
```
within GDB will give you a prompt that will let you see additional commands.

2 setting the core dump name schema
-----------------------------------

The pattern can be read/set via /proc/sys/kernel/core_pattern.

```sh
echo "newpattern" > /proc/sys/kernel/core_pattern
```

you can have variables to make the file named different per
executable, pid a.s.o..

max length 64 characters; default value is "core"

Here is a small list of possible variables

```sh
%p:       pid
%<NUL>:   '%' is dropped
%%:       output one '%'
%u:       uid
%g:       gid
%s:       signal number
%t:       UNIX time of dump
%h:       hostname
%e:       executable filename
%<OTHER>: both are dropped
```

If `core_pattern` does not include "%p" (default does not) and
`core_uses_pid` is set, then .PID will be appended to the filename.

example:

```sh
echo "core.%e.%p" > /proc/sys/kernel/core_pattern
# or use
sysctl -w kernel.core_pattern=core.%e.%p
```

produces files names

```sh
core.<executable>.<pid>
```

to make the changes permanent, add the following line to /etc/sysctl.conf:

```
kernel.core_pattern = core.%e.%p
```
