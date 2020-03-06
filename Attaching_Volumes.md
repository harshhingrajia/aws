# Attaching a Volume to an Instance:

#### 1. List the volumes
  `lsblk`

#### 2. Check if the volume has any data
  `sudo file -s /dev/xvdf`

#### 3. Format the volume as ext4
  `sudo mkfs -t ext4 /dev/xvdf`
  
#### 4. Create a directory
  `mkdir /myexternalvolume`

#### 5. Mount our EBS to our directory
  `sudo mount /dev/xvdf /myexternalvolume`

#### 6. Go to directory and verify size and free space
    ```sh
    cd /myexternalvolume
    echo "hello" > hello.txt
    df -h 
    ```      

#### 7. To unmount
  `unmount /dev/xvdf`

#### 8. Backup fstab file
  `sudo cp /etc/fstab /etc/fstab.bak`

#### 9. Add an entry into our fstab file
  `cat /etc/fstab`
  
#### 10. Add this line: (/dev/xvdf     /myexternalvolume     ext4     defaults,notail     0    0)
  `sudo nano /etc/fstab`
  
#### 11. Reboot the system
  `sudo reboot -h`
  
#### 12. Verify for error after ssh it again
   `sudo mount -a`
  
-----------------------------------------------------------------------------------------------------

# Resizing the Volume:

#### 1. Use lsblk to check the disk size
   `lsblk`

#### 2. See how the system sees our drive
  `df -h`

#### 3. Resize the partition
   `sudo resize2fs /dev/xvdf`
