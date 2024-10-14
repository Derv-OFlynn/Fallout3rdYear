Snapshots (or Checkpoints) is like capturing an image of your virtual machine at a moment in time

Easier when machine is powered off, like downloading a file.

A transaction in a database is not complete until all components of the transaction have been completed.

Snapshots often need to be taken of production machines that cannot be brought down, this is complicated

Useful when you need to perform a complicated upgrade to an application in a VM and want a quick way to roll back the changes if something goes wrong.

<mark style="background: #BABD00;">Do not ever use snapshots in place of backups!</mark>

### <mark style="background: #BABD00;">Creating a Snapshot:</mark>

Two types of checkpoints:
- Production Checkpoints
- Standard Checkpoints