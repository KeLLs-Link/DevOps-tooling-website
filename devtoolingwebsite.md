## Setup and technologies used in this Project


As a member of a DevOps team, you will implement a tooling website solution which makes access to DevOps tools within the corporate infrastructure easily accessible.
In this project you will implement a solution that consists of following components:

**`Infrastructure:`** AWS

**`Webserver Linux:`** Red Hat Enterprise Linux 8

**`Database Server:`** Ubuntu 20.04 + MySQL
Storage Server: Red Hat Enterprise Linux 8 + NFS Server

**`Programming Language:`** PHP

On the diagram below you can see a common pattern where several stateless Web Servers share a common database and also access the same files using Network File Sytem (NFS) as a shared file storage. Even though the NFS server might be located on a completely separate hardware – for Web Servers it look like a local file system from where they can serve the same files.

![image](./Screenshots/Snipaste_2024-06-28_11-06-14.png)

It is important to know what storage solution is suitable for what use cases, for this – you need to answer the following questions: what data will be stored, in what format, how this data will be accessed, by whom, from where, how frequently, etc. Based on this you will be able to choose the right storage system for your solution.

### STEP 1 – PREPARE NFS SERVER

Spin up a new EC2 instance with RHEL Linux 8 Operating System.
![image](./Screenshots/new-server.png)

![image](./Screenshots/new-server-running.png)

- **Configure LVM (Logical Volume Manager)on the Server.**


![image](./Screenshots/volumes.png)

![image](./Screenshots/fdisk.png)
Use 
```
df -h 
```
command to see all mounts and free space on your server

![image](./Screenshots/freespace.png)


Use fdisk(fixed or format disk) utility to create a single partition on each of the 3 disks.

List all available disks:
```
sudo fdisk -l
```
![image](./Screenshots/fdisk-l.png)

sudo fdisk /dev/xvdb
![image](./Screenshots/partitioned.png)

Perform the above steps for /dev/xvdc & /dev/xvdd

![image](./Screenshots/partitionscreated.png)
