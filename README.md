snapraid-btrfs-subvol
========

**NOT ADEQUATELY TESTED**  
Please use for evaluation purposes only.

This fork avoids the following warning when a btrfs subvolume is set to `data` .

```
WARNING! UUID is unsupported for disks: 'd1', 'd2'. Not using inodes to detect move operations.
```

## Dependency

`libuuid.so` and `uuid/uuid.h` are required.

debian: `apt install uuid-dev`  
RHEL: `dnf install libuuid-devel`

## How it work

Executing `state` on a btrfs subvolume (directory) returns a device number that does not physically exist.  
The original SnapRaid looks for the device number in `/proc/self/mountinfo` to get the UUID of the disk, but it does not exist.  
Detail: https://lwn.net/Articles/866582/

This fork attempts to get the UUID of a btrfs subvolume when the UUID cannot be getted by the above method.

## Limitation

Only support Linux.  
At least the following subcommands are still unavailable.

* down
* devices 
* smart

SnapRAID
========

SnapRAID is a backup program for disk arrays. It stores parity
information of your data and it recovers from up to six disk
failures.

SnapRAID is mainly targeted for a home media center, where you
have a lot of big files that rarely change.

Beside the ability to recover from disk failures, the other
features of SnapRAID are:

* You can use disk already filled with files, without the need to
  reformat them. You will access them like now.
* All your data is hashed to ensure data integrity and to avoid
  silent corruption.
* If the failed disks are too many to allow a recovery,
  you lose the data only on the failed disks.
  All the data in the other disks is safe.
* If you accidentally delete some files in a disk, you can
  recover them.
* The disks can have different sizes.
* You can add disks at any time.
* It doesn't lock-in your data. You can stop using SnapRAID at any
  time without the need to reformat or move data.
* To access a file, only a single disk needs to spin, saving power and
  producing less noise.

The official site of SnapRAID is:

    http://www.snapraid.it/

