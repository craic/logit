### Logit

#### Introduction

Recording unix shell commands is not as easy at it should be. 

The history and script built in commands help but in my work I needed a way to selectively record 
certain commands from my history. Cutting and pasting them into a file is not efficient. 

In addition I wanted a way to add comments to the log that described what each command was doing for future reference.

logit provides a way to do this. It first creates a custom bash shell instance in which you work. You run the logit
script to record previous commands and/or add comments. All the logit output goes to a specified log file.

You have complete control over what goes into the file.

So you can simply skip over general commands like ls or more that you inevitably use during a work session.

By adding descriptive comments, the output log file can serve as an annotated record of a work session and may be basis
for a shell script that can repeat the tasks on demand.



#### Example Session

```bash
jones$ logit start
Logit session started --------- 'logit help' for more information, 'exit' to end session
Commands are written to /Users/jones/Documents/craic/craic/logit/sandbox/logit.log

jones logit $ ls -l 
total 24
-rw-r--r--@ 1 jones  staff   579 Jun 13 11:15 README
[...]
jones logit $ logit
ls -l 
jones logit $ logit 'List all the files in this directory'
jones logit $ exit
exit
jones$
```

The default log file is logfile.log in the current working directory when logit is started

The log file from this example looks like
<pre>
#--------------------------------------------------------
# Session started by jones at Thu Jun 14 07:50:29 PDT 2012
#
ls -l 
# List all the files in this directory
</pre>

#### Installation

Copy the file logit and logit_sh to /usr/local/bin
If they are not already, make the scripts executable using __chmod a+x logit__ and __chmod a+x logit_sh__

#### Operation



#### Customizing