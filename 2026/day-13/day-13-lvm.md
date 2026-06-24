# Day 13 – Linux Volume Management (LVM)

## Task
Learn LVM to manage storage flexibly – create, extend, and mount volumes.

### Task 1: Check Current Storage
```bash
`lsblk` 
`df -h` 
`pvs`   
`vgs`   
`lvs`  
```
**observation** 
- No existing physical volumes, volume groups, or logical volumes
- `/dev/root` usage: 6.7G, 31% used

<img width="977" height="410" alt="task1 2" src="https://github.com/user-attachments/assets/2b84a264-57d7-4f52-8e80-8f146dd06ff1" />


<img width="709" height="355" alt="task1 3" src="https://github.com/user-attachments/assets/991e11df-d074-4e5d-9f62-6b43c5c48acb" />


### Task 2: Create Physical Volume
Command:
```bash
pvcreate /dev/xvdf /dev/xvdg /dev/xvdh    
pvs                                       
```
**observation** 

- Initialised/created physical volumes blocks "/dev/xvdf" "/dev/xvdg" "/dev/xvdh".
- Displays physical volumes ready to use

<img width="602" height="355" alt="task2 1" src="https://github.com/user-attachments/assets/f9ee1ad0-78b8-449f-929e-d74ffcf5dd79" />


<img width="667" height="261" alt="task2" src="https://github.com/user-attachments/assets/2300dd90-0da0-4d2d-af32-16f1f1b7c16a" />


### Task 3: Create Volume Group
Command:
```bash
vgcreate "tws_vg" /dev/xvdf /dev/xvdg	    
vgs                                       
```
**observation** 
- created volume group "tws_vg" from physical volumes "/dev/xvdf" and "/dev/xvdg".
- Available free space to use is 22G.

<img width="617" height="202" alt="task3" src="https://github.com/user-attachments/assets/be48d89e-ab7f-4de5-a4f6-de7c8334bed2" />

### Task 4: Create Logical Volume
Command:

```bash
lvcreate -L 10G -n tws_lv tws_vg	    
lvs                                   # Shows logical volumes.
```
**observation** 
- Created logical volume of 10GB with name "tws-lv" from logical group "tws_vg"
  
<img width="512" height="101" alt="task4" src="https://github.com/user-attachments/assets/ce3dfb02-ab29-4426-baaa-7ffa041abbd4" />

### Task 5: Format and Mount
Command:

```bash
mkdir -p /mnt/tws_lv_mount                  
mkfs.ext4 /dev/tws_vg/tws_lv               
mount /dev/tws_vg/tws_lv /mnt/tws_lv_mount  
df -h                                       
```
**observation** 
- Created directory for mount point -> "/mnt/tws_lv_mount"
- Before do mounting first formating LV with ext4 filesystem
- Mounted LV onto mount point -> /mnt/tws_lv_mount


<img width="1080" height="591" alt="task5" src="https://github.com/user-attachments/assets/5723694c-e02b-4868-8cfb-cded45220882" />


### Task 6: Extend the Volume
Command:

```bash
lvextend -L +5G /dev/tws_vg/tws_lv      
lsblk                                   
				
```
**observation** 
- Logical volume resized from 10G to 15G
  
<img width="1130" height="680" alt="task6" src="https://github.com/user-attachments/assets/4daaa2b5-ab65-4e08-89d6-956b642c1aa0" />

### Commands used
| Command | Purpose |
|----|----|
| lsblk | List all storage devices and partitions. |
| df -h | Shows mounted file systems and their usage.|
| pvs	  | Shows existing physical volumes |
| vgs   | Shows existing volume groups |
| lvs   | Shows existing logical volumes |
| pvcreate /dev/xvdf /dev/xvdg /dev/xvdh  | Creates physical volumes for blocks/devices "/dev/xvdf" "/dev/xvdg" "/dev/xvdh".|
| vgcreate "tws_vg" /dev/xvdf /dev/xvdg	| creates volume group "tws_vg" from physical volumes "/dev/xvdf" and "/dev/xvdg".|
| lvcreate -L 10G -n tws_lv tws_vg	| Creates logical volume of 10GB with name "tws-lv" from logical group "tws_vg" |
| lvextend -L +5G /dev/tws_vg/tws_lv	| Logical volume gets resized |
| mkdir -p /mnt/tws_lv_mount		|	Created directory for mount point -> "/mnt/tws_lv_mount"|
| mkfs.ext4 /dev/tws_vg/tws_lv		| Before do mounting first formating LV with ext4 filesystem|
| mount /dev/tws_vg/tws_lv /mnt/tws_lv_mount |	Mount  LV onto mount point -> /mnt/tws_lv_mount|





