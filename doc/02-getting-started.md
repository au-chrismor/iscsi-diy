# Getting Started

## Shopping List

You are going to need some parts to do this.  While you could run everything in a virtual machine, it's not really ideal for serious workloads.  That said, everything presented here (except for scalable networking) has been prototyped in KVM and VMWare Player, so it can be done.  Perhaps later I will make some virtual discs available for experimenting.

You will need a client system of some kind.  This could be FreeBSD, Windows, Solaris or Linux.  Because we're mucking around at a low level, it might be best not to use your main system, at least at first.

It probably goes without saying that you'll need a copy for FreeBSD.  I recommend using a current release (14.1 as of October 2024).  Head over to https://www.freebsd.org/where/ to get a copy

### A Starter System

This is the ideal way to learn.  You could use a recycled desktop system if you wanted.  Your requirements are along the following lines:

- A 64-bit computer system.  I used an HP Microserver (N54)
- 4 to 8GB RAM
- At least 2 physical discs
- 1 or 2 gigabit ethernet adapters
- A gigabit ethernet switch (nothing fancy at this stage)

### Something More Serious

Let's build on what we've learned, and make it faster and more reliable.  We'll need:

- A faster machine, preferably with a Xeon or Epyc processor
- 16GB or more RAM
- At least 4 physical discs.  One of those can be nVME
- 3 or more gigabit network adapters
- A gigabit switch which supports LACP link aggregation

### Enterprise Grade

Taking everything we built last time, let's make it even more flexible than before:

- You can use the "serious" machine, but you may want more RAM
- More disks with, or without hardware RAID
- 1 or more 10Gb ethernet adapters
- An ethernet switch capable of 10Gb and compatible with your adapters.
- If you want to do replication, you'll need two of everything except the switch

#### A note on other processor families

While it's true that FreeBSD is available for non-x86 platorms (specifically PowerPC, ARM and RISC-V) I've specified 64-bit x86 machines because:

- The x86-64 hardware readily available.
- RISC-V systems tend to have limited memory and hardware support right now.
- PowerPC systems tend to be quite expensive, compared to x86.
- Big ARM systems do exist, but they are not easily obtained.
- i386 systems will struggle for memory as your system grows in capability and capacity.

## Let's Get Started

I am *not* going to repeat the installation instructions step by step.  The FreeBSD Handbook is your best resource here.  If you have never installed FreeBSD, follow the steps at https://docs.freebsd.org/en/books/handbook/bsdinstall/  Even if you're an old hand, pay attention to the following points:

- Only install the base operating system, and prepare just the first disc.  We'll get to the other drives soon.
- If you have more than one ethernet card, just configure one for now.
- Don't install a Windowing system.
- Do create a user for yourself.  Add yourself the the "wheel" group so that you can use "su" and not have to log in as root.

## What Now?

Like just about any software, FreeBSD is regularly updated.  Fortunately there's a handy process for doing this called "freebsd-update".  Full instructions can be found at https://docs.freebsd.org/en/books/handbook/cutting-edge/#updating-upgrading-freebsdupdate but in essence, you use "freebsd-update fetch" to download all the relevant updates and then "freebsd-update install" to install them.  If a reboot is required, freebsd-update will tell you, but after the installation, I usually restart anyway, just to be sure.

