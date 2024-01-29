## Part 1

Here is my code in `ChatServer.java`:
```
import java.io.IOException;
import java.net.URI;
class ChatHandler implements URLHandler {
    // The state of the server: a StringBuilder to accumulate chat messages
    StringBuilder chatHistory = new StringBuilder();

    public String handleRequest(URI url) {
        if (url.getPath().equals("/")) {
            return chatHistory.length() == 0 ? "No messages yet." : chatHistory.toString();
        } else if (url.getPath().contains("/add-message")) {
            String[] parameters = url.getQuery().split("&");
            String user = null;
            String message = null;
            for (String param : parameters) {
                String[] keyValue = param.split("=");
                if (keyValue[0].equals("user")) {
                    user = keyValue[1];
                } else if (keyValue[0].equals("s")) {
                    message = keyValue[1];
                }
            }

            if (user != null && message != null) {
                chatHistory.append(user).append(": ").append(message).append("\n");
                return chatHistory.toString(); // Return the updated chat history
            } else {
                return "Invalid request. User and message parameters are required.";
            }
        } else {
            return "404 Not Found!";
        }
    }
}
class ChatServer {
    public static void main(String[] args) throws IOException {
        if (args.length == 0) {
            System.out.println("Missing port number! Try any number between 1024 to 49151");
            return;
        }

        int port = Integer.parseInt(args[0]);

        Server.start(port, new ChatHandler());
    }
}
```
I'm also using `Server.java`, which is provided in previous labs. After I run following code in EdStem command
```
[user@sahara ~/wavelet]$ javac Server.java ChatServer.java
[user@sahara ~/wavelet]$ java ChatServer 4000
Server Started!
```
I can use `https://0-0-0-0-4000-jc15uvgnbrni1q1acg5qnmo3o0.us.edusercontent.com/` to access my ChatServer

Screenshot one:

![plot](https://github.com/francisgan/cse15l-lab-reports/blob/main/report2/p1.png?raw=true)

Here I used `https://0-0-0-0-4000-jc15uvgnbrni1q1acg5qnmo3o0.us.edusercontent.com/add-message?s=Hello&user=jpolitz`. And then `handleRequest` is being called. The argument is an URI. After parse the URI, there are two parameters user and message. Before the parameter `chatHistory` was empty, now `user` and `message` are stored in `chatHistory`. The Server then returns everything in `chatHistory`.

Screenshot Two:

![plot](https://github.com/francisgan/cse15l-lab-reports/blob/main/report2/p2.png?raw=true))

Here I used `https://0-0-0-0-4000-jc15uvgnbrni1q1acg5qnmo3o0.us.edusercontent.com//add-message?s=How are you&user=yash`. And then `handleRequest` is being called. The argument is an URI. After parse the URI, there are two parameters user and message. Before the parameter `chatHistory` stores on meessage with user, now a new `user` and `message` pair has been stored in `chatHistory`. The Server then returns everything in `chatHistory`, which are two messages from two users.

## Part 2

The absolute path to the private key for your SSH key for logging into `ieng6`:
```
C:\Users\gl121>dir C:\Users\gl121\.ssh\id_rsa
 Volume in drive C has no label.
 Volume Serial Number is DE12-282B

 Directory of C:\Users\gl121\.ssh

2024/01/29  01:57             2,602 id_rsa
               1 File(s)          2,602 bytes
               0 Dir(s)  464,292,978,688 bytes free

C:\Users\gl121>dir C:\Users\gl121\.ssh
 Volume in drive C has no label.
 Volume Serial Number is DE12-282B

 Directory of C:\Users\gl121\.ssh

2024/01/29  01:57    <DIR>          .
2024/01/28  20:26    <DIR>          ..
2024/01/29  01:57             2,602 id_rsa
2024/01/29  01:57               573 id_rsa.pub
2024/01/29  01:57               723 known_hosts
               3 File(s)          3,898 bytes
               2 Dir(s)  464,292,954,112 bytes free
               
```
Since I'm using a windows pc, I use `dir` here. In `C:\Users\gl121\.ssh`, we can see a file called `id_rsa`, which is the private ket. Thus the absolute path of private ket is `C:\Users\gl121\.ssh\id_rsa`.


The absolute path to the public key for your SSH key for logging into `ieng6`:
```
[lgan@ieng6-201]:~:53$ ls ~/.ssh/authorized_keys
/home/linux/ieng6/oce/9d/lgan/.ssh/authorized_keys
[lgan@ieng6-201]:~:54$
```


A terminal interaction where you log into your ieng6 account without being asked for a password:
```
C:\Users\gl121>ssh lgan@ieng6.ucsd.edu
Last login: Mon Jan 29 02:01:02 2024 from 99-76-228-160.lightspeed.sndgca.sbcglobal.net
quota: Cannot resolve mountpoint path /home/linux/dsmlp/.snapshot/daily.2024-01-12_0010: Stale file handle
Hello lgan, you are currently logged into ieng6-201.ucsd.edu

You are using 0% CPU on this system

Cluster Status
Hostname     Time    #Users  Load  Averages
ieng6-201   02:10:01   1  1.89,  1.51,  1.47
ieng6-202   02:10:01   3  0.73,  0.90,  0.73
ieng6-203   02:10:01   1  2.03,  2.26,  2.28



To begin work for one of your courses [ cs15lwi24 ], type its name
at the command prompt.  (For example, "cs15lwi24", without the quotes).

To see all available software packages, type "prep -l" at the command prompt,
or "prep -h" for more options.
[lgan@ieng6-201]:~:50$
```

## Part 3

I learn how to connect remote server and run java code on it. I observer how multiple people access to the same remote server and how java code deal with it. I also learn how to use keys to access remote server faster.
