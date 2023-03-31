# Extended Setup guide - eMMC

## Adding Swap Partition

Swap partition is useful for OS performance because it offloads the RAM usage

### Check Swap Status

```bash
sudo swapon --show
```

If output is empty, then swap is disabled

### Allocate swap

```bash
sudo fallocate -l <swap_size>G /swapfile
```
If allocating 1 GB swap,

```bash
sudo fallocate -l 1G /swapfile
```

### Set up a Linux swap area on the file

```bash
sudo mkswap /swapfile
```

Because only the root user should have the right to write and read the swap file, you must set the permissions by using

```bash
sudo chmod 600 /swapfile
```

### Activate the swap file

```bash
sudo swapon /swapfile
```

### Verify active swap

```bash
sudo free -h
```

To make the changes permanent, write swap settings in /etc/fstab file

```
sudo nano /etc/fstab
```

Write this line:
```bash
/swapfile swap swap defaults 0 0
```
below this line:
```bash
tmpfs    /run   tmpfs  mode=0755,nodev,nosuid,strictatime  0  0
```

Then press `ctrl+x` and `y` to save the file

## Hybrid eMMC-SDCard

The eMMC has great speed in read/write capacity, but has less capacity than SDCard. You can use both spaces for system in order to maximize SBC capacity

### Short Explanation of Ubuntu Filesystem
Not all ubuntu filesystem is essential that's dangerous when edited. But there's two easily editable filesystem:

- `/home`: home directory, used for Downloads, Documents, Desktop, etc

- `/opt`: a directory where to install unbundled packages

### Check your SD Card name partition

```bash
lsblk
```

### Format the SD Card and mount

```bash
sudo mkfs -t ext4 /dev/mmcblk1p2

sudo mount /dev/mmcblk1p2 /mnt
```

### Transfer directory from eMMC to SD Card

```bash
sudo mv /opt /mnt && sudo mv /home /mnt
```

Make it permanent by editing /etc/fstab, edit the line like this

```bash
# uncomment this if your device has a SD/MMC/Transflash slot
/dev/mmcblk1p2 /mnt   auto defaults 0 0
/mnt/opt /opt   none bind 0 0
/mnt/home /home  none bind 0 0
```