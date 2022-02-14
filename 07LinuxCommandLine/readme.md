# Command-Line Mode Options #

Linux system administrators spend a significant amount of their time at a command line prompt. They often automate and troubleshoot tasks in this text environment. There is a saying, "graphical user interfaces make easy tasks easier, while command line interfaces make difficult tasks possible". Linux relies heavily on the abundance of command line tools. The command line interface provides the following advantages:

    * No GUI overhead is incurred.
    * Virtually any and every task can be accomplished while sitting at the command line.
    * You can implement scripts for often-used (or easy-to-forget) tasks and series of procedures.
    * You can sign into remote machines anywhere on the Internet.
    * You can initiate graphical applications directly from the command line instead of hunting through menus.
    * While graphical tools may vary among Linux distributions, the command line interface does not.

## Some Basic Utilities ##
There are some basic command line utilities that are used constantly, and it would be impossible to proceed further without using some of them in simple form before we discuss them in more detail. A short list has to include:

    * cat: used to type out a file (or combine files).
    * head: used to show the first few lines of a file.
    * tail: used to show the last few lines of a file.
    * man: used to view documentation.

The screenshot shows elementary uses of these programs. Note the use of the pipe symbol (|) used to have one program take as input the output of another.

For the most part, we will only use these utilities in screenshots displaying various activities, before we discuss them in detail.

## The Command Line ##
Most input lines entered at the shell prompt have three basic elements:

    * Command
    * Options
    * Arguments

The command is the name of the program you are executing. It may be followed by one or more options (or switches) that modify what the command may do. Options usually start with one or two dashes, for example, -p or --print, in order to differentiate them from arguments, which represent what the command operates on.

However, plenty of commands have no options, no arguments, or neither. In addition, other elements (such as setting environment variables) can also appear on the command line when launching a task.