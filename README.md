This file is for me to document things for final year project

#wiping clean sata disk:

#On linux
1. use sgdiks(gdisk) if dont have then install im on fedora so its <sudo dnf install gdisk>
2. once drive is connected to your device i.e. laptop or desktop use cli to find the disk : lsblk:

❯ lsblk
NAME        MAJ:MIN RM   SIZE RO TYPE MOUNTPOINTS
sda           8:0    0 447.1G  0 disk
├─sda1        8:1    0   499M  0 part
├─sda2        8:2    0   128M  0 part
├─sda3        8:3    0 442.1G  0 part
└─sda4        8:4    0   4.5G  0 part
zram0       251:0    0     8G  0 disk [SWAP]
nvme0n1     259:0    0 953.9G  0 disk
├─nvme0n1p1 259:1    0   600M  0 part /boot/efi
├─nvme0n1p2 259:2    0     2G  0 part /boot
└─nvme0n1p3 259:3    0 951.3G  0 part /home
                                      /

the sda is the sata disk and the sda1 to sda4 are the partition of the disk that we need to wipe

3. use sgdiks to clean wipe clean the disk <sudo sgdisk --zap-all /dev/sda>
4. then wipe remianing metadata <sudo wipefs -a /dev/sda>
5. verify the disk once again using lsblk , you will see that the sda files become one line that means its succesful:

❯ lsblk
NAME        MAJ:MIN RM   SIZE RO TYPE MOUNTPOINTS
sda           8:0    0 447.1G  0 disk
zram0       251:0    0     8G  0 disk [SWAP]
nvme0n1     259:0    0 953.9G  0 disk
├─nvme0n1p1 259:1    0   600M  0 part /boot/efi
├─nvme0n1p2 259:2    0     2G  0 part /boot
└─nvme0n1p3 259:3    0 951.3G  0 part /home
                                      /

#on windows

1. on windows we can use a tool call diskpart , this tool is built in into windows machines
2. to use it run cmd as administrator 
3. enter diskpart in cli to initilaize it 
4. list the disk present -> list disk
5. select the disk needed to be wiped -> select disk <number>
6. once selected just enter -> clean all 
7. the process will start and once the disk is done cleaning it will say so

