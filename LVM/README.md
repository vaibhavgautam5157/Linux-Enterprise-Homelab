# LVM (Logical Volume Management) Partitioning

🎯 Objective
- To demonstrates the complete workflow of creating and managing Logical Volumes (LVM) in a Linux environment.  


---

## 📌 **Project Overview**

Logical Volume Management (LVM) allows combining multiple physical disks into single logical volume group, enabling dynamic resizing and easy storage expansion.

In this project, we performed:

- **Adding new disks to the system**  
- **Creating physical volumes (PV)**  
- **Creating a volume group (VG)**  
- **Creating logical volumes (LV)**  
- **Formatting & mounting logical volumes**  
- **Extending logical volumes and resizing the filesystem**  
- **Verifying disk and LVM states**  

---

## 🧩 Steps Performed

### 1️⃣ Identify New Disks
- Used the following commands to list available disks:

  - lsblk
  - fdisk -l

### 2️⃣ Create Partition for LVM

- fdisk /dev/sdb

- proceed with options:
  - create new partiotion ( n )
  - primary partition ( p )
  - accept default partition number ( 1 ) and sector value and press enter
  - to change the partition type of LVM , type ( t ), then ( L ) to list hex codes and select ( 8e ) for LVM
  - confirm partition type by typing ( p )
  - write the changes with ( w )

### 3️⃣ Create Physical Volumes (PV)

- pvcreate /dev/sdb1


### 4️⃣ Verify PV

- pvdisplay


### 5️⃣ Create Volume Group (VG)

- vgcreate oracle_vg /dev/sdb1


### 6️⃣ Verify VG

- vgdisplay oracle_vg  


### 7️⃣ Create Logical Volume (LV)

- lvcreate -n oracle_lv --size 1000M oracle_vg


### 8️⃣ Verifying LV

- lvdisplay

  
### 9️⃣ Formating and Mounting LV 

- Formatting LV
  - mkfs.xfs /dev/oracle_vg/oracle_lv

- Create Mount Point & Mount LV
  - mkdir /LVM_oracle
  - mount /dev/oracle_vg/oracle_lv /LVM_oracle


### 🔟 Verify Final LVM Setup

- lsblk
- df -h

  
---


## 📁 Screenshots
All screenshots related to each step are available in the `Screenshots/` directory.


