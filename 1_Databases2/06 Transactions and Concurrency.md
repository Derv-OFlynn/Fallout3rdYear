### <mark style="background: #69E772;">Introduction to Transaction Processing:</mark>

<mark style="background: #69E772;">Single-User System:</mark> At most one user at a time can use the system. 
<mark style="background: #69E772;">Multi-user System:</mark> Many users can access the system concurrently.

<mark style="background: #69E772;">Concurrency:</mark>
- <mark style="background: #69E772;">Interleaved processing:</mark> concurrent execution of processes is interleaved in a single CPU
- <mark style="background: #69E772;">Parallel processing:</mark> processes are concurrently executed in multiple CPUs. 

### <mark style="background: #69E772;">Transactions:</mark>

A transaction (or logical unit of work) is a sequence of SQL statements that postgreSQL treats as a single unit.
 
<mark style="background: #69E772;">A transaction ends with a</mark> 
- commit, 
- rollback , 
- any DDL statement which issues an implicit commit. 

### <mark style="background: #69E772;">More on Transaction Processing:</mark>

A <mark style="background: #69E772;">Transaction</mark> includes one or more access operations (read -retrieval, write - insert or update, delete).

A <mark style="background: #69E772;">transaction (set of operations)</mark> may be stand-alone specified in a high level language like SQL submitted interactively, or may be embedded within a program.

<mark style="background: #69E772;">Transaction boundaries:</mark> Begin and End transaction.

An <mark style="background: #69E772;">application program</mark> may contain several transactions  separated by the Begin and End transaction boundaries. 

<mark style="background: #69E772;">SIMPLE MODEL OF A DATABASE (for purposes of discussing transactions):</mark>

<mark style="background: #69E772;">A database</mark> - collection of named data items

<mark style="background: #69E772;">Granularity of data</mark> - a field, a record , or a whole disk block (Concepts are independent of granularity)

<mark style="background: #69E772;">Basic operations are read and write</mark>
- <mark style="background: #69E772;">read_item(X):</mark> Reads a database item named X into a program variable. To simplify our notation, we assume that the program variable is also named X.
- <mark style="background: #69E772;">write_item(X):</mark> Writes the value of program variable X into the database item named X.

### <mark style="background: #69E772;">Two sample transactions T1 and T2:</mark>

