
# Part 1 - Bugs

## A failure-inducing input for the buggy program:
```
@Test
public void testReverseInPlace2() {
    int[] input1 = { 4,3 };
    ArrayExamples.reverseInPlace(input1);
    assertArrayEquals(new int[]{ 3, 4 }, input1);
}
```

## An input that doesn't induce a failure
```
@Test 
public void testReverseInPlace() {
    int[] input1 = { 3 };
    ArrayExamples.reverseInPlace(input1);
    assertArrayEquals(new int[]{ 3 }, input1);
}
```

## symptom:

![plot](https://github.com/francisgan/cse15l-lab-reports/blob/main/report3/p1.png?raw=true)

## debug:
original code:
```
static void reverseInPlace(int[] arr) {
  for(int i = 0; i < arr.length; i += 1) {
    arr[i] = arr[arr.length - i - 1];
  }
}
```

new code:
```
static void reverseInPlace(int[] arr) {
  for(int i = 0; i < arr.length / 2; i++) {
    int temp = arr[i];
    arr[i] = arr[arr.length - i - 1];
    arr[arr.length - i - 1] = temp;
  }
}
```

The fix addresses the issue by using a temporary variable to hold one of the values being swapped, ensuring no data is overwritten prematurely. By iterating only up to the midpoint of the array, each pair of elements is swapped just once, correctly reversing the array without duplicating or losing any elements.




# Part 2 - Researching Commands

For this part I choose `find` command.

## Option 1: -type
This option allows us to determine the type of the files we want to search. The most Common types include f for regular files and d for directories. 

Source:https://man7.org/linux/man-pages/man1/find.1.html

### -type example 1:
```
[user@sahara ~/docsearch]$ find ./technical -type d
./technical
./technical/911report
./technical/biomed
```

### -type example 1:
```
[user@sahara ~/docsearch]$ find ./technical -type f
./technical/911report/chapter-13.4.txt
./technical/911report/chapter-2.txt
./technical/911report/chapter-11.txt
./technical/911report/chapter-13.1.txt
./technical/911report/chapter-10.txt
./technical/911report/chapter-3.txt
./technical/911report/chapter-7.txt
./technical/911report/preface.txt
...(too many results here, they are all regular files)
```

## Option 2: -name
This option allows us to search for files and directories based on their names.

Source:https://man7.org/linux/man-pages/man1/find.1.html
### -name example 1:
```
[user@sahara ~/docsearch]$ find ./technical -name "*3-15.txt"
./technical/biomed/1471-2407-3-15.txt
./technical/biomed/1471-2164-3-15.txt
./technical/biomed/1471-2091-3-15.txt
./technical/biomed/1471-2180-3-15.txt
./technical/biomed/1471-2121-3-15.txt
./technical/biomed/1471-2334-3-15.txt
```

### -name example 2:
```
[user@sahara ~/docsearch]$ find ./technical -name "pre*"
./technical/911report/preface.txt
```

## Option 3: -mtime
This option allows us to finds files and directories based on their modification time.

Source:https://man7.org/linux/man-pages/man1/find.1.html
### -mtime example 1:
```
[user@sahara ~/docsearch]$ find ./technical -mtime -1
./technical/911report/chapter-13.4.txt
./technical/911report/chapter-2.txt
./technical/911report/chapter-11.txt
./technical/911report/chapter-13.1.txt
./technical/911report/chapter-10.txt
./technical/911report/chapter-3.txt
./technical/911report/chapter-7.txt
...(all files modified in the last 1 day in ./technical)
```

### -mtime example 2:
This example find files that are not modified in the last 1 day in ./technical, there are no output since I just clone the repo to local.
```
[user@sahara ~/docsearch]$ find ./technical -mtime +1
```

## Option 4: -size
The -size option allows you to find files based on their size.

Source:https://man7.org/linux/man-pages/man1/find.1.html
### -size example 1:
This example find files larger than 150kb
```
[user@sahara ~/docsearch]$ find ./technical -size +150k
./technical/911report/chapter-13.4.txt
./technical/911report/chapter-3.txt
./technical/911report/chapter-13.5.txt
```

### -size example 2:
This example find empty files
```
[user@sahara ~/docsearch]$ find ./technical -size 0
./technical/biomed/1476-9433-1-3.txt
./technical/biomed/1476-511X-1-2.txt
./technical/biomed/1476-511X-2-3.txt
./technical/biomed/1476-0711-2-3.txt
./technical/biomed/1472-6963-3-14.txt
./technical/biomed/1477-7827-1-43.txt
./technical/biomed/1475-2883-2-11.txt
...(all emptry files)
```
