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
$ logit help
$ logit start
```



#### Installation

Copy the file logit and logit_sh to /usr/local/bin
If they are not already, make the scripts executable using __chmod a+x logit__ and __chmod a+x logit_sh__

#### Operation



#### Customizing