
# CSE15L Lab Report 4

### Step 4

#### Explaination: ssh tp remote ieng6  server. In this step, I didn't need to input password, because I have key authorization.
```
ssh lgan@ieng6.ucsd.edu
```
![plot](https://github.com/francisgan/cse15l-lab-reports/blob/main/report4/image6.png?raw=true)
### Step 5

#### Explaination: Clone git repo to ieng6 server.
```
git clone git@github.com:francisgan/cse15_lab7.git
```
![plot](https://github.com/francisgan/cse15l-lab-reports/blob/main/report4/image4.png?raw=true)
### Step 6
#### Explaination: Compile java files and run tester using bash file.
```
bash test.sh
```
![plot](https://github.com/francisgan/cse15l-lab-reports/blob/main/report4/image1.png?raw=true)
### Step 7
#### Explaination: Open java file in terminal by using vim.
Open java file with vim:
```
vim ListExamples.java
```

In vim:
```
/ i n d e x <space> + = <space>1 <enter> n n L L L L L x i 2 <esc> : w q <enter>
```
Press `/` start query

Press `i n d e x <space> + = <space>` to tell vim what information I want to query. 

Press `<enter>` to search for the query.

Press `n`, search the next matched information.

Press `L` move the cursor to right by one position

Press `x` to delete one.

Press `i` to start insertion mode. Press `2` to insert 2.

Press `<esc>` back to normal mode.

Press `: w q <enter>` to save file and quit vim.


![plot](https://github.com/francisgan/cse15l-lab-reports/blob/main/report4/image5.png?raw=true)
### Step 8
#### Explaination: Compile java files and run tester using bash file again.
```
bash test.sh
```
![plot](https://github.com/francisgan/cse15l-lab-reports/blob/main/report4/image3.png?raw=true)
### Step 9
#### Add changed file and make a commit, then push to git repo.
```
git add .
git commit -m “fix bug”
git push
```
![plot](https://github.com/francisgan/cse15l-lab-reports/blob/main/report4/image2.png?raw=true)
