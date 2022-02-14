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

## sudo ##

All the demonstrations created have a user configured with sudo capabilities to provide the user with administrative (admin) privileges when required. sudo allows users to run programs using the security privileges of another user, generally root (superuser). 

On your own systems, you may need to set up and enable sudo to work correctly. To do this, you need to follow some steps that we will not explain in much detail now, but you will learn about later in this course. When running on Ubuntu and some other recent distributions, sudo is already always set up for you during installation. On other Linux distributions, you will likely need to set up sudo to work properly for you after the initial installation.

Next, you will learn the steps to set up and run sudo on your system.

## Steps for Setting Up and Running sudo ##
If your system does not already have sudo set up and enabled, you need to do the following steps:

    You will need to make modifications as the administrative or superuser, root. While sudo will become the preferred method of doing this, we do not have it set up yet, so we will use su (which we will discuss later in detail) instead. At the command line prompt, type su and press Enter. You will then be prompted for the root password, so enter it and press Enter. You will notice that nothing is printed; this is so others cannot see the password on the screen. You should end up with a different looking prompt, often ending with ‘#’. For example:
    $ su Password:
    #
    Now, you need to create a configuration file to enable your user account to use sudo. Typically, this file is created in the /etc/sudoers.d/ directory with the name of the file the same as your username. For example, for this demo, let’s say your username is student. After doing step 1, you would then create the configuration file for student by doing this:
    # echo "student ALL=(ALL) ALL" > /etc/sudoers.d/student
    Finally, some Linux distributions will complain if you do not also change permissions on the file by doing:
    # chmod 440 /etc/sudoers.d/student

That should be it. For the rest of this course, if you use sudo you should be properly set up. When using sudo, by default you will be prompted to give a password (your own user password) at least the first time you do it within a specified time interval. It is possible (though very insecure) to configure sudo to not require a password or change the time window in which the password does not have to be repeated with every sudo command.

## virtual terminal ##
Virtual Terminals (VT) are console sessions that use the entire display and keyboard outside of a graphical environment. Such terminals are considered "virtual" because, although there can be multiple active terminals, only one terminal remains visible at a time. A VT is not quite the same as a command line terminal window; you can have many of those visible at once on a graphical desktop.

One virtual terminal (usually number one or seven) is reserved for the graphical environment, and text logins are enabled on the unused VTs. Ubuntu uses VT 7, but CentOS/RHEL and openSUSE use VT 1 for the graphical display.

An example of a situation where using VTs is helpful is when you run into problems with the graphical desktop. In this situation, you can switch to one of the text VTs and troubleshoot.

To switch between VTs, press CTRL-ALT-function key for the VT. For example, press CTRL-ALT-F6 for VT 6. Actually, you only have to press the ALT-F6 key combination if you are in a VT and want to switch to another VT.

## Turning Off the Graphical Desktop ##

Linux distributions can start and stop the graphical desktop in various ways. The exact method differs from distribution and among distribution versions. For the newer systemd-based distributions, the display manager is run as a service, you can stop the GUI desktop with the systemctl utility and most distributions will also work with the telinit command, as in:

$ sudo systemctl stop gdm (or sudo telinit 3)

and restart it (after logging into the console) with:

$ sudo systemctl start gdm (or sudo telinit 5)

On Ubuntu versions before 18.04 LTS, substitute lightdm for gdm.

## Killing the Graphical User Interface ## 

Methods of bringing down the GUI:

student:/tmp> sudo systemctl stop gdm
student:/tmp> sudo systemctl stop lightdm
student:/tmp> sudo telinit 3
      

Methods of bringing the GUI back up:

student:/tmp> sudo systemctl start gdm
student:/tmp> sudo systemctl start lightdm
student:/tmp> sudo telinit 5

## Basic Operations ##

In this section, we will discuss how to accomplish basic operations from the command line. These include how to log in and log out from the system, restart or shut down the system, locate applications, access directories, identify absolute and relative paths, and explore the filesystem.

