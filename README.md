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

##Javascript
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

##Javascript Testing
typical process
```
install jest: npm install --save-dev jest
add jest to test script to package.json
  'test': 'jest'
Ensure your script file ends in xxx.test.js
code test as:
  test('description', () => {expect(function.toBe(answer}
```

##NPM
Initialize project
```
npm init (add -y to use defaults)
```
Install package dependencies
```
npm install
```

##Python
Regex for all indices
```
[x.start() for x in re.finditer(r'\)', input_string)]
```

##Python Testing
Typical process
```
import unittest
Create a class that inherents unittest.TestCase
Write methods in that class that are prepended by test_, do a self.asertXXX in each def
Call unittest.main() in the main file test
```

##VSCode
Open current window in directory
```
code -r .
```
Open new window in directory
```
code .
```

#Ubuntu System Setup
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