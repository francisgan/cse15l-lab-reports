## Part 2

The absolute path to the private key for your SSH key for logging into ieng6 (on your computer, an EdStem workspace, or on the home directory of the lab computer):
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