![image](https://courses.edx.org/assets/courseware/v1/678d889dcb1112024ef10815f9210a07/asset-v1:LinuxFoundationX+LFS101x+2T2021+type@asset+block/LFS01_ch06_screen11.jpg)

## Logging In and Out ##

An available text terminal will prompt for a username (with the string login:) and password. When typing your password, nothing is displayed on the terminal (not even a * to indicate that you typed in something), to prevent others from seeing your password. After you have logged into the system, you can perform basic operations.

Once your session is started (either by logging into a text terminal or via a graphical terminal program), you can also connect and log into remote systems by using Secure SHell (SSH). For example, by typing ssh student@remote-server.com, SSH would connect securely to the remote machine (remote-server.com) and give student a command line terminal window, using either a password (as with regular logins) or cryptographic key to sign in without providing a password to verify the identity.

## Rebooting and Shutting Down ##

The preferred method to shut down or reboot the system is to use the shutdown command. This sends a warning message, and then prevents further users from logging in. The init process will then control shutting down or rebooting the system. It is important to always shut down properly; failure to do so can result in damage to the system and/or loss of data.

The halt and poweroff commands issue shutdown -h to halt the system; reboot issues shutdown -r and causes the machine to reboot instead of just shutting down. Both rebooting and shutting down from the command line requires superuser (root) access.

When administering a multi-user system, you have the option of notifying all users prior to shutdown, as in:

$ sudo shutdown -h 10:00 "Shutting down for scheduled maintenance."

NOTE: On recent Wayland-based Linux distributions, broadcast messages do not appear on terminal emulation sessions running on the desktop; they appear only on the VT console displays.

## Locating Applications ##
Depending on the specifics of your particular distribution's policy, programs and software packages can be installed in various directories. In general, executable programs and scripts should live in the /bin, /usr/bin, /sbin, /usr/sbin directories, or somewhere under /opt. They can also appear in /usr/local/bin and /usr/local/sbin, or in a directory in a user's account space, such as /home/student/bin.

One way to locate programs is to employ the which utility. For example, to find out exactly where the diff program resides on the filesystem:

$ which diff
/usr/bin/diff

If which does not find the program, whereis is a good alternative because it looks for packages in a broader range of system directories:

$ whereis diff
diff: /usr/bin/diff /usr/share/man/man1/diff.1.gz /usr/share/man/man1p/diff.1p.gz

as well as locating source and man files packaged with the program.

## Accessing Directories ##

When you first log into a system or open a terminal, the default directory should be your home directory. You can print the exact path of this by typing echo $HOME. Many Linux distributions actually open new graphical terminals in $HOME/Desktop. The following commands are useful for directory navigation:

Command     |    	Result
----------- | ------------------------------------------------------------------
pwd 	    |   Displays the present working directory
cd ~ or     |   cd 	Change to your home directory (shortcut name is ~ (tilde))
cd .. 	    |   Change to parent directory (..)
cd - 	    |   Change to previous directory (- (minus))

## Understanding Absolute and Relative Paths ##
There are two ways to identify paths:

    Absolute pathname
    An absolute pathname begins with the root directory and follows the tree, branch by branch, until it reaches the desired directory or file. Absolute paths always start with /.
    Relative pathname
    A relative pathname starts from the present working directory. Relative paths never start with /.

Multiple slashes (/) between directories and files are allowed, but all but one slash between elements in the pathname is ignored by the system. ////usr//bin is valid, but seen as /usr/bin by the system.

Most of the time, it is most convenient to use relative paths, which require less typing. Usually, you take advantage of the shortcuts provided by: . (present directory), .. (parent directory) and ~ (your home directory).

For example, suppose you are currently working in your home directory and wish to move to the /usr/bin directory. The following two ways will bring you to the same directory from your home directory:

    Absolute pathname method
    $ cd /usr/bin
    Relative pathname method
    $ cd ../../usr/bin

In this case, the absolute pathname method requires less typing.

![image](https://courses.edx.org/assets/courseware/v1/c9a79bc0bfc23d476b1c89380ca90aad/asset-v1:LinuxFoundationX+LFS101x+2T2021+type@asset+block/LFS01_ch06_screen19.jpg)

## Exploring the Filesystem ##
Traversing up and down the filesystem tree can get tedious. The tree command is a good way to get a bird’s-eye view of the filesystem tree. Use tree -d to view just the directories and to suppress listing file names.

The following commands can help in exploring the filesystem:

Command | 	Usage
------- | ------------------------------------------------------------------------------------------
cd / 	|   Changes your current directory to the root (/) directory (or path you supply)
ls 	    |   List the contents of the present working directory
ls –a 	|   List all files, including hidden files and directories (those whose name start with . )
tree 	|   Displays a tree view of the filesystem
