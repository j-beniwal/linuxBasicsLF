# Chapter 13 : Manipulating Text #

## ntroduction ##

### Learning Objectives ###
By the end of this chapter, you should be able to:

* Display and append to file contents using cat and echo. 
* Edit and print file contents using sed and awk.
* Search for patterns using grep.
* Use multiple other utilities for file and text manipulation.

## cat and echo ##

### Command Line Tools for Manipulating Text Files ###

Irrespective of the role you play with Linux (system administrator, developer or user), you often need to browse through and parse text files, and/or extract data from them. These are file manipulation operations. Thus, it is essential for the Linux user to become adept at performing certain operations on files.

Most of the time, such file manipulation is done at the command line, which allows users to perform tasks more efficiently than while using a GUI. Furthermore, the command line is more suitable for automating often executed tasks.

Indeed, experienced system administrators write customized scripts to accomplish such repetitive tasks, standardized for each particular environment. We will discuss such scripting later in much detail.

In this section, we will concentrate on command line file and text manipulation-related utilities.

### cat ###

cat is short for concatenate and is one of the most frequently used Linux command line utilities. It is often used to read and print files, as well as for simply viewing file contents. To view a file, use the following command:

    $ cat <filename>

For example, cat readme.txt will display the contents of readme.txt on the terminal. However, the main purpose of cat is often to combine (concatenate) multiple files together. You can perform the actions listed in the table using cat.

The tac command (cat spelled backwards) prints the lines of a file in reverse order. Each line remains the same, but the order of lines is inverted. The syntax of tac is exactly the same as for cat, as in:

$ tac file
$ tac file1 file2 > newfile

Command 	                 |   Usage
---------------------------- | ------------------------------------------
cat file1 file2 	         |   Concatenate multiple files and display the output; i.e. the entire content of the first file is followed by that of the second file
cat file1 file2 > newfile |	    Combine multiple files and save the output into a new file
cat file >> existingfile 	|    Append a file to the end of an existing file
cat > file 	              |      Any subsequent lines typed will go into the file, until CTRL-D is typed
cat >> file 	             |   Any subsequent lines are appended to the file, until CTRL-D is typed

### Using cat Interactively ###

cat can be used to read from standard input (such as the terminal window) if no files are specified. You can use the > operator to create and add lines into a new file, and the >> operator to append lines (or files) to an existing file. We mentioned this when talking about how to create files without an editor.

To create a new file, at the command prompt type cat > <filename> and press the Enter key.

This command creates a new file and waits for the user to edit/enter the text. After you finish typing the required text, press CTRL-D at the beginning of the next line to save and exit the editing.

Another way to create a file at the terminal is cat > <filename> << EOF. A new file is created and you can type the required input. To exit, enter EOF at the beginning of a line.

Note that EOF is case sensitive. One can also use another word, such as STOP.

![cat demo image](https://courses.edx.org/assets/courseware/v1/2186f2162bb7f8d6f7fac9004f7d4784/asset-v1:LinuxFoundationX+LFS101x+2T2021+type@asset+block/cateoffedora.png)

### echo ###

echo simply displays (echoes) text. It is used simply, as in:

    $ echo string

echo can be used to display a string on standard output (i.e. the terminal) or to place in a new file (using the > operator) or append to an already existing file (using the >> operator).

The –e option, along with the following switches, is used to enable special character sequences, such as the newline character or horizontal tab:

* \n represents newline
* \t represents horizontal tab.

echo is particularly useful for viewing the values of environment variables (built-in shell variables). For example, echo $USERNAME will print the name of the user who has logged into the current terminal.

The following table lists echo commands and their usage:

Command 	                   | Usage
------------------------------ | -------------------------------------------------
echo string > newfile 	     |   The specified string is placed in a new file
echo string >> existingfile |	The specified string is appended to the end of an already existing file
echo $variable 	            |    The contents of the specified environment variable are displayed

## Working with Large and Compressed Files ##

### Working with Large Files ###

System administrators need to work with configuration files, text files, documentation files, and log files. Some of these files may be large or become quite large as they accumulate data with time. These files will require both viewing and administrative updating. In this section, you will learn how to manage such large files.

For example, a banking system might maintain one simple large log file to record details of all of one day's ATM transactions. Due to a security attack or a malfunction, the administrator might be forced to check for some data by navigating within the file. In such cases, directly opening the file in an editor will cause issues, due to high memory utilization, as an editor will usually try to read the whole file into memory first. However, one can use less to view the contents of such a large file, scrolling up and down page by page, without the system having to place the entire file in memory before starting. This is much faster than using a text editor.

Viewing somefile can be done by typing either of the two following commands:

    $ less somefile
    $ cat somefile | less

By default, man pages are sent through the less command. You may have encountered the older more utility which has the same basic function but fewer capabilities: i.e. less is more!

### head ### 

head reads the first few lines of each named file (10 by default) and displays it on standard output. You can give a different number of lines in an option.

For example, if you want to print the first 5 lines from /etc/default/grub, use the following command:

    $ head –n 5 /etc/default/grub

You can also just say:

    head -5 /etc/default/grub

### tail ###

tail prints the last few lines of each named file and displays it on standard output. By default, it displays the last 10 lines. You can give a different number of lines as an option. tail is especially useful when you are troubleshooting any issue using log files, as you probably want to see the most recent lines of output.

For example, to display the last 15 lines of somefile.log, use the following command:

    $ tail -n 15 somefile.log

You can also just say:

    tail -15 somefile.log

To continually monitor new output in a growing log file:

    $ tail -f somefile.log

This command will continuously display any new lines of output in somefile.log as soon as they appear. Thus, it enables you to monitor any current activity that is being reported and recorded.

### Viewing Compressed Files ###

When working with compressed files, many standard commands cannot be used directly. For many commonly-used file and text manipulation programs, there is also a version especially designed to work directly with compressed files. These associated utilities have the letter "z" prefixed to their name. For example, we have utility programs such as zcat, zless, zdiff and zgrep.

Here is a table listing some z family commands:

 Command 	                              |  Description
----------------------------------------- | --------------------------------
$ zcat compressed-file.txt.gz 	         |   To view a compressed file
$ zless somefile.gz or $ zmore somefile.gz |	To page through a compressed file
$ zgrep -i less somefile.gz 	           | To search inside a compressed file
$ zdiff file1.txt.gz file2.txt.gz 	     |   To compare two compressed files

Note that if you run zless on an uncompressed file, it will still work and ignore the decompression stage. There are also equivalent utility programs for other compression methods besides gzip, for example, we have bzcat and bzless associated with bzip2, and xzcat and xzless associated with xz.

##