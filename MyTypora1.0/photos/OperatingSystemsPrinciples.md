# Mind Map

## Chapter1+Chapter2

C:/Users/StevenLiang/Desktop/Study/OperatingSystem/Operating Systems.pdf

# Introduction

- What Operating system do? 是什么？
- Operating-System Operations 有什么操作？
- Storage Structure 储存结构
- Resource Management 资源管理
- Computing Environments  环境

## What is operating systems?

A program that acts as an intermediary between a user of a computer and the computer hardware.

There is no universally accepted definition of Operating-System.

- necessary:

	kernel

- unnecessary:

	systems programs

- not included:

	application programs

- middleware

## Computer System Structure

There are four components:

1. **Hardware**

	provides basis computing resources

2. **Operation system**

3. **Application programs**

	define the ways in which the system resources are  used to solve the computing problems of the users

4. **Users**

Abstract View of Components of Computer:

<img src="C:/Users/StevenLiang/Pictures/Camera Roll/微信图片_20230224145342.png" alt="微信图片_20230224145342" style="zoom:50%;" />

## What Operating system do?

Operating system is a **resource allocator**(资源分配程序) and control program making efficient use of HW and managing  execution of user programs.

## Storage Structure

- Main memory

	主存

	only large storage media that the CPU can access directly.

	主存的特点：

	- Random access 随机访问

	- Typically volatile 通常不稳定

	- Typically random - access memory in the form of Dynamic Random-access  Memory (DRAM).

		通常是以动态随机访问形式，随机访问存储器内存(DRAM)

- Secondary storage

	二级存储器

	extension of main memory that provides large nonvolatile  storage capacity.

- Hard Disk Drives (HDD)

	硬盘驱动器

	rigid metal or glass platters covered with magnetic recording material.

- Non-volatile memory (NVM) devices

	非易失性内存设备

	faster than hard disks, nonvolatile.

### Storage Hierarchy

分级存储器体系；存储层次

### Storage-Device Hierarchy

![微信图片_20230224203920](C:/Users/StevenLiang/Pictures/Camera Roll/微信图片_20230224203920.png)

### How a Modern Computer Works

<img src="C:/Users/StevenLiang/Pictures/Camera Roll/微信图片_20230224204118.png" alt="微信图片_20230224204118" style="zoom:50%;" />

(A von Neumann architecture)

### Direct Memory Access Structure

直接访问内存结构

- Device controller transfers blocks of data from buffer storage directly  to main memory without CPU intervention.

	 设备控制器将数据块从存储缓冲区直接传输到主存，而不需要CPU干预。

- Used for high-speed I/O devices able to transmit information at close to memory speeds.

	用于能够以接近内存速度传输信息的高速I/O设备。

## Resource Management

### Process Management

进程管理

A process is a program in execution. It is a unit of work within the system.

进程是正在执行的程序。它是系统内的一个工作单元。

Program is a passive  entity; process is an active entity.

程序是一个被动的实体; 进程是活动实体。

Process needs resources to accomplish its task e.g. CPU, memory, I/O, files, and Initialization data.

进程需要资源来完成它的任务，例如CPU、内存、I/O、文件和初始化数据。

Process termination requires reclaim of any reusable resources.

进程终止需要回收任何可重用资源。

- Single-threaded process 单线程

	has one program counter specifying location of next instruction to  execute.

	单线程进程有一个程序计数器，指定下一条要执行的指令的位置。

- Multi-threaded process  多线程

	has one program counter per thread.

	多线程进程每个线程有一个程序计数器。

### Memory Management

内存管理

### File-system Management

文件系统管理

### Mass-Storage Management

### Caching

介于CPU和内存之间

### Characteristics of Various Types of Storage

### I/O Subsystem

## Computer System Environments

### Traditional

### Mobile

### Client Server

### Peer-to-Peer

### Cloud computing

### Real-Time Embedded Systems

实时嵌套系统

## What Happens When a Computer is Powered Up?

开机步骤：

1. A bootstrap program executes.

	Bootstrap program is usually stored in a ROM/EEPROM on the  motherboard.

2. The bootstrap program loads the operating-system kernel into the main memory.

3. The bootstrap program lets the CPU executes the kernel.

4. The operating-system kernel loads some other components of the operating system.(the hardware drivers, system  daemons, etc.)

5. The operating-system kernel loads graphic interface program to provide user a graphic interface,  or just stop (stay at a command line environment).

6. The operating-system kernel waits for user input.

## Interrupts

Interrupts provide a mechanism to stop what the CPU is doing and immediately transfer execution to a fixed location.

Interrupt types:

1. Hardware interrupt
2. Software interrupt (exception or trap)

## Multitasking (Timeshareing)

多任务

the CPU executes multiple processes by **switching among them**, but the **switches occur frequently**, so the user feels that  multiple programs are running at the same time.

转换速度快，以至于让用户认为它们在同时进行

![微信图片_20230224195048](C:/Users/StevenLiang/Pictures/Camera Roll/微信图片_20230224195048.png)

## Dual-mode Operation

双模式运转

- user mode

	a program can only access the memory allocated to itself.

- kernel mode

	a program can access the whole memory  including the memory allocated to other programs.

This allows OS to protect itself and other system components.

In a CPU, there is mode bit (a register 寄存器), specifying which mode is using. 

# Operating-System Structures

Operating systems provide an environment for execution of programs and  services to programs and users.

A set of functions that operating-system services provides:

- User interface
- Program execution
- I/O operations
- File-system manipulation
- Communications
- Error detection

## User and Operating-System Interface

- Command line interface (CLI)
- graphical user interface (GUI) 

## Touchscreen Interfaces

## System Calls

System calls provide an interface to the services made available by an operating  system.

### System Call Implementation

### System Call Parameter Passing

### Types of System Calls

- Process control
- File management
- Device management
- Information maintenance
- Communications
- Protection

## System Services



