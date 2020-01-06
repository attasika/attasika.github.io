---
layout: default
---

## Introduction to the Course

![Ubuntu logo](https://homecoder.files.wordpress.com/2012/08/logo-ubuntu_st_noc2ae-black_orange-hex.png)

The _Command Line Tools for Linguists_ course provided a nice introduction to back end with basic command line functions and examples of linguistic processing capabilities the command line can offer. Additionally, standard development project workflow concepts such as `git` and GitHub, were introduced. The course helped me approach syntax with a more analytical perspective. In the end of the course I feel now much more comfortable in a command line environment than before.

### Week 1: Introduction to Command Line Environments

On the first week of the course we set up the command line environment and walked through the most basic commands and principles regarding the command line. The first step for me was to mount Ubuntu on my Windows 10 system. I learned how the mounted operating system relates to the original mount OS and briefly about relations of bash, MS-DOS, Unix and Linux. We practiced using the very most basic Unix commands for instance for changing directories, listing contents of a directory, viewing contents of a text file, creating, renaming, moving, copying and deleting files and directories. These were somewhat familiar to me from the _Introduction to Language Technology_ course, but this was a much needed recap, as on the previous course we only briefly considered basic Unix commands. Then we looked into other Unix commands such as `wget` for fetching files from the web, `cat` for printing contents of files, and `echo` for printing input text as output. Additionally, a very important time-saving function, tab completion was introduced, that I found extremely powerful. We also learned the basics of two command-line based text editors, Emacs and the more simple Nano. Almost the entire content of the first week was crucial for the rest of the course. The skills learned on the first week were refined and learned by heart during the remainder of the course.

#### Command examples:

A table of some of the most very basic Unix commands:

Command | Function
--- | --- 
`cd <directoryname>` | change directory
`ls <optional directoryname>` | list contents of a directory
`touch <filename>` | create a new file
`mv <filename> <new filename>` | rename file
`mv <filename> <directory name>` | move file
`cp <filename> <new filename or directory name>` | copy file
`rm <filename>` | remove file
`less <filename>` | view contents of a file

This command we used in the first quiz to download a text file from the Internet:
```
$ wget http://www.gutenberg.org/files/215/215-0.txt
```

### Week 2: Navigating a UNIX System

On the second week of the course we learned how to get around a Unix system quicker. We also learned the differences between relative and absolute paths and some important directories in the Unix system (bin, temp, and usr). Additionally, the `ls` command was covered more in depth. Now in the end of the course I personally find most practical in most cases to use `ls -1` to list contents each item on a separate line to effortlessly analyze the output. We also considered how command options work and how they can be stringed together.

Additionally, the concept of file permissions work on Unix-like systems. The matter seemed quite hard at first to approach, but I think I managed to get a pretty good idea of the `drwxrwxrwx` and octal representations of permissions on Linux. 

Moreover, we considered basic zipping and unzipping commands of files and directories, how to log in and out of remote servers and transfer data between local and remote directories and finally we familiarized ourselves with Unix processes and the concept of foreground and background. The second week was a lot to digest, but I think I got quite a good hang of everything that was discussed. 

#### Syntax examples:

* `mv <path to file> .` moves a file to current working directory
* `cd ..` change directory one step up in the directory hierarchy
* `cd -` change directory to previous directory
* `cd` change directory to home directory, the `~`
* `cd /` change directory to root

### Week 3: Basic Corpus Processing

The week 3 taught us the basic principles of character encodings and conversion between different encodings. The caracter encodings were somewhat familiar from the previous course, but it was good to dive a little bit deeper in to the considered matter. We also examined some linguistically relevant commands such as `tr`, `sort`, `uniq`, `wc` and `grep`. Moreover, we took a closer look at stream redirection and efficient use of `cat` alongside stream redirection. Also pipes were introduced to demonstrate how to transfer a command's output into another command's input. We became familiar with the `/dev/null/` directory as well to find a way to redirect unwanted output into trash. Additionally, we went through a recap on `egrep`, that was already familiar from the previous course. For me it was much needed, because I had most of the regular expression rules already forgotten.

Finally, we considered formatted text files with main focus on csv (comma-separated values) files. We tried some basic csv file editing commands in practice, such as `split`, `cut`, `paste` and `join`. The logic behind formatted text files was not so familiar to me from before, but now I feel much more comfortable with them.

#### Syntax examples:

* `echo <input> > file.txt` creates a text file `file.txt` with contents specified after `echo`

* `echo <input> >> file.txt` appends specified contents to the end of file.txt

* `cat file1.txt file2.txt > file3.txt` creates a new file `file3.txt` with contents from both `file1.txt` and `file2.txt`

### Week 4: Advanced Corpus Processing

On the fourth week we dived deep into the `sed` (stream editor) command. We learned that it is an extremely powerful tool for processing text files. In short and in my opinion, the `sed` command's functionality starts where the `tr` command's capabilities ends. With the `sed` command, the concept of back-referencing became familiar as well. 

We also saw how commands could be stringed together to perform more complicated tasks with a single prompt. This helped me understand better what programming could be in practice (having never really programmed anything before). In addition to pipelines, we also considered the `diff` command in detail to understand how it can be used in many ways to find differences between text files.

Finally, we refined our regular expression skills further with Regex Crossword puzzles, that I ultimately found very fun and addictive! Having enjoyed doing some Sudoku puzzles in the past, the Regex Puzzles was personally a highly positive experience in practicing regular expressions. 

#### Pipeline example:

The following pipeline introduced in the technical videos transforms a text file into sentence per line format. The original file is not overwritten.
```
cat life_of_bee.txt  | dos2unix | sed 's/^$/#/' | tr '\n' ' ' | sed -E 's/([.?!]) ([A-Z])/\1# \2/g' | sed -E 's/([IVX][.])#/\1/g' | tr '#' '\n' | sed 's/^ *//' | sed 's/ *$//' | grep -v "^$" > life_of_bee.sent
```

### Week 5: Scripting and Configuration Files

The fifth week was probably the heaviest for me on this course. With lots of content on the week and with no previous experience in programming, for the first time on this course I really struggled to complete the quiz. But ultimately, I did!

First we were taught the formalities and typical structure of a bash script file (.sh file). We became familiar with the shebang, `#!`. Then we examined how scripts could be run and how permissions are related to .sh files. 

Then we saw how variables work in a script and looked more closely what is the practical difference between single and double quotation marks. Additionally we learned about `if`, `if else` and `case` sentences and their syntax. 

Then we examined exit codes and found out about their importance in bash script files. We also familiarized ourselves with environment variables with spotlight on the `PATH` variable, and the `export` command.

Finally we learned how to customize configuration files such as `.bashrc` and `.profile` to tune our command prompt according to our preferences. Creating aliases with the `alias` command was an important part of this process.

#### Configuration file syntax example

One part of the configuration file customization process was to customize the command prompt's look and layout. I prefer the standard Ubuntu layout, but wanted to change the colors of the prompt to something "cooler" than the original. This syntax was created with http://bashrcgenerator.com/ introduced in the reading materials of the week.

```
export PS1="\[\033[38;5;14m\]\u@\h\[$(tput sgr0)\]\[\033[38;5;15m\]:\[$(tput sgr0)\]\[\033[38;5;33m\]\w\[$(tput sgr0)\]\[\033[38;5;15m\]\\$\[$(tput sgr0)\] "
```
 
### Week 6: Installing and Running Programs


On the sixth week we first looked at `su` and `sudo` in more depth. Then we familiarized ourselves with software libraries and dependency trees closely related to Unix-like systems. We found that installing and updating software on Linux is much more convenient with Linux in comparison to Windows because of package managers. We tried in practice searching for available software, installing and removing them.

Then we tried the `pip` command for managing and installing python packages. We found out how to create requirements lists and how to use virtual environments, as well. Finally, we dived deep into the world of Makefiles and their syntax.

To me, getting the Makefile right was the toughest part of the week. With re-watching the videos and trial-and-error procedures, I finally was able to figure out what was missing from my file. Additionally managing python packages felt like a mess due to the number of different python versions. Using the `pip` command will probably be more convenient in the future, in case I need python in the future.

#### Syntax example:

This is the rule I struggled so much on week 6 to get right. This is a rule in the Makefile that compiles all books in the data directory without metadata in to a single file.

```
data/all.no_md.txt: $(BOOKS:%=data/%.no_md.txt)
	cat $^ > data/all.no_md.txt
```

### Week 7: Version Control

The final week before the final assignment introduced the concept of version control. Automatic version control (or version history) was already familiar for me from Google Drive, for example. On the other hand, the most popular version control tool `git` was introduced on this course for manual but very efficient version control. We walked through basic `git` functions like initiating version control, the staging area, committing and branches. We learned how commit messages are crucial in case a specific older version of a file was wanted to be found.

We also created our own GitHub account and set up a remote repository. We learned how to clone an existing remote repository from GitHub to our local computer, as well. Then we also learned how to push changes to a remote repository and how to undo almost anything with `git`. 

As the `git` command is far more versatile and complex compared to most of other commands learned on this course, it seemed like quite a lot to take in. On the other hand, while working on the final assignment of the course, I think I learned by heart quite well the most basic `git` workflow.

#### Command example:

This is a crucial `git` command that makes it possible to push changes to a remote repository and pull changes from a remote repository after having cloned it to a local computer:

```
git remote add <reponame> <repourl>
```


### The final week: Building Webpages using GitHub Pages

On the very final week of the course, we learned that Jekyll is a static simplified web page generator that generates html pages from simpler Markdown text. We also learned that GitHub can be used to build and host web pages and this we did in practice. In addition, we acquired basic Markdown skills by going through the tutorial and creating student's very own pages from a template for the final assignment. Markdown was not either familiar to me from before, but was not difficult to learn due to its low abstractness.

Additionally, we used Overleaf to build ourselves a fancy _Curriculum Vitae_. Overleaf was already introduced on the previous course as well, but I frustrated with it back then probably because I might have missed the tutorial video shown (again?) on this course, which helped me understand better how I should approach LaTeX. Now having compiled my CV in Overleaf I feel considerably more comfortable with LaTeX and Overleaf.

#### Command example:

When working in the web page project directory, this command compiles locally webpages from Markdown files. The resulting page can then be viewed in a web browser to evaluate the appearance of the pages.

```
bundle exec jekyll serve
```

