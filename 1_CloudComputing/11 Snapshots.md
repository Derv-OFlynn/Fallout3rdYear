Snapshots (or Checkpoints) is like capturing an image of your virtual machine at a moment in time

Easier when machine is powered off, like downloading a file.

A transaction in a database is not complete until all components of the transaction have been completed.

Snapshots often need to be taken of production machines that cannot be brought down, this is complicated

Useful when you need to perform a complicated upgrade to an application in a VM and want a quick way to roll back the changes if something goes wrong.

PowerPoint and word docs compile down to XML. Microsoft chose XML because it is extensible, promoting forward and backward compatibility.

A mark-up language is a language with annotations.

<mark style="background: #BABD00;">Do not ever use snapshots in place of backups!</mark>

### <mark style="background: #BABD00;">Creating a Snapshot:</mark>

Two types of checkpoints:
- Production Checkpoints
- Standard Checkpoints

### <mark style="background: #BABD00;">Introduction:</mark>

<mark style="background: #BABD00;">Scenario:</mark>  
- Need to perform a complicated upgrade to an application in a VM and want a quick way to roll back the changes if something goes wrong.  
- The company is building a demo or class lab and a quick way is needed to reset the virtual machines to their starting point.  
- You are testing software and need to repeat a set of tests very quickly without re-deploying virtual machines.

### <mark style="background: #BABD00;">Why Snapshots?</mark>

Keep multiple captures of a single virtual machine  
over time  

Could snapshot a virtual machine with just the operating system, service pack, and patches.  

Then create a second snapshot with SQL Server, service pack, and update rollup.  

Then a third snapshot with an application installed in the virtual machine.  

Can roll back the virtual machine (by applying a snapshot) to any of these 3 points in time to redo an install for the purposes of demo, testing, documentation, or training.  

A hierarchy of snapshots will be created for you

### <mark style="background: #BABD00;">Creating a Snapshot:</mark>

Two types of checkpoints  

<mark style="background: #BABD00;">Production Checkpoints:</mark>  
- Use backup technology in the Guest OS to create data-consistent checkpoints that do not include information about running applications.  
- uses Volume Shadow Copy Service or File System Freeze on a Linux virtual machine to create a data-consistent backup of the virtual machine. No snapshot of the virtual machine memory state is taken.  

<mark style="background: #BABD00;">Standard Checkpoints:</mark>
- Creates application-consistent checkpoints that capture the current state of the applications.  
- Takes a snapshot of the virtual machine and virtual machine memory state at the time the checkpoint is initiated.  
- A snapshot is not a full backup and can cause data consistency issues with systems that replicate data between different nodes such as Active Directory.  
- Hyper-V only offered standard checkpoints (formerly called snapshots) prior to Windows 10.

### <mark style="background: #BABD00;">Volume Shadow Copy Service (VSS):</mark>

Backing up and restoring critical business data can be very complex  

The data usually needs to be backed up while the applications that produce the data are still running. This means that some of the data files might be open or they might be in an inconsistent state  

If the data set is large, it can be difficult to back up all of it at one time  

Correctly performing backup and restore operations requires close coordination between  
- between the backup applications,  
- and the line-of-business applications that are being backed up,  
- and the storage management hardware and software.

Volume Shadow Copy Service (VSS) facilitates the  
conversation between these components to allow them to work better together.  

When all the components support VSS, you can use them to back up your application data without taking the applications offline.  

VSS coordinates the actions that are required to create a consistent shadow copy (also known as a snapshot or a point-in-time copy) of the data that is to be backed up.

The shadow copy can be used as-is, or it can be used in scenarios such as the following  
- You want to back up application data and system state information, including archiving data to another hard disk drive, to tape, or to other removable media.  
- You're data mining.  
- You're performing disk-to-disk backups.  
- You need a fast recovery from data loss by restoring data to the original Logical Unit Number (LUN) or to an entirely new LUN that replaces an original LUN that failed

### <mark style="background: #BABD00;">How are snapshots stored?</mark>

When you take a snapshot of a running VM, Hyper-V briefly pauses the VM to create a new automatic virtual hard disk (AVHD) which is <mark style="background: #BABD00;">essentially a differencing disk</mark>, attaches it to the VM to store changes to the VM data, saves the processor state into a file (.bin), then resumes the  
VM.  

