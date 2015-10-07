# create a repository on github.com

## create a new repository on the command line
```sh
echo "# notes" >> README.md
git init
git add README.md
git commit -m "init notes"
git remote add origin https://github.com/zfoolt/notes.git
git push -u origin master
```

## push an existing repository from the command line
```sh
git remote add origin https://github.com/zfoolt/notes.git
git push -u origin master
```
