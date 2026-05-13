# Challenge: Photon Lockdown (Hardware)

## Solution

1. Identify the file type:
   ```sh
   file rootfs
   # rootfs: Squashfs filesystem, little endian, version 4.0, zlib compressed, ...
   ```
2. Mount the squashfs image:
   ```sh
   sudo mount -o loop=/dev/loop1 rootfs /mnt/squashfs
   ```
3. Search for the flag:
   ```sh
   grep -ri "HTB" /mnt/squashfs
   ```