![](https://i.imgur.com/0JXmWkI.png)


### <mark style="background: #69E772;">Why Concurrency Control is needed:</mark>

<mark style="background: #69E772;">The Lost Update Problem:</mark> This occurs when two transactions that access the same database items have their operations interleaved in a way that makes the value of some database item incorrect. 

<mark style="background: #69E772;">The Temporary Update (or Dirty Read) Problem:</mark> This occurs when one transaction updates a database item and then the transaction fails for some reason. The updated item is accessed by another transaction before it is changed back to its original value. 

<mark style="background: #69E772;">The Incorrect Summary Problem:</mark> If one transaction is calculating an aggregate summary function on a number of records while other transactions are updating some of these records, the aggregate function may calculate some values before they are updated and others after they are updated. 

### <mark style="background: #69E772;">Lost Update problem:</mark>

# <mark style="background: #FF5582A6;">SLIDE 9</mark>

### <mark style="background: #69E772;">The temporary update problem:</mark>

# <mark style="background: #FF5582A6;">SLIDE 10</mark>

### <mark style="background: #69E772;">The incorrect summary problem:</mark>
# <mark style="background: #FF5582A6;">SLIDE 11</mark>


### <mark style="background: #69E772;">Concurrency Control:</mark>

<mark style="background: #69E772;">Properties of a transaction:</mark>
- ATOMICITY
- CONSISTENCY
- ISOLATION
- DURABILITY

# <mark style="background: #FF5582A6;">SLIDE 12</mark>

### <mark style="background: #69E772;">A.C.I.D. properties:</mark>

<mark style="background: #69E772;">Atomicity:</mark> the is the “all or nothing” property ; a transaction is an indivisible unit of work

<mark style="background: #69E772;">Consistency:</mark> transactions transform the DB from one consistent state to another consistent state

<mark style="background: #69E772;">Isolation:</mark> transactions execute in isolation i.e. the partial effect of one transaction is not visible to other transactions.

<mark style="background: #69E772;">Durability (aka Persistence):</mark> the effect of a successfully completed (i.e. committed) transaction are permanently recorded in the DB and cannot be undone. 

### <mark style="background: #69E772;">Transactions Manager:</mark>

The transaction manager enforces the ACID properties 
- It schedules the operations of transactions • COMMIT and ROLLBACK are used to ensure atomicity 
- Locks or timestamps are used to ensure consistency and isolation for concurrent transactions 
- A log is kept to ensure durability in the event of system failure and make the system recoverable

### <mark style="background: #69E772;">Transaction and System Concepts:</mark>

A <mark style="background: #69E772;">transaction</mark> is an atomic unit of work that is either completed in its entirety or not done at all. For recovery purposes, the system needs to keep track of when the transaction starts, terminates, and commits or aborts.

<mark style="background: #69E772;">Transaction states:</mark>
- Active state
- Partially committed state
- Committed state
- Failed state
- Terminated State 

### <mark style="background: #69E772;">State diagram illustrating the states for transaction execution.</mark>

# <mark style="background: #FF5582A6;">SLIDE 17</mark>

### <mark style="background: #69E772;">Making changes persist:</mark>

When data is changed, it must be persisted, to ensure that the change takes.

<mark style="background: #69E772;">E.g. a text editor:</mark>
- SAVE will COMMIT your changes.
- QUIT will ROLLBACK your changes.

<mark style="background: #69E772;">AUTOCOMMIT:</mark>
- When this feature is ON, changes are persisted as soon as they happen.
- Similar to Google Docs.

### <mark style="background: #69E772;">The transaction control commands:</mark>

<mark style="background: #69E772;">commit</mark> makes all changes since the beginning of a transaction permanent 

<mark style="background: #69E772;">rollback</mark> rolls back (undoes) all changes since the beginning of a transaction.

<mark style="background: #69E772;">Other users:</mark> 
- cannot see the results of the transaction until it has been committed.
- Can see the data as it was before the other user's transaction started!

### <mark style="background: #69E772;">AUTOCOMMIT, COMMIT and ROLLBACK:</mark>

Many modern database clients set autocommit on by default.

![](https://i.imgur.com/ufIuzwk.png)

### <mark style="background: #69E772;">Implicit and explicit transactions:</mark>

<mark style="background: #69E772;">In autocommit mode:</mark>
- Every SQL statement is considered to be a transaction
- It has an implicit BEGIN before it.
- It has an implicit COMMIT after it.

![](https://i.imgur.com/Fgzm0n8.png)

### <mark style="background: #69E772;">Why recovery is needed:</mark> 

(What causes a Transaction to fail)
1. <mark style="background: #69E772;">A computer failure (system crash):</mark> A hardware or  software error occurs in the computer system during transaction execution. If the hardware crashes, the contents of the computer’s internal memory may be lost.
2. <mark style="background: #69E772;">A transaction or system error:</mark> Some operation in the transaction may cause it to fail, such as integer overflow or division by zero. Transaction failure may also occur because of erroneous parameter values or because of a logical programming error. In addition, the user may interrupt the transaction during its execution.
3. <mark style="background: #69E772;">Local errors or exception conditions</mark> detected by the transaction: 
	- certain conditions necessitate cancellation of the transaction. For example, data for the transaction may not be found. A condition, such as insufficient account balance in a banking database, may cause a transaction, such as a fund withdrawal from that account, to be cancelled. 
	- a programmed abort in the transaction causes it to fail.
4. <mark style="background: #69E772;">Concurrency control enforcement:</mark> The concurrency control method may decide to abort the transaction, to be restarted later, because it violates serializability or because several transactions are in a state of deadlock
5. <mark style="background: #69E772;">Disk failure:</mark> Some disk blocks may lose their data because of a read or write malfunction or because of a disk read/write head crash. This may happen during a read or a write operation of the transaction. 
6. <mark style="background: #69E772;">Physical problems and catastrophes:</mark> This refers to an endless list of problems that includes power or air-conditioning failure, fire, theft, sabotage, overwriting disks or tapes by mistake, and mounting of a wrong tape by the operator. 

<mark style="background: #69E772;">Recovery techniques use the following operators:</mark>
- <mark style="background: #69E772;">undo:</mark> Similar to rollback except that it applies to a single operation rather than to a whole transaction.
- <mark style="background: #69E772;">redo:</mark> This specifies that certain <mark style="background: #69E772;">transaction operations</mark> must be <mark style="background: #69E772;">redone</mark> to ensure that all the operations of a committed transaction have been applied successfully to the database. 

### <mark style="background: #69E772;">The System Log:</mark>

<mark style="background: #69E772;">Log or Journal:</mark> The log keeps track of all transaction operations that affect the values of database items. This information may be needed to permit recovery from transaction failures. The log is kept on disk, so it is not affected by any type of failure except for disk or catastrophic failure. In addition, the log is periodically backed up to archival storage (tape) to guard against such catastrophic failures.  

T in the following discussion refers to a unique <mark style="background: #69E772;">transaction-id</mark> that is generated automatically by the system and is used to identify each transaction: 

<mark style="background: #69E772;">Types of log record:</mark> 
- ``[start_transaction,T]:`` Records that transaction T has started execution.
- ``[write_item,T,X,old_value,new_value]:`` Records that transaction T has changed the value of database item X from old_value to new_value.
- ``[read_item,T,X]:`` Records that transaction T  has read the value of database item X.
- ``[commit,T]:`` Records that transaction T has completed successfully, and affirms that its effect can be committed (recorded permanently) to the database.
- ``[abort,T]:`` Records that transaction T has been aborted. 

### <mark style="background: #69E772;">Recovery using log records:</mark>

If the system crashes, we can recover to a consistent database state by examining the log

Because the log contains a record of every write operation that changes the value of some database item, it is possible to <mark style="background: #69E772;">undo</mark> the effect of these write operations of a transaction T by tracing backward through the log and resetting all items changed by a write operation of T to their ``old_values``.

We can also <mark style="background: #69E772;">redo</mark> the effect of the write operations of a transaction T by tracing forward through the log and setting all items changed by a write operation of T (that did not get done permanently) to their ``new_values``.   

### <mark style="background: #69E772;">Logs: the Transaction Schedule:</mark>

<mark style="background: #69E772;">Transaction schedule:</mark> When transactions are executing concurrently in an interleaved fashion, the order of execution of operations from the various transactions forms a transaction schedule. 

A <mark style="background: #69E772;">schedule</mark> (or <mark style="background: #69E772;">history</mark>) S of n transactions T1, T2, ..., Tn: It is an ordering of the operations of the transactions subject to the constraint that, for each transaction Ti that participates in S, the operations of T1 in S must appear in the same order in which they occur in T1. Note, however, that operations from other transactions Tj can be interleaved with the operations of Ti in S. 

Two operations are <mark style="background: #69E772;">conflicting</mark> if the belongs to 2 active transactions and at least one of the 2 is a write and they use the same data item

![](https://i.imgur.com/iYAteB5.png)

### <mark style="background: #69E772;">Characterising Schedules based on recoverability:</mark>


<mark style="background: #69E772;">Recoverable schedule:</mark> One where no transaction needs to be rolled back. 
 
 A schedule S is <mark style="background: #69E772;">recoverable</mark> if no transaction T in S commits until all transactions T’ that have written an item that T reads have committed. Still cascading rollback of uncommitted transactions possible!

<mark style="background: #69E772;">Cascadeless schedule:</mark> One where every transaction reads only  the items that are written by committed transactions.

<mark style="background: #69E772;">Schedules requiring cascaded rollback:</mark> A schedule in which uncommitted transactions that read an item from a failed transaction must be rolled back. 

<mark style="background: #69E772;">Strict Schedules:</mark> A schedule in which a transaction can neither read or write an item X until the last transaction that wrote X has committed. 

<mark style="background: #69E772;">Serial schedule:</mark> A schedule S is <mark style="background: #69E772;">serial</mark> if, for every transaction T participating in the schedule, all the operations of T are executed consecutively in the schedule. Otherwise, the schedule is called non-serial schedule.

<mark style="background: #69E772;">Serialisable schedule:</mark> A schedule S is <mark style="background: #69E772;">serialisable</mark> if it is equivalent to some serial schedule of the same n transactions

 
Being serialisable implies that the schedule is a correct schedule.
- It will leave the database in a consistent state. 
- The interleaving is appropriate and will result in a state as if the transactions were serially executed, yet will achieve efficiency due to concurrent execution. 

Being serialisable is not the same as being serial

<mark style="background: #69E772;">conflict – serialisable:</mark> A schedule is conflict – serializable if by swapping non conflicting operations a serial schedule can be obtained

### <mark style="background: #69E772;">Schedule examples:</mark>

![](https://i.imgur.com/nh5kQ4p.png)


### <mark style="background: #69E772;">Database Concurrency Control:</mark>

<mark style="background: #69E772;">Why Concurrency Control is needed:</mark>
- The Lost Update Problem. 
- The Temporary Update (or Dirty Read) Problem. 
- The Incorrect Summary Problem . 

<mark style="background: #69E772;">Purpose of Concurrency Control:</mark>
- To enforce Isolation (through mutual exclusion) among conflicting transactions. 
- To preserve database consistency through consistency preserving execution of transactions.
- To resolve read-write and write-write conflicts.

<mark style="background: #69E772;">Example:</mark>  In concurrent execution environment if T1 conflicts with T2 over a data item A, then the existing concurrency control decides if T1 or T2 should get the A and if the other transaction should wait.  

### <mark style="background: #69E772;">Concurrency control is based on locks:</mark>

<mark style="background: #69E772;">Locking:</mark> 
- allows a user to take hold of a block for updating.
- Prevents other users from modifying the same data. 
- Locks can create performance problems.
- When one process locks, others are shut out. 
- There are several levels of locking.

<mark style="background: #69E772;">When modifying:</mark> 
- The transaction should place a lock until committed or rolled back. 
- This is known as data concurrency.

### <mark style="background: #69E772;">Transactions and Locking:</mark>

<mark style="background: #69E772;">Transactions start with BEGIN</mark>
- When an ``INSERT``, ``UPDATE`` or ``DELETE``  takes place:
- It locks the row that is being ``INSERTed`` / ``UPDATEd`` / ``DELETEd``. Other sessions cannot see the changes that are being made.

The lock holds until the transaction session is finished by issuing 
- COMMIT or
- ROLLBACK

### <mark style="background: #69E772;">Exclusive locks:</mark>

<mark style="background: #69E772;">Exclusive locks occur on ROWS when:</mark>
- The row is ``INSERTed``
- The row is ``DELETEd``
- The row is ``UPDATEd``
- The row is ``SELECTed``... FOR UPDATE...

### <mark style="background: #69E772;">Locking rows:</mark>

![](https://i.imgur.com/YITpjM5.png)


### <mark style="background: #69E772;">Locking Techniques: Binary Locking Scheme</mark>

A binary lock can have two states or values: locked (1) or unlocked (0)

If the value of the lock on item X is 1, item X cannot be accessed by a database operation that requests X.

If the value of the lock on item X is 0, item X can be accessed when requested.

The current value of the lock on item X is referred to as LOCK(X).

Binary locks are kept in a lock table which contains records where each record contains three fields:

``<DB Item, LOCK, Locking Transaction>``

Only items that are locked are kept in the table. Items that are not in the table are considered to be unlocked.

<mark style="background: #69E772;">The following code performs the lock operation:</mark>
```
lock-item(X):
B:	if LOCK (X) = 0 (*item is unlocked*)
	then LOCK (X)  1 (*lock the item*)
	else begin
		wait (until lock (X) = 0 and the lock manager 		wakes up the transaction);
	goto B
	end;
```

<mark style="background: #69E772;">The following code performs the unlock operation:</mark>
```
unlock-item(X):
LOCK (X)  0 (*unlock the item*)
if any transactions are waiting then wake up one of the waiting the transactions;
```

### <mark style="background: #69E772;">Locking Techniques: Essential components</mark>

To use the binary locking scheme, every transaction must obey the following rules:
- A transaction T must issue the operation lock_item(X) before any read_item(X) or write_item(X) operations are performed in T.
- A transaction T must issue the operation unlock_item(X) after all read_item(X) or write_item(X) operations are completed in T.
- A transaction T will not issue a lock_item(X) operation if it already holds the lock on item X.
- A transaction T will not issue a unlock_item(X) unless it already holds the lock on item X.

### <mark style="background: #69E772;">Shared/Exclusive Locking Scheme:</mark>

<mark style="background: #69E772;">Two locks modes (a) shared (read) and (b) exclusive (write).</mark>
- <mark style="background: #69E772;">Shared mode:</mark> shared lock (X).  More than one transaction can apply shared lock on X for reading its value but no write lock can be applied on X by any other transaction.
- <mark style="background: #69E772;">Exclusive mode:</mark> Write lock (X).  Only one write lock on X can exist at any time and no shared lock can be applied by any other transaction on X.

``LOCK(X)`` has now 3 states: “``read_locked``”, “``write_locked``” or “``unlocked``”.

<mark style="background: #69E772;">Conflict matrix:</mark>
![](https://i.imgur.com/zX7YS7T.png)

Locking Techniques: Shared/Exclusive Lock Operations

<mark style="background: #69E772;">The following code performs the read lock operation:</mark>
```
read_lock(X):
	B: if LOCK (X) = “unlocked” then
begin LOCK (X)  “read-locked”;
	no_of_reads (X)  1;
end
else if LOCK (X)  “read-locked” then
	      no_of_reads (X)  no_of_reads (X) +1
	  else begin wait (until LOCK (X) = “unlocked” and
		   the lock manager wakes up the transaction);
		   go to B
end;
```

<mark style="background: #69E772;">The following code performs the write lock operation:</mark>
```
write_lock(X):
    B: if LOCK (X) = “unlocked” then
LOCK (X)  “write-locked”;
else  begin 
         wait (until LOCK (X) = “unlocked” and
		   the lock manager wakes up the transaction);
        go to B
end;
```

<mark style="background: #69E772;">The following code performs the unlock operation:</mark>
```
unlock(X):
	if LOCK (X) = “write-locked” then
begin LOCK (X)  “unlocked”;
	 wakeup one of the transactions, if any
end
else if LOCK (X)  “read-locked” then
	begin
	      no_of_reads (X)  no_of_reads (X) -1
	      if  no_of_reads (X) = 0 then 		  
	      begin
		 LOCK (X) = “unlocked”;
		wakeup one of the transactions, if any
	      end
	end;
```

### <mark style="background: #69E772;">Lock conversion:</mark>

<mark style="background: #69E772;">Lock upgrade: existing read lock to write lock</mark>
```
if Ti has a read-lock (X) and Tj has no read-lock (X) (i  j) then
	     convert read-lock (X) to write-lock (X)
    else
	    force Ti to wait until Tj unlocks X

```

<mark style="background: #69E772;">Lock downgrade: existing write lock to read lock</mark>
```
Ti has a write-lock (X)    (*no transaction can have any lock on X*)
	     convert write-lock (X) to read-lock (X)

```

![](https://i.imgur.com/4XkR0Ax.png)

![](https://i.imgur.com/SALmRZg.png)

### <mark style="background: #69E772;">Two-Phase Locking Techniques - The algorithm:</mark>

<mark style="background: #69E772;">Two Phases:  (a) Locking (Growing) (b) Unlocking (Shrinking).</mark>
- <mark style="background: #69E772;">Locking (Growing) Phase:</mark>  A transaction applies locks (read or write) on desired data items one at a time.
- <mark style="background: #69E772;">Unlocking (Shrinking) Phase:</mark> A transaction unlocks its locked data items one at a time.
- <mark style="background: #69E772;">Requirement:</mark> For a transaction these two phases must be mutually exclusively, that is, during locking phase unlocking phase must not start and during unlocking phase locking phase must not begin.

![](https://i.imgur.com/mqTwdGi.png)

### <mark style="background: #69E772;">Deadlock:</mark>

A deadlock can occur when two or more users are waiting for data locked by each other. 

Deadlocks prevent some transactions from continuing to work. 

The next example illustrates two transactions in a deadlock.

### <mark style="background: #69E772;">Dealing with Deadlock and Starvation:</mark>
![](https://i.imgur.com/2k66wP7.png)

### <mark style="background: #69E772;">A second Example:</mark>
![](https://i.imgur.com/VbWwxRt.png)

### <mark style="background: #69E772;">Example Explanation:</mark>

<mark style="background: #69E772;">At timepoint A:</mark>
- no problem exists as each transaction has a row lock on the row it attempts to update.
- Each transaction proceeds without being terminated.
- However, each tries next to update the row currently held by the other transaction. 

<mark style="background: #69E772;">At timepoint B:</mark>
- a deadlock results, because neither transaction can obtain the resource it needs to proceed or terminate. 
- It is a deadlock because no matter how long each transaction waits, the conflicting locks are held.

### <mark style="background: #69E772;">Deadlock Prevention:</mark>

A transaction locks all data items it refers to before it begins execution.  This way of locking prevents deadlock since a transaction never waits for a data item.  The conservative two-phase locking uses this approach.

Other deadlock prevention algorithms use the concept of a timestamp TS(T) which is a unique identifier assigned to transactions based on the order in which they start. If T1 starts before T2, then

TS(T1) < TS(T2) (older transaction has the smaller timestamp value)  

<mark style="background: #69E772;">Examples of such algorithms are:</mark>       
- <mark style="background: #69E772;">Wait-die:</mark> If TS(Ti) < TS(Tj), then (Ti is older than Tj) Ti is allowed to wait; otherwise (Ti younger than Tj) abort Ti (Ti dies) and restart it later with the same timestamp.
- <mark style="background: #69E772;">Wound-wait:</mark> If TS(Ti) < TS(Tj), then (Ti is older than Tj) abort Tj (Ti wounds Tj) and restart it later with the same timestamp; otherwise (Ti younger than Tj) Ti is allowed to wait.

### <mark style="background: #69E772;">Deadlock Detection and Resolution:</mark>

In this approach, deadlocks are allowed to happen. The scheduler maintains a wait-for-graph for detecting cycle. If a cycle exists, then one transaction involved in the cycle is selected (victim) and rolled-back.

Another approach to deal with deadlock is the use of timeouts. In this method, if a transaction waits for a period of time longer than a system-defined timeout period, the system assumes that a transaction maybe in s state of deadlock and aborts it regardless of whether a deadlock actually exists or not.

### <mark style="background: #69E772;">Starvation:</mark>

Starvation occurs when a particular transaction consistently waits or restarted and never gets a chance to proceed further. 

In a deadlock resolution it is possible that the same transaction may consistently be selected as victim and aborted. 

This limitation is inherent in all priority based scheduling mechanisms.  

In Wound-Wait scheme a younger transaction may always be wounded (aborted) by a long running older transaction which may create starvation.