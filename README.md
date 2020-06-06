# Code Platoon Notes

## Git
typical process
```
git add .
git status
git commit -m ‘my solution’
git push origin master
```

create branch
```
git checkout -b “branch name”
```

list branches
```
git branch
```

checkout a branch
```
git checkout “branch name”
```

Sync local to repo
```
git pull
```

Merge branches
```
git merge “branch”
```

Reset branch back to match remote
```
git fetch origin && git reset --hard origin/<branch name> && git clean -f -d

```

## Javascript

export function
```
module.exports = xxx;
```
import function
```
let yyy = require("./xxx");
```
Sort list
```
list.sort()
```
Get unique list
```
Array.from(new Set(list))
```
Reverse string
```
str.split("").reverse().join("")
```
Convert string to int
```
parseInt(str)
```
String replace
```
str.replace(/re_pattern/g, str); (g for global replace, otherwise first instance)
```
Extract alphanumeric from string
```
string.replace(/[^a-z0-9]/g, '')
```
Compare two arrays
```
npm install shallow-equal --save
Let shallowEqualArrays = require('shallow-equal/arrays');
shallowEqualArrays(array1, array2)
```
Iterate through object keys
```
for (let key in exampleObj) {}
```
slice array
```
array.slice(start, end); (end not included)
```
convert float to integer
```
Math.floor(x)
```
get list of object keys
```
Object.keys(object)
```
check if key exists in object
```
object.hasOwnProperty(key)
```
max of list
```
Math.max(...list); (this is almost like list comprehension)
```

## Javascript Testing

typical process
```
install jest: npm install --save-dev jest
add jest to test script to package.json
  'test': 'jest'
Ensure your script file ends in xxx.test.js
code test as:
  test('description', () => {expect(function.toBe(answer}
```

## NPM

Initialize project
```
npm init (add -y to use defaults)
```
Install package dependencies
```
npm install
```

## Python

Regex for all indices
```
[x.start() for x in re.finditer(r'\)', input_string)]
```
setting up a virtual envirnment
```
python -m venv <venv name>
```
## Python Testing

Typical process
```
import unittest
Create a class that inherents unittest.TestCase
Write methods in that class that are prepended by test_, do a self.asertXXX in each def
Call unittest.main() in the main file test
```

## VSCode

Open current window in directory
```
code -r .
```
Open new window in directory
```
code .
```

## PostgreSQL
### Basic Terminal Commands
| command | description 
| ------ |  ---------- 
| psql | enter psotgresql CLI
command | description 
------ |  ---------- 
psql | enter psotgresql CLI
psql \<db name\> | enter psotgresql CLI within \<db name\> database 
createdb \<name\>  | create database 
dropdb \<name\>  | delete database 
pg_dump \<name\>  | extract db into file 

### Basic PostgreSQL CLI Commands
command | description 
------ |  ---------- 
\l | list all db 
\du | list all users 
\q | quit CLI 
\d \<table\> | list table 
\i \<filename\> | execute CLI commands from file 

### Table Filtering
```
SELECT * FROM table_name WHERE [column] [operator] [value];
```
operator | description | example |
------ |  ---------- | --- |
=  | equals | `SELECT * FROM students WHERE first_name = 'Andre';` |
<> | not equals | `SELECT * FROM enrollments WHERE grade <> 'A';` |
\>  | greater than | `SELECT * FROM classes WHERE credits > 2;` |
<  | less than | `SELECT * FROM enrollments WHERE grade < 'B';` |
\>= | greater than or equal to | `SELECT * FROM enrollments WHERE grade >= 'B';` |
<= | less than or equal to | `SELECT * FROM enrollments WHERE grade <= 'C';` |
BETWEEN | between values | `SELECT * FROM classes WHERE credits BETWEEN 3 AND 4;` |
LIKE | pattern match, `%` represents wildcard | `SELECT * FROM classes WHERE name like 'SPAN%';` |
IN | match against a list of values | `SELECT * FROM enrollments WHERE grade IN ('A','B');` |


# Ubuntu System Setup
install nvm using [link](https://www.liquidweb.com/kb/how-to-install-node-version-manager-on-ubuntu/)
Install npm
```
nvm install 12
```
Set git username
```
git config --global user.name "jasonpul"
```
Set git email
```
git config --global user.email "jason.pul.ca@gmail.com"
```
Set git to password cache
```
git config --global credential.helper cache
```
Set git global ignore
```
touch  ~/.gitignore_global
git config --global core.excludesfile '~/.gitignore_global'
```
Set VSCode as your git editor
```
git config --global core.editor "code -n -w"
```
add the following to a .bash_profile
```
alias lsl='ls -al'
alias python='python3.7'
alias pip='pip3'

parse_git_branch() {
  git branch 2> /dev/null | sed -e '/^[^*]/d' -e 's/* \(.*\)/(\1)/'
}

if [ -f ~/.git-completion.bash ]; then
  . ~/.git-completion.bash
fi

export PS1="\[\033[36m\]\u\[\033[m\]@\[\033[32m\]\h:\[\033[33;1m\]\w\[\033[m\]\$(parse_git_branch) \[\033[00m\]$\[\033[00m\] "
export PROMPT_COMMAND='echo -ne "\033]0;${PWD##*/}\007"'
export CLICOLOR=1
export LSCOLORS=ExFxBxDxCxegedabagacad
```
source the bash_profile from bashrc
```
source ~/.bash_profile
```
Set node runtime for VSCode debugging [link](https://askubuntu.com/questions/1065276/cannot-find-runtime-node-on-path-in-visual-studio-code-running-installed-on-u)
```
"runtimeExecutable": nodepath
```
install sqlite3
```
sudo apt  install sqlite3 libsqlite3-dev
```
install python3.7
```
XXXXXXXXXXXXXXXXXXXXXXXXXXXXX
sudo apt-get install -y python3.7
sudo apt-get install -y python3.7-dev
sudo apt-get install -y python3.7-venv
pip install psycopg2
```
# Ubuntu PostgreSQL Setup
Install PostgreSQL
```
sudo apt-get install -y postgresql libpq-dev
```
## Adding a PostgreSQL role that Matches your Linux Username
steps take from [link](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-postgresql-on-ubuntu-18-04)
If you don't add a role that matches your linux username, you must execute all psql commands under the postgres user using
```
sudo -u postgres <command>
```
For example
```
sudo -u postgres psql
```
After adding your linux username as a psql role, you previous command can be executed under your current account
```
psql
```
## Role Creation Steps
Create a PostgreSQL role (user) that matches your linux username
```
sudo -u postgres createuser --interactive
```
Enter your linux username and password. The interactive output should look like this:
```
Enter name of role to add: <linux-username>
Shall the new role be a superuser? (y/n) y
```
Create a default database for your new postgres roll
```
sudo -u postgres createdb <linux-username>
```