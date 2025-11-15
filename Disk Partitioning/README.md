# Add a Disk & Create Standard Partition 

🎯 Objective
Attach a new virtual disk to the Linux system and create a standard partition
using `fdisk`. Format it, mount it, and make it persistent using `/etc/fstab`.

---

## 🧩 Steps Performed

### 1️⃣ Add New Disk
- Added a new virtual disk through Oracle VirtualBox.
- Verified detection of the disk using:

  - lsblk 
  - fdisk -l


### 2️⃣ Create a Partition
Used `fdisk`:

  fdisk /dev/sdb

Performed:
- Create new partition  
- Choose default sector values  
- Save and exit  

### 3️⃣ Format the Partition
Formatted the partition using XFS or EXT4:


mkfs.xfs /dev/sdb1


### 4️⃣ Create Mount Point


mkdir /data


### 5️⃣ Mount the Partition


mount /dev/sdb1 /data


### 6️⃣ Make it Persistent (fstab)
Added entry in `/etc/fstab`:


/dev/sdb1  /data  xfs  defaults  0  0


---

## 📸 Screenshots
All screenshots related to this task are located in the `screenshots/` folder.

---

## 🧪 Verification
Commands used to verify:


 - lsblk
 - df -h
 - mount | grep sdb1


---

## 📝 Summary
This module demonstrates:
- Adding a virtual disk  
- Creating standard partitions  
- Formatting and mounting  
- Making persistent entries in fstab 
