# Part 1 - Debugging Scenario

## file & directory structure:

![plot](https://github.com/francisgan/cse15l-lab-reports/blob/main/report5.png?raw=true)

`GreetNames.java` Content:
```
public class GreetNames {
    public static void main(String[] args) throws Exception {
        
        for (int i=0;i<3;i++) {
            File file = new File(args[0]);
            Scanner scanner = new Scanner(file);
            String name = scanner.nextLine();
            System.out.println("Hello, " + name + "!");
            scanner.close();
        }
    }
}
```

`names.txt` content:
```
A
B
C
```

`run.sh` content:
```
javac GreetNames.java
java GreetNames names.txt 
```

## Debugging Senario:

Student: Hi everyone,

I'm working on a Java program that's supposed to read a list of names from a text file and print each name with a greeting. I wrote a bash script to compile and run the Java program, but I'm getting unexpected output. Instead of greeting each name, it's just printing the first name over and over again. I thought maybe the bug was with how I'm reading the file in Java, but now I'm not so sure. Here's a screenshot of the output I'm getting:
```
Hello, A!
Hello, A!
Hello, A!
```
Expected output should be:
```
Hello, A!
Hello, B!
Hello, C!
```

TA: Could you take a screen shot of your java code and use `cat` command to print content in txt file?

Student:
Here is my java code:
```
public class GreetNames {
    public static void main(String[] args) throws Exception {
        
        for (int i=0;i<3;i++) {
            File file = new File(args[0]);
            Scanner scanner = new Scanner(file);
            String name = scanner.nextLine();
            System.out.println("Hello, " + name + "!");
            scanner.close();
        }
    }
}
```
Here is output in terminal:
```
[user@sahara ~]$ cat names.txt
A
B
C
```

TA: The bug is that you create a new scanner in every loop. You should create scanner only once before the for loop.

#### The full command line (or lines) you ran to trigger the bug:

`bash run.sh`

#### A description of what to edit to fix the bug: Move `Scanner scanner = new Scanner(file);` before the for loop.


# Part 2 - Reflection

I learned vim in second half of quarter. Learning vim is very important to me. Before when I do a git commit, I don't know what to do in vim and how to quit. Now I can do it easily. Furthermore, when I ssh a remote AWS server, I can modify argument with vim in terminal really quick. I don't need to create a jupyternote book GUI anymore, which saves a lot of time for me.
