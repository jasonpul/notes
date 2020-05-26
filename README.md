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
Set node runtime for VSCode debugging [link](https://askubuntu.com/questions/1065276/cannot-find-runtime-node-on-path-in-visual-studio-code-running-installed-on-u)
```
"runtimeExecutable": nodepath
```

# Ubuntu PostgreSQL Setup
Install PostgreSQL
```
sudo apt-get install -y postgresql libpq-dev
```
## Adding a PostgreSQL role that Matches your Linux Username
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