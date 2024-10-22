# Getting Started

## Shopping List

You are going to need some parts to do this.  While you could run everything in a virtual machine, it's not really ideal for serious workloads.  That said, everything presented here (except for scalable networking) has been prototyped in KVM and VMWare Player, so it can be done.  Perhaps later I will make some virtual discs available for experimenting.

You will need a client system of some kind.  This could be FreeBSD, Windows, Solaris or Linux.  Because we're mucking around at a low level, it might be best not to use your main system, at least at first.

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