Hyper-V also makes a copy of the VM configuration file, and saves the contents of the VM memory and processor state.  

Snapshots can also be created when a VM is turned-off, in which case Hyper-V does not need to capture VM memory or processor state data.

Snapshot data files are stored as .avhd files (with Hyper-V).  

Taking multiple snapshots can quickly consume storage space!  

Files usually are located in the same folder (or a sub folder) as the virtual hard disk.  

Do not delete .avhd files directly from the storage location. Instead, use Hyper-V Manager to select the virtual machine, and then delete the snapshots from the snapshot tree.

### <mark style="background: #BABD00;">Virtual Disk File Formats:</mark>

<mark style="background: #BABD00;">VMDK:</mark> An open format developed by VMWare.  Most common format (used by Oracle VirtualBox)

<mark style="background: #BABD00;">VHD:</mark> A native format from Microsoft (Hyper-V and Microsoft Virtual PC)

<mark style="background: #BABD00;">VHDX:</mark> Next Generation VHD.
- VHDX has 64TB disk limit; VHD has 2TB disk limit.  
- VHDX supports large block sizes (sometimes better performance)  
- VHDX protects against file corruption, VHD does not.  
- Two way conversion between VHD and VHDX is possible.  
- VHDX works in Windows Server 2012 and later (not earlier).  
- VHDX is supported in Microsoft Azure (as of 2021).

<mark style="background: #BABD00;">AVHD:</mark> A VHD differencing disk.  

<mark style="background: #BABD00;">AVHDX:</mark> A VHDX differencing disk.

<mark style="background: #BABD00;">OVF:</mark>  
- The OVF Specification provides a means of describing the properties of a virtual system.  
- It is an XML based format.  
- It supports extendibility.  
- An OVF file is used to describe a single virtual machine or single virtual appliance.  

<mark style="background: #BABD00;">OVA:</mark> An OVA file is an OVF file packaged together with all of its supporting files (disk images, metadata, etc).

