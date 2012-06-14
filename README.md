### Logit

#### Introduction

Recording unix shell commands is not as easy at it should be. 

The history and script built in commands help but in my work I needed a way to selectively record 
certain commands from my history. Cutting and pasting them into a file is not efficient. 

In addition I wanted a way to add comments to the log that described what each command was doing for future reference.

__logit__ provides a way to do this. It first creates a custom bash shell instance in which you work. You run the logit
script to record previous commands and/or add comments. All the logit output goes to a specified log file.

You have complete control over what goes into the file. So you can simply skip over general commands like 
ls or more that you inevitably use during a work session.

By adding descriptive comments, the output log file can serve as an annotated record of a work session and may be basis
for a shell script that can repeat the tasks on demand.

#### Installation

Copy the file __logit__ and __logit_sh__ to __/usr/local/bin__

If they are not already, make the scripts executable using __chmod a+x logit__ and __chmod a+x logit_sh__

#### Usage

```shell
Usage
   logit start                      Start a logit shell and log commands to logit.log
   logit start <filename>           Start a logit shell and log commands to supplied file

   logit "this is a comment"        Log the quoted string as a comment

   logit                            Log the previous command
   logit 0 "this is a comment"      Log the previous command preceded by a comment line

   logit -N                         Log the Nth previous command
   logit -N "this is a comment"     Log the Nth previous command preceded by a comment line

   logit N                          Log a specific command from the history
   logit N "this is a comment"      Log a specific command from the history preceded by a comment line

   logit show                       Output the contents of the logit log file
```

__logit start__ creates a Bash sub shell, with a modified prompt, in which you can call __logit__ to record specific commands and comments.

The need for a sub shell is due to the limitations and quirks of the Bash history mechanism.

The default log file is __logfile.log__ in the current working directory when logit is started. You can supply an alternate file
as a argument to __logit start__


#### Example Session

```bash
jones$ logit start my.log
Logit session started --------- 'logit help' for more information, 'exit' to end session
Commands are written to my.log

jones logit $ logit 'this is an example logit session'
jones logit $ date
Thu Jun 14 14:11:17 PDT 2012
jones logit $ logit
date
jones logit $ echo A
A
jones logit $ echo B
B
jones logit $ logit -1 'log the command before the last one'
echo A
jones logit $ exit
jones$
```


The log file from this example looks like
<pre>
#--------------------------------------------------------
# Session started by jones at Thu Jun 14 14:10:57 PDT 2012
#
# this is an example logit session
date
# log the command before the last one
echo A
</pre>


#### Customizing

The prompt within a logit sub shell has the word 'logit' in red. This reminds you that you are working in a logit shell.
You can change the color of this to another ANSI terminal color by setting the environment variable LOGIT_COLOR before
your start a logit shell. You can enter any of the ANSI color escape codes of the form '00;34'.

For example this changes the color to blue:
```shell
$ export LOGIT_COLOR="00;34"
```


#### License

This code is freely distributed under the terms of the MIT license

<pre>
	Copyright (c) 2012  Robert Jones

	Permission is hereby granted, free of charge, to any person obtaining a copy of this software 
	and associated documentation files (the "Software"), to deal in the Software without restriction,
	including without limitation the rights to use, copy, modify, merge, publish, distribute, 
	sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is 
	furnished to do so, subject to the following conditions:

	The above copyright notice and this permission notice shall be included in all copies or 
	substantial portions of the Software.

	THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING 
	BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND 
	NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, 
	DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, 
	OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
</pre>
