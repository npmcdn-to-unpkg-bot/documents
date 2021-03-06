File System btrfs
=================
https://btrfs.wiki.kernel.org/index.php/Main_Page

sudo apt-get install btrfs-tools


Create btrfs filesystem
-----------------------
::

    # Create the btrfs filesystem
    mkfs.btrfs -L label /dev/sdc2 
    mount /dev/sdc2 /mnt

    # Show information
    btrfs filesystem show


Modify the btrfs filesystem
---------------------------
::

    # Add/Delete
    btrfs device add /dev/sdc3 /mnt #Don't need mkfs firtly.
    btrfs device delete /dev/sdc3 /mnt
    
    # Resize btrfs filesystem online
    btffs filesystem resize 4G /mnt
    btffs filesystem resize +1G /mnt
    btffs filesystem resize -1G /mnt


Snapshot and Rollback
---------------------
::

    # Create snapshot
    btrfs subvolume snapshot /mnt /mnt/snap1

    # Delete snapshot
    btrfs subvolume delete /mnt/snap1

    # Rollback
    btrfs subvolume list
    btrfs subvolume set-default <id> <path>
    umount /mnt && mount /dev/sdc2 /mnt || reboot
    
