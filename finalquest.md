# File Systems and Storage Management
#### By Jack Seymour
#### Operating Systems CMSI 3510

## Introduction
For my final quest, I decided to focus on **File Systems and Storage Management**. File systems are a fundamental part of understanding operating systems. Within computing, file systems are responsible for managing how data is stored, organized, retrieved, and secured on physical and virtual storage devices. As data storage needs have become more intense, file systems have evolved to adapt to these needs. With these complexities, file systems support features such as journaling, encryption, and fault tolerance. In modern operating systems, such as Windows, macOS, and Linux, file systems are tailored to balance metrics such as performance, reliability, and compatibility across various hardware applications of the operating system.

This report will focus on exploring the architecture and functionality of file systems, with an emphasis on their role in storage management. It begins by explaining the core principles underlying file systems and their organization. Next, it will compare popular file systems such as NTFS, FAT32, EXT4, and APFS, highlighting their strengths and limitations. The report will explore some modern operating systems and why they choose their respective file systems within them.

---

## Architecture and Functionality of File Systems
A file system can be defined as the system that links the operating system with the storage media. File systems provide a way for organizing data in a structured manner and offer mechanisms for accessing such data in an efficient and reliable manner. A file system is divided into three layers namely the **physical layer**, the **logical layer** and the **virtual file system layer**. All these layers work in conjunction to ensure that data is well arranged, easily retrieved and protected.

### The Physical Layer
The physical layer or commonly known as the storage layer deals with the physical storage devices such as the hard disk drives (HDDs), solid state drives (SSDs) among others. This layer handles the complexities of the raw data blocks and presents them as sectors or clusters that can be addressed. This layer is responsible for “translating the actual data that makes up a file system into a standardized file system interface” and often involves significant on-the-fly translation for virtualized or network file systems (Gambord, 2024). Thus, the storage layer implements the lower level data that is used in the rest of the layers, including the logical structure.

### The Logical Layer
The logical layer or the file system layer defines the logical organization of the data. It divides data into blocks and names the blocks with filenames and extends directories to arrange the files in a data structure for easy storage and retrieval. Within this layer, several key components include:

- **Inodes**: Metadata structures that store information about files, including ownership, permissions, and storage locations on the disk. “Each inode has a unique numeric ID, called the inode number or file serial number” (Gambord, 2024).
![Inode Table Diagram](https://rgambord.github.io/cs374/_images/inode_table.svg)
- **Dentry Objects**: These directory entries associate filenames with inode numbers and organize the file system as a tree-like structure, allowing navigation across parent and child directories (Gambord, 2024).
- **File Allocation Table (FAT)**: A simple indexing scheme based in older file systems to keep track of the locations of the files.
- **Journals**: Used by contemporary file systems including EXT4 and NTFS journals record the changes made to the files before they are actually made to enhance data integrity in case of system shutdowns or crashes.

This layer also manages critical functionalities such as space allocation and fragmentation control. Advanced file systems, such as Btrfs and ZFS, implement features like data deduplication, checksumming, and snapshots, which enhance reliability and efficiency.

### The Virtual File System Layer
The virtual file system (VFS) acts as the intermediary between the logical and physical layers, enabling users to interact seamlessly with the file system. The VFS “manages a cache of objects that were recently retrieved from the physical file system” to improve performance by minimizing direct interactions with storage hardware (Gambord, 2024).

This layer abstracts the details of the underlying storage mechanism, providing a unified view of disparate storage systems. For instance, pseudo file systems like `/proc` or `/dev` are dynamically generated in memory but appear to users as part of the cohesive file system tree (Gambord, 2024).

---

## Comparison of Popular File Systems
Modern computing relies on diverse file systems tailored to specific needs such as performance, compatibility, reliability, and security. This section compares four widely used file systems—**FAT32**, **NTFS**, **EXT4**, and **APFS**—highlighting their strengths and limitations.

### FAT32 (File Allocation Table)
FAT32, introduced with Windows 95, is one of the oldest file systems still in use today. Its simplicity and cross-platform compatibility make it ideal for external drives, USB sticks, and camera storage. Kingston notes its simplicity, "makes it easy to implement and use, making it suitable for devices with limited resources or compatibility requirements."
- **Strengths**: Universal compatibility with Windows, macOS, and Linux.  
- **Limitations**: “does not support file-level security permissions, journaling, encryption, or compression” (Kingston), a 4 GB maximum file size, and a 2 TB partition size limit.

### NTFS (New Technology File System)
NTFS is the default file system for modern Windows operating systems. It supports journaling, encryption, and large files and partitions, making it ideal for enterprise and personal use. However, macOS offers only read support for NTFS without third-party tools.  
- **Strengths**: Advanced features like journaling, file permissions, and encryption.  
- **Limitations**: Limited cross-platform compatibility.

### EXT4 (Fourth Extended File System)
EXT4 is the default file system for most Linux distributions. It balances performance and reliability, supporting journaling and large file sizes. However, EXT4 lacks native support on Windows or macOS.  
- **Strengths**: High performance on Linux, robust journaling, and advanced features.  
- **Limitations**: Limited compatibility outside Linux.

### APFS (Apple File System)
APFS, introduced with macOS High Sierra in 2017, is optimized for SSDs and flash storage. It features strong encryption, snapshots, and fast directory sizing, making it integral to Apple’s ecosystem. According to Kingston, APFS “offers improved performance compared to its predecessor, HFS+.”
- **Strengths**: Excellent performance on SSDs, robust encryption, and support for snapshots.  
- **Limitations**: Exclusivity to Apple platforms.

---

## File Systems in Modern Operating Systems
### Windows
Windows primarily uses NTFS for internal drives due to its robust features, including journaling and file-level permissions. For external storage, Windows supports FAT32 and exFAT, offering compatibility with other platforms.

### macOS
Mac computers transitioned from HFS+ to APFS, which is optimized for SSDs and integrates well with Apple’s hardware and software. macOS also supports FAT32 and exFAT for external storage compatibility with non-Apple devices.

### Why These Choices Matter
The choice of file system reflects the priorities of the operating system’s design philosophy:  
- **Windows** prioritizes functionality and compatibility. NFTS is more versatile for a broad range of applications and customizability compared to Apple.
- **macOS** Apple's mindset prioritizes hardware integration and high data security. This added security makes APFS not usable on other operating systems. This seems to be an intentional move by Apple in their products. 

---

## Conclusion
File systems are have integral architecture for operating systems. They serving as the backbone for data storage and management. By using this report, we can understand the architecture, functionality, and design of popular file systems. This report has provided a look into how modern computing platforms manage and secure data efficiently.


References
---
Gambord, R. "File System Structure." *File System Structure - CS 374 - Operating Systems Documentation*, rgambord.github.io/cs374/modules/03/file-system-concepts/structure/.

“Understanding File Systems.” _Kingston Technology Company_, Aug. 2023, www.kingston.com/en/blog/personal-storage/understanding-file-systems.