![](https://i.imgur.com/VUWGvD2.png)

### <mark style="background: #BABD00;">Snapshot considerations:</mark>

Taking a snapshot (also known as checkpoint) reduces the performance of the virtual machine while the snapshot is created. You should not use these snapshots on virtual machines that provide  
services in a production environment.  
[Microsoft Learning Link](https://learn.microsoft.com/en-us/windows-server/virtualization/hyper-v/best-practices-analyzer/avoid-using-checkpoints-on-a-virtual-machine-server-workload-production)  

MS do not recommend using snapshots on virtual machines that are configured with fixed virtual hard disks because they reduce the performance benefits that are otherwise gained by using fixed virtual hard disks. (Why?)

[Link 1 - Winsows 2012](https://learn.microsoft.com/en-us/previous-versions/windows/it-pro/windows-server-2012-r2-and-2012/dn818483(v=ws.11) "https://learn.microsoft.com/en-us/previous-versions/windows/it-pro/windows-server-2012-r2-and-2012/dn818483(v=ws.11)")

[Link2 - Fixed vs dynamic disks](https://learn.microsoft.com/en-us/answers/questions/560255/fixed-vs-dynamic-disks "https://learn.microsoft.com/en-us/answers/questions/560255/fixed-vs-dynamic-disks")

[Azure managed disks overview](https://learn.microsoft.com/en-us/azure/virtual-machines/managed-disks-overview "https://learn.microsoft.com/en-us/azure/virtual-machines/managed-disks-overview")

[hyper v guest design fixed vs dynamic vhd](https://www.altaro.com/hyper-v/hyper-v-guest-design-fixed-vs-dynamic-vhd/ "https://www.altaro.com/hyper-v/hyper-v-guest-design-fixed-vs-dynamic-vhd/")

Presence of a VM snapshot reduces the disk performance of the virtual machine. Creating more snapshots will increase that degradation. Hyper-V snapshots should not to be used as a VM backup.  

Taking multiple snapshots can quickly consume a large amount of storage space. When you use Hyper-V Manager to delete a snapshot, the snapshot is removed from the snapshot tree but the ``.avhd`` file is not deleted until you turn off the virtual machine.

### <mark style="background: #BABD00;">Automatic Virtual Hard Disk:</mark>

Each virtual hard disk of the virtual machine is also treated by the snapshot. This is done using a special kind of differential virtual hard disk called the <mark style="background: #BABD00;">Automatic Virtual Hard Disk (AVHD)</mark>:

![](https://i.imgur.com/bHrMMLM.png)

A differencing disk is the disk created the moment you begin a snapshot.

Each <mark style="background: #BABD00;">VHD</mark> file will become a parent to an AVHD file. The virtual machine will start using the AVHD file for reads and writes after the snapshot, and the VHD file for reads older than the snapshot.  

Each <mark style="background: #BABD00;">VHDX</mark> file will become a parent to an AVHDX file. The virtual machine will start using the AVHDX file for reads and writes after the snapshot, and the VHDX file for reads older than the snapshot.  

With each new snapshot that is taken, the active AVHD is detached from the VM, and becomes the parent of a new child AVHD that is attached to the VM and captures changes to the VM data until the next snapshot is  created. Note: Hierarchy!

### <mark style="background: #BABD00;">Reverting/Applying Snapshots:</mark>

Revert feature can be thought of as a single-level undo feature! Previous snapshot state.  

During the Revert process, the VM is stopped, the current AVHD is deleted, and a new AVHD is created. (new ‘fork’ for progress)  

When a Revert is performed, all configuration modifications made to the running VM since the snapshot was taken are discarded.  

Apply option may be used to return to a snapshot that is higher than one level up from the running VM. Fully flexible.

### <mark style="background: #BABD00;">Deleting Snapshots:</mark>

Deleting a single snapshot will not affect other snapshots (at the same level), but it will immediately delete the configuration file and save state files associated with the snapshot. 

<mark style="background: #BABD00;">NB:</mark> In a snapshot hierarchy, the snapshot AVHD may be related to other snapshot AVHDs through a parent-child relationship. A snapshot AVHD is only immediately deleted if it is not the parent of a child AVHD.  

If there is only one child AVHD, it is merged into the parent AVHD the next time that the VM is powered-off.

Deleting a snapshot subtree immediately deletes the configuration and save state files associated with all the snapshots in the subtree. If the running virtual machine AVHD is not a child of any snapshot in the subtree, then all of the AVHDs in the subtree will also be deleted.  

(If the running virtual machine AVHD depends on a chain of AVHDs in the subtree that is deleted, then the AVHD chain will be merged into the AVHD that is one level above the deleted subtree, the next time that the VM is powered-off.)

### <mark style="background: #BABD00;">Common snapshot mistakes:</mark>

There are several mistakes that one can make with snapshots:  

<mark style="background: #BABD00;">Swap the parent VHD/X files:</mark> There is a link between the AVHD/X and the VHD/X file. Do not attempt to break and recreate this link.  

<mark style="background: #BABD00;">Delete the VHD/X files:</mark> Data older than the snapshot, such as the guest operating system, are stored in the parent disks. Do not delete the virtual hard disks.  

<mark style="background: #BABD00;">Delete the AVHD/X files:</mark> Doing this will delete all the data of the virtual machine since the snapshot was created. Do not do this.  

<mark style="background: #BABD00;">Leave a snapshot in place for a long time:</mark> Differential disks, and therefore AVHD/X files, are intended for short-term usage. Performance will degrade as the files will continue to grow over time.

### <mark style="background: #BABD00;">Archival Backups?</mark>

Export the virtual machine.  

Takes some time, but you can make an importable copy of many virtual machines at once by using the Hyper-V Manager. What you end up with is a set of files that can be copied to a new location and easily imported.  

Use PowerShell and it’s support of WMI to administer Hyper-V. So, a script could automate:  
- Shutting down the virtual machine  
- Exporting the virtual machine and/or Copy the .VHD files  
- Starting the virtual machine  

Or treat it as if it were a physical server – complete with backup agents installed into it, and using some enterprise class backup and archiving solution. It all depends upon the purpose of the server, the business applications and/or data housed therein, the ease with which you want to be able to recreate the server, etc. Altaro, VEEAM, etc.