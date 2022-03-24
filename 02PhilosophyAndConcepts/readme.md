# Linux Terminology #
Before you begin using Linux, you need to be aware of some basic terms such as kernel, distribution, boot loader, service, filesystem, X Window system, desktop environment, and command line. These are very commonly used by the Linux community.

**kernel:**
The *kernel* is considered the brain of the Linux operating system. It controls the hardware and makes the hardware interact with the applications. An example of a kernel is the Linux kernel. The most recent Linux kernel, along with past Linux kernels, can be found at the kernel.org web site.

**distribution:**
A *distribution* also known as Distros is a collection of programs combined with the Linux kernel to make up a Linux-based operating system. Some common examples of a distribution are Red Hat Enterprise Linux, Fedora, Ubuntu, and Gentoo.

**boot loader:**
The *boot loader*, as the name implies, is a program that boots the operating system. Two examples of a boot loader are GRUB and ISOLINUX.

**service:**
A *service* is a program that runs as a background process. Some examples of the service are httpd, nfsd, ntpd, ftpd and named.

**filesystem:**
A *filesystem* is a method for storing and organizing files in Linux. Some examples of filesystems are ext3, ext4, FAT, XFS and Btrfs.

**X Window System:**
The *X Window System* provides the standard toolkit and protocol to build graphical user interfaces on nearly all Linux systems.

**desktop environment:**
The *desktop environment* is a graphical user interface on top of the operating system. GNOME, KDE, Xfce and Fluxbox are some examples of the desktop environment.

**command line:**
The *command line* is an interface for typing commands on top of the operating system.

**Shell:**
The *Shell* is the command line interpreter that interprets the command line input and instructs the operating system to perform any necessary tasks and commands. For example, bash, tcsh and zsh.


# Distribution # 

So, what is a Linux distribution and how does it relate to the Linux kernel?

The Linux kernel is the core of the operating system. A full Linux distribution consists of the kernel plus a number of other software tools for file-related operations, user management, and software package management. Each of these tools provides a part of the complete system. Each tool is often its own separate project, with its own developers working to perfect that piece of the system.

While the most recent Linux kernel (and earlier versions) can always be found in The Linux Kernel Archives, Linux distributions may be based on different kernel versions. For example, the very popular RHEL 8 distribution is based on the 4.18 kernel, which is not new, but is extremely stable. Other distributions may move more quickly in adopting the latest kernel releases. It is important to note that the kernel is not an all or nothing proposition, for example, RHEL/CentOS have incorporated many of the more recent kernel improvements into their older versions, as have Ubuntu, openSUSE, SLES, etc.

Examples of other essential tools and ingredients provided by distributions include the C/C++ and Clang compilers, the gdb debugger, the core system libraries applications need to link with in order to run, the low-level interface for drawing graphics on the screen, as well as the higher-level desktop environment, and the system for installing and updating the various components, including the kernel itself. And all distributions come with a rather complete suite of applications already installed.

![this is image](https://courses.edx.org/assets/courseware/v1/be89578552325fd81fb6a9a6b613afe9/asset-v1:LinuxFoundationX+LFS101x+2T2021+type@asset+block/distroroles.png)

## Services Associated with Distributions ##

The vast variety of Linux distributions are designed to cater to many different audiences and organizations, according to their specific needs and tastes. However, large organizations, such as companies and governmental institutions and other entities, tend to choose the major commercially-supported distributions from Red Hat, SUSE, and Canonical (Ubuntu).

CentOS and CentOS Stream are popular free (as in no cost) alternatives to Red Hat Enterprise Linux (RHEL) and are often used by organizations that are comfortable operating without paid technical support. Ubuntu and Fedora are widely used by developers and are also popular in the educational realm. Scientific Linux is favored by the scientific research community for its compatibility with scientific and mathematical software packages. Both CentOS variants are binary-compatible with RHEL; i.e. in most cases, binary software packages will install properly across the distributions.

Note that CentOS is planned to disappear at the end of 2021 in favor of CentOS Stream. However, there are at least two new RHEL-derived substitutes: Alma Linux and Rocky Linux which are establishing a foothold.

Many commercial distributors, including Red Hat, Ubuntu, SUSE, and Oracle, provide long term fee-based support for their distributions, as well as hardware and software certification. All major distributors provide update services for keeping your system primed with the latest security and bug fixes, and performance enhancements, as well as provide online support resources.

![this is image](https://courses.edx.org/assets/courseware/v1/85a0445af315a7fb90444a2d3cd0e608/asset-v1:LinuxFoundationX+LFS101x+2T2021+type@asset+block/LFS01_ch02_screen_24.jpg)

# Summary #
You have completed Chapter 2. Let’s summarize the key concepts covered:

* Linux borrows heavily from the UNIX operating system, with which its creators were well-versed.
* Linux accesses many features and services through files and file-like objects.
* Linux is a fully multi-tasking, multi-user operating system, with built-in networking and service processes known as daemons.
* Linux is developed by a loose confederation of developers from all over the world, collaborating over the Internet, with Linus Torvalds at the head. Technical skill and a desire to contribute are the only qualifications for participating.
* The Linux community is a far reaching ecosystem of developers, vendors, and users that supports and advances the Linux operating system.
* Some of the common terms used in Linux are: kernel, distribution, boot loader, service, filesystem, X Window system, desktop  environment, and command line.
* A full Linux distribution consists of the kernel plus a number of other software tools for file-related operations, user management, and software package management.
