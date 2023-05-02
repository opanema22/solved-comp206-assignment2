Download Link: https://assignmentchef.com/product/solved-comp206-assignment2
<br>
<h1>Ex. 1 —  A basic shell script for searching tar files</h1>

In class we explored the tar command that can be used to archive files and entire directory structures. Sometimes we would want to check the contents of a tar file without extracting it back, such as to check if a particular filename is present in a given tar file. Programmers often keep such handy set of commands written together in the form of a shell script that can be used repeatedly.

For this task, you will create a shell script named tarzan.sh which accepts 2 arguments – the name of a file, followed by a tar file’s name. The tar file name maybe passed on using absolute path or relative path. The objective is to inform the user if a particular file is present in a tar file or not, without extracting it. The tar command provides you with an option to list all the contents in the tar file without extracting it. Use the man command to explore the tar command and find this option.

Below is an example (valid) usage.

$ ./tarzan.sh sort.c /archives/2017/gamingProject.tar

<strong> </strong>for writing code with proper (readability) indentation and writing necessary comments (required to understand the logic, etc.) in the code.

1.Use vi to create your script in mimi.cs.mcgill.ca .

2.Ensure that your script can be executed using bash shell.

3.If the script is not passed two arguments to it, you must throw an error/usage message, such as the following example.

$ ./tarzan.sh sort.c

Usage ./tarzan.sh filename tarfile

4.<strong> </strong>If the tar file cannot be found, the script should throw an error message.

$ ./tarzan.sh sort.c /archives/2017/gamingProject.tar

Error cannot find tar file /archives/2017/gamingProject.tar

5.<strong> </strong>If the tar file is found, but the filename that is searched is not present in it, the script should display this fact.

$ ./tarzan.sh sort.c /archives/2017/gamingProject.tar sort.c does not exist in /archives/2017/gamingProject.tar

6.If the script is able to locate the filename in the tar file, it should display the found message.

$ ./tarzan.sh sort.c /archives/2017/gamingProject.tar sort.c exists in /archives/2017/gamingProject.tar

<h1>Ex. 2 — A bash script for file search and content display</h1>

Search is a very essential form of interaction with the contents stored in a file system. In this task, you will write a bash shell script seeker.sh that will look for file names with a specific string in the file name and optionally display its contents to the screen.

The usage syntax for the script is as follows.

$ /seeker.sh [-c] [-a] pattern [path]

The options/arguments in square brackets are optional, and their intent is as follows.

-c indicates that the script should display the contents of the file. Otherwise only the absolute path to the file (including file name) is displayed to the screen.

-a indicates that if there are multiple matching files, the output should include all of them. Otherwise only (any) one of the file is included in the output.

path is the absolute path to the directory under which the script should look for the files. If this argument is not passed to the script, it is expected to look for files under the ”current directory”.

pattern is a string that you want the script to look for in the name of a file (NOT contents of the file). For example if pattern is msg, it should match the file names mymsg.txt, msg.txt, random.msg, lastmsgs.txt, etc. An example output of this script is as below.

<table width="681">

 <tbody>

  <tr>

   <td width="681">$ /seeker.sh -c -a msg /mydata/scribbles==== Contents of: /mydata/scribbles/msg2.txt ====Hi, I am msg2.txt Not all those who wander are lost.==== Contents of: /mydata/scribbles/msg.txt ====Hello there, I am msg.txt</td>

  </tr>

 </tbody>

</table>

<strong>2 Points </strong>for writing code with proper (readability) indentation and writing necessary comments (required to understand the logic, etc.) in the code.

1.Use vi to create your script in mimi.cs.mcgill.ca .

2.Ensure that your script can be executed using bash shell.

3.Ensure that your script is passed proper arguments. pattern is the only mandatory input to the script. An appropriate error and usage message should be raised if proper arguments are not passed into the script. See examples below.

$ ./seeker.sh

Error missing the pattern argument.

Usage ./seeker.sh [-c] [-a] pattern [path]

$ ./seeker.sh -c

Error missing the pattern argument.

Usage ./seeker.sh [-c] [-a] pattern [path]

$ ./seeker.sh -a

Error missing the pattern argument.

Usage ./seeker.sh [-c] [-a] pattern [path]

$ ./seeker.sh -c -a

Error missing the pattern argument.

Usage ./seeker.sh [-c] [-a] pattern [path]

4.<strong> </strong>If the directory passed as argument to the script does not exist, the script should display this fact.

$ ./seeker.sh msg /nosuchdir

Error /nosuchdir is not a valid directory

$ ./seeker.sh -a msg /nosuchdir

Error /nosuchdir is not a valid directory

5.<strong> </strong>If script cannot find any files with the specified pattern in its name, it should display this information.

$ ./seeker.sh -a meow /etc/cron.d

Unable to locate any files that has pattern meow in its name in /etc/cron.d.

6.<strong> </strong>When -a option is not passed, include only (any) one matching file in the output.

$ ./seeker.sh msg /scribbles/messages

/scribbles/messages/msg2.txt

7.<strong> </strong>When -a option is passed, include all the files that match the pattern

$ ./seeker.sh -a msg /scribbles/messages

/scribbles/messages/msg2.txt

/scribbles/messages/msg.txt

8.<strong> </strong>When -c option is passed, contents of the files must be displayed

<table width="651">

 <tbody>

  <tr>

   <td width="651">$ ./seeker.sh -c msg /scribbles/messages==== Contents of: /scribbles/messages/msg2.txt ====Hi, I am msg2.txt Not all those who wander are lost.$ ./seeker.sh -c -a msg /scribbles/messages==== Contents of: /scribbles/messages/msg2.txt ====Hi, I am msg2.txt Not all those who wander are lost.==== Contents of: /scribbles/messages/msg.txt ====Hello there, I am msg.txt</td>

  </tr>

 </tbody>

</table>

9.<strong> </strong>When path argument to indicate the directory to look for files is not passed, search in the current directory.

<table width="651">

 <tbody>

  <tr>

   <td width="651">$ cd /scribbles/messages$ ./seeker.sh -c -a msg==== Contents of: /scribbles/messages/msg2.txt ====Hi, I am msg2.txt Not all those who wander are lost.==== Contents of: /scribbles/messages/msg.txt ====Hello there, I am msg.txt</td>

  </tr>

 </tbody>

</table>