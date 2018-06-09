tty
====

`struct termios`: 包含可以检测和更改的终端设备特性 
```c
struct termios {
  tcflag_t c_iflag;             /* input flags */
  tcflag_t c_oflag;             /* output flags */
  tcflag_t c_cflag;             /* control flags */
  tcflag_t c_lflag;             /* local flags */
  cc_t     cc_cc[NCCS];         /* control characters */
};
```

[Serial Programming Guide for POSIX Operating Systems](https://www.cmrr.umn.edu/~strupp/serial.html)
[Serial Programming HOWTO](http://tldp.org/HOWTO/Serial-Programming-HOWTO/)

