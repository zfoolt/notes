clipboard
===========

linux
-----

1. `xclip`

```bash
sudo apt-get install xclip

echo test | xclip -selection c
# Ctrl + v == test
# maybe you can do some aliases
alias setclip="xclip -selection c"
alias getclip="xclip -selection c -o"
```
2. `xsel` 

```bash
sudo apt-get install xsel
```

Mac
---

```bash
echo "Hello World" | pbcopy
pbpaste
```

Cygwin
------

```bash
echo "foo" > /dev/clipboard
cat /dev/clipboard
```

.oh-my-zsh
-----------

Linux/Mac/Cygwin 通用

```zsh
echo "foo" | clipcopy
clippaste
```
