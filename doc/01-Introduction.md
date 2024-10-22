# Introduction

## What is iSCSI and why do I need it?

iSCSI is the "Internet Small Computer Systems Interface".

Historically, SCSI was a set of standards for connecting computers to a range of peripheral devices, but it was best known for connecting storage devices (disc, tape, etc) to computers.  In server-class systems it has been the defacto standard for storage control.

The physical interfaces have evolved since the standards were introduced in the early 1980's, but the key feature which set it apart from other interfaces was that it was a purely digital command/response interface.  This abstracted the storage platform in such a way that any vendor's peripheral could be connected to a controller with the expectation they would communicate successfully.  The layout of a disk was no longer important as the SCSI commands were based on storage blocks.

With suitable software layers, multiple hosts can share access to storage devices on the SCSI buss.  Mechanisms for doing this are complex, and are not for the feint-hearted.  In the majority of installations we ended up with a single host and multiple peripherals on a single buss, but this could become a limitation, especially if high-availability was required.

One of the challenges however was the physical connection.  This has been well documented elsewhere so I won't repeat the information.  IBM and Cisco jointly developed the iSCSI specification as a way of making the connection between host and peripheral much more universal, albeit initially at a lower performance level.  All that is required for an iSCSI connection is network capable of delivering TCP/IP frames.

iSCSI abstracts the peripheral layer even further, as the host system no longer connects to the actual device, but to a software interface which presents (usually) storage devices as targets, regardless of how the blocks are actually being stored.  An iSCSI target system might present a physical disc as a target to the host, or perhaps a file on a disk is used as a virtual disc device.  The host system treats either in the same manner.

Just as SCSI had "Hosts" and "Targets", iSCSI uses "Initiators" and "Targets".  The term "Target" often has two meanings in the iSCSI world:

1. The software which manages connections as well as the storage objects presented back to the Initiator.
2. The storage object presented to the Initiator.

We will use the terms interchangably in these documents.  Your indulgence is appreciated.

### So why would I want to use it?

Let's say you have a number of systems hosting virtual machines, using KVM or VMWare.  In order to be able to migrate VM's between hosts, a shared, reliable storage layer is required, and iSCSI can provide at least the shared part of this solution.  Later on, we will see how to make it highly reliable.

## Why did you build it on FreeBSD?

Sure, there are lots of choices for a free (of charge) operating system, so why choose FreeBSD over one of the popular Linux suites?  Firstly, I have a personal preference towards FreeBSD, and one of it's strengths is that there aren't a variety of distributions ("distros") out there.  There is FreeBSD, maintained by the FreeBSD Foundation.

Secondly, it's very robust, and has underpinned a lot of open source and commercial applications.  If you've used a Citrix NetScaler, Nintendo Switch or Playstation 3 or later, you're using FreeBSD.  Cisco use it as the basis of their NXOS platform as is NetApp's OnTAP, EMC's Isilon.  WhatsApp, FlightAware and parts of Netflix all run on top of FreeBSD as well.

So if it's good enough for them, it'll do fine for our needs.

## What are we going to build?

By the end of this, you will be able to deliver a working iSCSI storage system, capable of supporting multiple hosts; with a reliable, fault-tolerant storage system with features including, but not limited to high-availability, de-duplication, snapshots and even replication.  What's more is that no specialised hardware is required to make it happen.  Chances are you have most of what you need already.

