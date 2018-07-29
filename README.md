# bash-basics
Crash course on bash

## man
Manual for any command
```
man find
```

## cd
Change directory
```
cd folder/
```

## ls
List of available folders and files
```
ls
```

#### flags
- -l
More detailed list
```
ls -l
# -rw-r--r-- 1 nino8 197609     0 Jul 29 11:52 file.txt
```
First character is shows us if it is directory (d) or file (-), other flags are permissions. Then we see user, group and created or modified date.

- -a
To see hidden files and folder
```
ls -a
# . .. Some_folder file.txt
```
. and .. are special folder, they mean current directory and parent directory. So to go up one level you can write ```cd ..```

## cat
For checking file content
```
cat file.txt
# Hello world
```

## cat
For checking file content
```
cat file.txt
# Hello world
```

## less
Similar like cat, but better tool for file checking. First you only see file content and not previous command, secondly you can navigate more easily (g - beginning of file, shift g - end of file), you can search text with /search_term. Btw, q is for quitting less program.
```
less file.txt
```

## .
Open current directory.
It can be useful for hidden files like .git ```. .git```

```. somefile.js``` - will open with default program for that extension. We can select program to open it with ```. somefile.js TextEdit```. Can be useful for files without ext or without default one.

## touch
To create a file
```
touche file.txt
```

## echo
Something like print or console.log for bash
```
echo "Hello world"
```

We could use it to put text in a file ```echo 'Some sentence I want to save' > file.txt```. If we do it multiple times, it will override previous text, so to append we use >> ```echo 'New sentence' >> file.txt``


