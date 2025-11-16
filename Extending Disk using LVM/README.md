# Extending Disk Using LVM (Logical Volume Manager)

- **The Need to extend a disk arises when an existing disk, such as one mounted on oracle, become full.**

This project demonstrates how to extend storage in a Linux system using LVM (Logical Volume Manager).  


---

## 🚀 Project Overview

LVM allows flexible disk management by logically grouping storage devices.  
In this project, I extended an existing LVM-based filesystem by:

- Adding a new virtual disk (`/dev/sdc`)
- Creating a new LVM Physical Volume (PV)
- Extending the existing Volume Group (VG)
- Increasing the size of the Logical Volume (LV)
- Growing the XFS filesystem `xfs_growfs` to use the newly added space



---

## 🛠️ Steps Performed

### **1️⃣ Verify Current Disks**

- Used tools like:
  - lsblk
  - fdisk -l



### **2️⃣ Add a New Virtual Disk**

- Added `/dev/sdc` from the hypervisor and confirmed detection.



### **3️⃣ Create a New Partition**

- fdisk /dev/sdc

*Created a new partition `/dev/sdc1` and set its type to LVM (`8e`).*



### **4️⃣ Initialize the Partition as a PV**

- pvcreate /dev/sdc1



### **5️⃣ Extend the Volume Group**

- vgextend oracle_vg /dev/sdc1



### **6️⃣ Extend the Logical Volume (LV)**

- lvextend -L +1000 /dev/oracle_vg/oracle_lv



### **7️⃣ Grow the XFS Filesystem**

- xfs_growfs /LVM_oracle



### **8️⃣ Verify Extended Storage**

- df -h
- lsblk



---


## 📂 Screenshots

All related screenshots showing each step are available in the `Screenshots/` directory of this repository.

---

## 📘 Learning Outcome

By completing this project, I gained hands-on experience with:

- LVM storage architecture (PV, VG, LV)
- Disk partitioning using `fdisk`
- Extending volumes safely on a running Linux system
- Growing XFS filesystems online
- Troubleshooting mount issues and updating `/etc/fstab`




---



## 📎 Conclusion

This project demonstrates a complete workflow of extending disk storage using LVM, a critical real-world skill for managing Linux servers.  
The steps and screenshots serve as a reference for anyone learning storage management on Linux.

