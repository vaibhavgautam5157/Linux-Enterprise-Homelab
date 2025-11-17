# LVM (Logical Volume Management) Partitioning

## *What is LVM ?*

LVM is a storage management technology used in Linux that provides far more flexibility than traditional partitioning.
 It allows you to combine multiple physical disks into a single logical volume group, making disk management efficient and scalable.

### **📘 How It Works:**

<img width="629" height="481" alt="LVM" src="https://github.com/user-attachments/assets/e21d2807-ad7c-4fa5-a9c0-e53391df5507" />



**➡️ In the first scenario (Single Disk + Volume Group), a single disk is partitioned and assigned to one volume group.**

**➡️ In the second scenario (Multiple Disks + One Volume Group), several disks are combined into a single volume group from which multiple logical volumes (partitions) are created.**


### **⚙️ Advantages of LVM:**
 - ✅ Flexibility: You can easily resize partitions or add new disks without affecting existing data.
 - ✅ Scalability: If you run out of space in a 300 GB volume group, simply add another disk — for example, extending it to 400 GB — without disrupting the file system.
 - ✅ Dynamic Management: Ideal for environments where disk usage changes frequently, such as virtual machines or corporate servers.


### **🔗 In short:**
 LVM gives Linux Administrators the power to manage storage dynamically, ensuring smooth scalability and efficient resource utilization.

 


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


