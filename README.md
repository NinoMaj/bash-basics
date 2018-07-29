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

## mkdir
Make new directory

```
mkdir my_folder
```

To create folder and new folder in it, add -p flag
```
mkdir -p outter_dir/inner_dir
```

## rm
Remove folder or file
```
rm file.txt
```
To delete folder and its content add recursive flag
```
rm -r folder/
```
If you don't want conformation message and error warning if file doesn't exist add -f flag
```
rm -rf folder/
```

## mv
Move files and folders, but it also can be used for renames
```
mv target.txt desination_folder/target.txt
```
Rename while moving
```
mv target.txt desination_folder/renamed_target.txt
```
Just rename
```
mv file.txt renamed_file.txt
```

## cp
Copy, as with move we could also rename while copying
```
cp file.txt folder/file.txt
```
To copy whole folder
```
cp -R src/* dest/
```

## find
To find files and folders
a) To find all txt files in my_folder, we would write
```
find my_folder/ -name "*.txt" # btw, this is not regex
```

b) For case insensitive search use -iname flag
```
find my_folder/ -iname "*.txt"
```

c) To find all folders in current directory
```
find . -type d
```

d) We can combine b) and c) to find all folder named text
```
find . type d -iname "text"
```

d) We could combine it with delete flag to delete what we found
```
find . type d -iname "text" -delete
```

e) To run some operation on found files, like run imaginary encrypt on each txt file in my_important_folder
```
find my_important_folder/ -iname "*.txt" -exec encrypt
```

## grep
Find search term in files, every outputed line will be one search match
a) Find version in lodash package
```
grep "version" node_modules/lodash/package.json
```

b) We can search multiple files
```
grep "version" node_modules/**/*.json
```

c) To colorize match, --color flag
```
grep --color "version" node_modules/**/*.json
```

d) To output two lines before and after found search term, we have context flag -C
```
grep -C 2 "term" file.txt
```

e) Use regex with -e
```
grep -e "[0-9]" file.tx
```

## curl
Output http response
```
curl www.google.com
```

a) To include headers use -i flag
```
curl -i www.google.com
```

b) By default curl won't follow redirect, if we want that we use L flag
```
curl -L www.google.com
```

c) To include headers -H flag
```
curl -H "Authorization: Bearer 34151534" localhost:8000/api/auth
```

d) To change http verb -X flag
```
curl -X POST -H "Content-Type: application/json" -d '{"name": "John"}' http://example.com/api/user
# d is for body
```

e) To output to a file -o flag
```
curl -il www.example.com/ -o file.txt
```

f) To parse json output we could pipe it to some program, like globally installed node package jsome
```
curl www.site.com | jsome
```

## Scripting
a) To init JS project
```
touch init-js.sh
echo "Initializing JS project at $(pwd)" # pwd - is current working directory
git init
npm init -y # create package.json with all defaults
mkdir src
touch src/index.js
code . # to open in VS Code
```
Save file and then run with ```.init-js.sh```
If you get persmission denied, with ```ls -l``` check first four flags ```-rw-``` 1. flag is file or director, then user permission, 2. read, 3. write and 4. execute. if 4th flag is ```-``` you don't have execute permission. This are default permissions settings.
To change that write ```chmod u+x script.sh``` to add to the user execute permission. Now flags should be ```-rwx```

If we want to execute this script from anywhere we must use ```$PATH``` variable.
Type ```echo $PATH``` to see all folders where shell is looking for executables.
To see from where node executable is rantype ```which node```
To put our file in PATH ```cp init-js.sh /use/local/bin/init-js```
Test it with ```which init-js```

## Variables
```
my_var=12345 # Don't use spaces
echo $my_var
```
Variables are scoped per script.

To export my_var to be accessible outside of script
```
export my_var
```

To unset variable
```
unset my_var
```

To see all bash global variables
```
env
```
Common global var is USER, to reference it ```echo $USER```

Script to clone a local branch from to temp folder
```
touch clone-to-temp.sh

temp=$(mktemp -d)
git clone --branch $1 $PWD $temp
echo "branch $1 was cloned to $temp folder"
# we can now run some test or task here...

chmod u+x clone-to-temp.sh

#test it with .clone-to-temp.sh new-temp-branch
```




