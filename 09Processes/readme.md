# Chapter 9: Processes #

## Introduction ##

### Learning Objectives ###

By the end of this chapter, you should be able to:

* Describe what a process is and distinguish between types of processes.
* Enumerate process attributes.
* Manage processes using ps and top.
* Understand the use of load averages and other process metrics.
* Manipulate processes by putting them in background and restoring them to foreground.
* Use *at*, *cron*, and *sleep* to schedule processes in the future or pause them.

## Introduction to Processes and Process Attributes ##

### What Is a Process? ###
A process is simply an instance of one or more related tasks (threads) executing on your computer. It is not the same as a program or a command. A single command may actually start several processes simultaneously. Some processes are independent of each other and others are related. A failure of one process may or may not affect the others running on the system.

![This is image](https://courses.edx.org/assets/courseware/v1/219d348bf46fa4b3b8c83b3dbdf3fb31/asset-v1:LinuxFoundationX+LFS101x+2T2021+type@asset+block/LFS01_ch16_screen03.jpg)

Processes use many system resources, such as memory, CPU (central processing unit) cycles, and peripheral devices, such as network cards, hard drives, printers and displays. The operating system (especially the kernel) is responsible for allocating a proper share of these resources to each process and ensuring overall optimized system utilization.

### Process Types ###
A terminal window (one kind of command shell) is a process that runs as long as needed. It allows users to execute programs and access resources in an interactive environment. You can also run programs in the background, which means they become detached from the shell.

Processes can be of different types according to the task being performed. Here are some different process types, along with their descriptions and examples:

Process Type           | 	Description                                                           |	Example
---------------------- | --------------------------------------------------------------------    | ----------------
Interactive Processes  |	Need to be started by a user, either at a command line or through a graphical interface such as an icon or a menu selection.  |	bash, firefox, top
Batch Processes        |	Automatic processes which are scheduled from and then disconnected from the terminal. These tasks are queued and work on a FIFO (First-In, First-Out) basis. |	updatedb, ldconfig
Daemons                |	Server processes that run continuously. Many are launched during system startup and then wait for a user or system request indicating that their service is required. |	httpd, sshd, libvirtd
Threads                |	Lightweight processes. These are tasks that run under the umbrella of a main process, sharing memory and other resources, but are scheduled and run by the system on an individual basis. An individual thread can end without terminating the whole process and a process can create new threads at any time. Many non-trivial programs are multi-threaded. |	firefox, gnome-terminal-server
Kernel Threads         |	Kernel tasks that users neither start nor terminate and have little control over. These may perform actions like moving a thread from one CPU to another, or making sure input/output operations to disk are completed. |	kthreadd, migration, ksoftirqd