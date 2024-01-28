# Share an example of using the command with no arguments.
```
[user@sahara ~]$ pwd
/home
[user@sahara ~]$ cd
[user@sahara ~]$ ls
lecture1
[user@sahara ~]$ cat




^C
```
1. ```cd```: The working directory is home when it is run. cd is intended to change directories, since we did not specify which directory, it will go to (or stay as) default home directory. This is not an error.
2. ls: the working directory is home when it is run. ls prints the files and folders of the working directory so therefore it only prints lecture1. The directories and files under lecture1 are not printed because they are not under the home directory. This is not an error.
3. cat: The working directory is home when it is run. cat is meant to print the contents of a file but with no arguments, there is nothing to print. This results in an error because this common requires a specified file. 


# Share an example of using the command with a path to a directory as an argument.
```
[user@sahara ~]$ cd lecture1
[user@sahara ~/lecture1]$ pwd
/home/lecture1
```
```
[user@sahara ~]$ cd messages
bash: cd: messages: No such file or directory
[user@sahara ~]$ pwd
/home
```
```
[user@sahara ~]$ cd lecture1
[user@sahara ~/lecture1]$ cd messages
[user@sahara ~/lecture1/messages]$ 
```
1. cd <directory>: the working directory was lecture1 after cd lecture1 was run as shown by the pwd. This is not an error. When cd messages was run, however, the working directory was still home by default and this produced an error message because in the home directory, cd cannot see files and directories under a different directory. This problem can be solved by changing the working directory to lecture1 first and then changing it to messages. cd can now access lecture1 directory first and therefore can access the messages directory within lecture1. This is not an error. 
```
[user@sahara ~]$ ls lecture1
Hello.class  Hello.java  messages  README
[user@sahara ~]$ ls messages
ls: cannot access 'messages': No such file or directory
[user@sahara ~]$ cd lecture1
[user@sahara ~/lecture1]$ ls messages
ar-jo.txt  en-us.txt  es-mx.txt  zh-cn.txt
```
2. ls <directory>: the working directory is home. The given path is lecture1 so ls displays all the files and folders of lecture1. This is not an error. ls messages gives the same error as cd <messages> for the same reasoning and hence can be solved by changing the directory to lecture1. With the working directory changed, files and directories under lecture1 can be accessed and ls messages displays the files underneath messages. 
```
[user@sahara ~]$ cat lecture1
cat: lecture1: Is a directory
```
3. cat<directory>: the working directory is home. cat is meant to print the contents of a given file but since the given is a directory, cat tells the user that lecture1 is a directory, not a file. This is an error because cat expects a file so it does not print out the contents like it should since a directory is given instead. 


# Share an example of using the command with a path to a file as an argument.

```
[user@sahara ~]$ cd lecture1
[user@sahara ~/lecture1]$ cd README
bash: cd: README: Not a directory

```
1. cd <file>: since no files exist in the home directory, I first changed the working directory to lecture1. Then I tried to cd README (a file) but the output yields an error message. This is because a file is not a directory so it will not work. Unlike directories, files cannot store other files or directories so you cannot work with things in a file since there’s nothing in there other than its own content.

```
[user@sahara ~/lecture1]$ ls README
README
[user@sahara ~/lecture1]$ ls Hello.class
Hello.class
```
2. ls <file>: the working directory is lecture1. The output is the exact same as the given file. Since there are no files or folders under the file, ls just lists out the file inputed. This is an error because ls expects a directory since a file has no files/directories inside of itself, ls cannot display anything except the inputted file. 

```
[user@sahara ~/lecture1]$ cat README
To use this program:

javac Hello.java
java Hello messages/en-us.txt
[user@sahara ~/lecture1]$ cat Hello.java
import java.io.IOException;
import java.nio.charset.StandardCharsets;
import java.nio.file.Files;
import java.nio.file.Path;

public class Hello {
  public static void main(String[] args) throws IOException 
{
    String content = Files.readString(Path.of(args[0]), Stan
dardCharsets.UTF_8);    
    System.out.println(content);
  }
```
3. cat <file>: the working directory is lecture1. The command displays the content inside the specified file. This is not an error. 

