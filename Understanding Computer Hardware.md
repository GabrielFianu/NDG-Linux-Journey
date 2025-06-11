# Understanding Computer Hardware. 

## Introduction
This exercise will help you learn about commands to display information about the computer's hardware.

---

### Use commands to list hardware

In this task, you will execute several commands and examine several files to display your hardware configuration.

In order to determine the type of CPU, execute the lscpu command:

lscpu

![Image](https://github.com/user-attachments/assets/291da920-7ff1-4c61-a7e4-25b2fbd503dd)

![Image](https://github.com/user-attachments/assets/349c2d11-0b88-486d-af5e-9754d7ee34f6)


Being able to display CPU information can be important when trying to determine if more advanced Linux features can be used on your system. 
For even more details about your CPU(s), you can examine the /proc/cpuinfo file, especially the "flags" that are listed which determine whether or not your CPU has certain features.

**Use the head command with the -n option to list the first 20 lines of the cpuinfo file**

head -n 20 /proc/cpuinfo

![Image](https://github.com/user-attachments/assets/7b8fd081-3e4a-4198-8393-1798b252d4b7)

**To discover how much RAM and swap space is being used, use the free command**

free -m
free -g

The output shows the amount of memory in megabytes when the -m option is used and in gigabytes when the -g option is used:

![Image](https://github.com/user-attachments/assets/250df558-fa31-4c8c-a61c-acee9049b6f1)

![Image](https://github.com/user-attachments/assets/88ffc28a-f1d6-4b5d-aa10-c1f4604e92c5)

In the output above, you can see that the system has 64298 megabytes (roughly 64 gigabytes) of physical memory (RAM). Of that, only 12937 megabytes are being used, a good sign that you have enough memory for your system's needs.
In the event that you run out of memory, swap is used. Swap is hard drive space that is used to temporarily store data that is supposed to be stored in RAM.


To see what devices are connected to the PCI bus, use the lspci command:

lspci

![Image](https://github.com/user-attachments/assets/0c983b4e-def9-477c-96e4-df843e633d51)

**Notice** from the partial output below, that many of the devices connected to the system board are displayed:
The output of the lspci command can be helpful for identifying devices that are not supported by the Linux kernel. 
Some devices such as video cards may only provide basic functionality without installing proprietary driver software. However, new distributions are rapidly addressing this problem and advanced hardware functionality is more commonly available today.


Use the lspci command with the -k option to show devices along with the kernel driver and modules used:

![Image](https://github.com/user-attachments/assets/b7213c17-8977-4a96-b29b-efa1a00d9467)


Attempt to list the USB connected devices:

lsusb

![Image](https://github.com/user-attachments/assets/fedb8ac4-9e5b-47f7-be6a-fe799a5763ed)

This is how you can get information on any USB memory sticks that you may want to mount, as well as peripheral devices like mice and keyboards.


For hardware to function, the Linux kernel usually loads a driver or module. Use the lsmod command to view the currently loaded modules:

lsmod

![Image](https://github.com/user-attachments/assets/686d57ef-690d-423c-915f-cb74376a155f)

Partial output of the command is shown below. The first column is the module name, and the second is the amount of memory used by the module. 
The number in the "Used by" column indicates how many other modules are using the module. The names of the other modules using the module may also be listed in the "Used by" column, but is often incomplete:


The system board of many computers contains what is known as BIOS, or a Basic Input and Output System. System Management BIOS, or SMBIOS, is a standard defining the data structures and how to communicate information about computer hardware.

The fdisk command is useful for identifying and manipulating disk storage resources on a system. Since it can be used to create, format and delete partitions, as well as for getting information, it should be used with care in administrator mode to avoid data loss. 
The fdisk command can be used in two ways: interactively and non-interactively.

When the -l option is used with fdisk, then the command will non-interactively list block devices, which includes disks (hard drives) and logical volumes.

![Image](https://github.com/user-attachments/assets/4dcc756c-f60e-49ce-8dec-118dbbd5f4b6)

Without the -l option, the fdisk command enters an interactive mode that is typically used to modify partitions on a disk device.




