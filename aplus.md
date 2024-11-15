# Comptia A+ Course Notes
These notes are taken from Myers's *CompTIA A+ Certification All-In-One*, excluding notes from Chapter One 

## The Visible Computer
### The Computing Process
#### The Computer Parts
#### Stages
#### Why it Matters
#### Breaking it Down
### Computing Hardware
### Computing Software
#### Common Operating System Function
#### User Interfaces
#### File Structures and Paths
#### The Tech Launch Points
## CPUs
### CPU Core Components
#### The Man in the Box
#### Clock
#### Back to the External Data Bus
### Memory
#### Memory and RAM
#### Address Bus
### Modern CPUs
#### Developers
#### Technology
### Selecting and Installing CPUs
#### Selecting a CPU
#### Installation Issues
### Troubleshooting CPUs
#### Symptoms of Overheating
#### Catastrophic Failure
## RAM
### Understanding DRAM
#### Organizing DRAM
#### Practical DRAM
#### DRAM Sticks
#### Consumer DRAM
### Types of DRAM
#### SDRAM
#### RDRAM
#### DDR SDRAM
#### DD2
#### DD3
#### DDR3L/DDR3U
#### DDR4
#### RAM Variations
### Working with DRAM
#### Do You Need More RAM?
#### Getting the Right RAM
#### Installing DIMMs
#### Installing SO-DIMMs in Laptop
#### Troubleshooting RAM
## Firmware
### Communications
#### Talking to the keyboard
#### BIOS
### CMOS and RTC
#### Typical System Setup Utility
#### Graphical UEFI System Setup Utility
#### Text-Based UEFI Intel-Based Setup Utility
#### Other BIOS Security Settings
#### Exiting and Saving Settings
### Option ROM and Device Drivers
#### Option ROM
#### Device Drivers
#### BIOS Everywhere
### Power-On Self Test(POST)
#### Before and During the Video Test: Beep Codes
#### Text Errors
#### POST Cards
#### The Boot Process
### Care and Feeding of BIOS/UEFI and CMOS
#### Default/Optimized Settings
#### Clearing CMOS RTC RAM
#### Losing CMOS RTC Settings
#### Flashing the ROM
## Motherboards
### How Motherboards Work
#### Form Factors
#### Chipset
#### Standard Components
#### Additional Components
### Expansion Bus
#### Structure and Function of the Expansion Bus
#### PCI
#### Mini-PCI
#### PCI Express
#### Installing Expansion Cards
#### Troubleshooting Expansion Cards
### Upgrading and Installing Expansion Cards
#### Choosing the Motherboard and the Case
#### Installing the Motherboard
### Troubleshooting Motherboards
#### Symptoms
#### Techniques
#### Options
## Power Supplies
### Understanding Electricity
#### Supplying AC
#### Supplying DC
### Installing and Maintaining Power Supplies
#### Installing
#### Cooling
### Troubleshooting Power Supplies
#### No Motherboard
#### Switches
#### When Power Supplies Die Slowly
#### Fuses and Fire
#### Modular Power Supplies
#### Temperature and Efficiency
## Mass Storage Technologies
### How Hard Drives Work
#### Magnetic Hard Drives
#### Solid-State Hard Drives
#### Hybrid Hard Drives
### Connecting Hard Drives
#### PATA
#### SATA
#### eSATA and other External Drives
#### Refining Mass Storage Communcation
### Protecting Data with RAID
#### RAID
#### Implementing RAID
#### Software vs. Hardware
#### Dedicated Raid Boxes
### Installing Drives
#### Choosing Your Drive
#### PATA Drive Installation
#### Cabling SATA Drives
#### Connecting Solid-State Drives
#### BIOS Support: Configuring CMOS and Installing Drivers
#### Troubleshooting Hard Drive Installation
## Implementing Mass Storage
### Hard Drive Partitions
#### Master Boot Record
#### Dynamic Disks
#### GUID Partition Table
#### Other Partition Types
#### When to Partition
#### Partition Naming Problems
### Hard Drive Formatting
#### File Systems in Windows
#### FAT32
#### NTFS
#### exFAT
#### File Systems in macOS
#### File Systems in Linux
### The Partitioning, Formatting, and Pooling Process
#### Bootable Media
#### Partitioning and Formatting with the Installation Media
#### Disk Management
#### Formatting a Partition
#### Storage Spaces
### Maintaining and Troubleshooting Hard Drives
#### Maintanence
#### Troubleshooting Hard Drive Implementation
#### Third-Party Partition Tools
## Essential Peripherals
### Supporting Common Ports
#### Serial Ports
#### USB Ports
#### Firewire Ports
#### Thunderbolt Ports
#### General Port Issues
### Common Peripherals
#### Keyboards
#### Pointing Devices
#### Biometric Devices
#### Smart Card Readers
#### Barcode/QR Scanners
#### Touch Screens
#### KVM Switches
#### Game Controllers and Joysticks
#### Digitizers
#### Multimedia Devices and Formats
### Storage Devices
#### Flash Memory
#### Optical Media
## Building a PC
### Specialized PCs
#### Prerequisites to Building
#### Custom PCs for Specific Jobs
#### Standard Thick Clients
#### Thin Clients
#### Virtualization Workstation 
#### Gaming PCs
#### Graphics/CAD/CAM Design Workstation
#### Audio/Video Editing Workstation
#### Network Attached Storage Devices
### Installing and Upgrading Windows
#### Media Sources
#### Types of Installation
#### The OS Installation Process
#### Troubleshooting Installation Problems
### Post-Installation Tasks
#### Patches, Service Packs, and Updates
#### Upgrading Drivers
#### Restoring User Data Files (If Applicable)
#### Install Essential Software
#### Migrating and Retiring Systems
#### No Installation is Perfect
#### Privacy Concerns with Windows 10
## Windows Under the Hood
### Registry
#### Accessing the Registry
#### Registry Components
#### Talking Registry
#### Manual Registry Edits
#### Command-Line Registry Editing Tools
### The Boot Process
### Applications, Processes, and Services
#### Task Manager
#### Resource Monitor
#### Performance Tools
### Tools for Programmers
#### Component Services
#### Data Sources
## Users, Groups, and Permissions
### Authentication with Users and Groups
#### User Accounts
#### Passwords
#### Groups
#### Standard User and Elevated Privileges
#### Configuring Users and Groups in Windows
### Authorization Through NTFS
#### NTFS Permissions
#### Inheritance
#### Permission Propagation
#### Techs and Permissions
#### Permissions in Linux and macOS
### Sharing Resources Securely
#### Sharing Folders and Files
#### Locating Shared Folders
#### Administrative Shares
#### Protecting Data with Encryption
### Beyond Sharing Resources
#### Security Policies
#### User Account Control
#### How UAC Works
#### UAC in Modern Windows
## Maintaining and Optimizing Operating Systems
### Maintaining Operating Systems
#### Patch Management
#### Managing Temporary Files in Windows
#### Registry Maintenance
#### Disk Maintenance Utilities
#### Scheduling Maintenance
#### Controlling Autostarting Software
#### Handy Windows Administration Tools
### Optimizing Operating Systems
#### Installing and Removing Software
#### Installing and Optimizing a Device
#### Performance Options
### Preparing for Problems
#### Backing Up Personal Data
#### System Restore in Windows
## Working with the Command-Line Interface
### Deciphering the Command-Line Interface
#### Shells
#### Accessing the Command-Line Interface in Windows
#### Accessing the Command-Line Interface in macOS and Linux
#### The Command Prompt
#### Closing the Terminal
#### File Formats and Filenames
#### Drives and Folders
### Mastering Fundamental Commands
#### Structure: Syntax and Switches
#### Viewing Directory Contents: dir and ls
#### Changing Directory Focus: cd 
#### Moving Between Drives
#### Making Directories: mk and mkdir
#### Removing Directories: rm and rmdir
#### Running a Program in Windows
#### Running a Program in macOS and Linux
### Working with Files
#### Using Wildcards to Locate Files
#### Deleting Files
#### Copying and Moving Files
#### Pruning and Grafting Folder Trees
### Assorted Windows Commands
#### chkdsk(/f /r)
#### format
#### hostname
#### gpupdate
#### gpresult
#### sfc
#### shutdown
#### Using Special Keys in Windows
#### Powershell
### Assorted macOS and Linux Commands
#### ifconfig
#### iwconfig
#### ps
#### grep
#### apt-get/APT
#### vi
#### dd
#### shutdown
#### passwd
### Scripting
#### Script Types and Languages
#### Anatomy of a Script
#### Environment Variable
## Troubleshooting Operating Systems
### Failure to Boot
#### Failure to Boot: Hardware or Configuration
#### Failure to Boot: Windows
#### Failure to Boot: Linux
### Failure to Start Normally
#### Device Drivers
#### Registry
#### Advance Startup Options
#### Rebuild Windows Profiles
#### Troubleshooting Tools
#### More Control Panel Tools
### Application Problems
#### Application Installation Problems
#### Problems with Uninstalling
#### Compatibility
#### Missing File or Incorrect File Version
#### Unresponsive Apps
#### Application Crashes
#### Volume Shadow Copy Service and System Protection
## Display Technologies
### Video Displays
#### LCD Monitors
#### Projectors
#### VR Headsets
#### Common Monitor Features
### Display Adapters
#### Motherboard Slot
#### Graphics Processor
#### Video Memory
#### Integrated GPUs
#### Connector Types and Associated Cables
### Installing and Configuring Video
#### Software
#### Working with Drivers
#### 3-D Graphics
### Troubleshooting Video
#### Troubleshooting Video Cards and Drivers
#### Troubleshooting Monitors
#### Troubleshooting Projectors
### Additional Display Topics
#### MicroLED
#### High Dynamic Range
#### Adaptive Sync
#### Video Modes
#### eGPUs
## Essentials of Networking
### Roles Hosts Play in Networks
### Networking Technologies
#### Frames and NICs
#### Ethernet
#### Ethernet with Twisted Pair
#### Ethernet with Alternate Connections
### Implementing Ethernet
#### Typical LAN
#### Structured Cabling
#### Going Wide
## Local Area Networking
### TCP/IP
#### Network Addressing with IPv4
#### TCP/UDP
#### Network Addressing with IPv6
### Installing and Configuring a Wired Network
#### Installing a NIC
#### Configuring IP Addressing
#### Connecting to a Switch
#### Sharing and Security
#### Network Shares
#### Network Organization
### Troubleshooting Networks
#### Repairing Physical Cabling
#### Fixing Common Problems
## Wireless Networking
### Wireless Networking Components
#### Wireless Networking Software
#### Wireless Network Modes
#### Wireless Networking Security
#### Speed and Range Issues
### Wireless Networking Standards
#### IEEE 802.11-Based Wireless Networking
#### Other Wireless Standards
### Installing and Configuring Wireless Networking
#### Wi-Fi Configuration
#### Bluetooth Configuration
#### Cellular Configuration
### Troubleshooting Wi-Fi
#### Hardware Troubleshooting
#### Software Troubleshooting
#### Connectivity Troubleshooting
#### Configuration Troubleshooting
## The Internet
### How the Internet Works
#### Internet Tiers
#### TCP/IP: The Language of the Internet
#### Internet Service Providers
#### Connection Concepts
### Connecting to the Internet
#### Dial-Up
#### DSL
#### Cable
#### Fiber
#### Wi-Fi
#### Line-of-Sight Wireless
#### Cellular
#### Satellite
#### Connection to the Internet
### Internet Application Protocols
#### The World Wide Web
#### E-Mail
#### File Transfer Protocol(FTP)
#### Telnet and SSH
#### SFTP
#### Voice over IP
#### Remote Desktop
#### Virtual Private Networks
#### File Sharing
#### Internet Utility Protocols
#### The Internet of Things
### Internet Troubleshooting
#### No Connectivity
#### Limited Connectivity
#### Local Connectivity
#### Slow Transfer Speeds
#### Online Gaming
## Virtualization
### Benefits of Virtualization
#### Power Saving
#### Hardware Consolidation
#### System Management and Security
#### Research
### Implementing Virtualization
#### Meet the Hypervisor
#### Emulation vs. Virtualization
#### Client-Side Virtualization
#### Server-Side Virtualization
### To The Cloud
#### The Service-Layer Cake
#### Ownership and Access
#### Why The Cloud
## Portable Computing
### Portable Computing Devices
#### Taxonomy
#### Input Devices
#### Display Types
### Extending Portable Computers
#### Single Function Ports
#### Networking Options
#### Portable Specific Expansion Slots
#### Storage Card Slots
#### General Purpose Ports
### Managing and Maintaining Portable Computers
#### Batteries
#### Power Management
#### Cleaning
#### Heat
#### Protecting the Machine
### Upgrading and Repairing Laptop Computers
#### Disassembly Process
#### Standard Upgrades
#### Hardware/Device Replacement
### Troubleshooting Portable Computers
#### Power and Performance
#### Components
## Understanding Mobile Devices
### Mobile Computing Devices
#### Device Variants
#### Mobile Hardware Features
### Mobile Operating Systems
#### Development Models
#### Apple iOS
#### Google Android
#### Mobile OS Features
### Configuring a Mobile Device
#### Enhancing Hardware
#### Installing and Configuring Apps
#### Network Connectivity
#### Data
#### E-Mail
#### Synchronization
#### Mobile Device Communication and Ports
## Care and Feeding of Mobile Devices
### Troubleshooting Mobile Device Issues
#### Troubleshooting Tools
#### Touchscreen and Display Issues
#### Apps Not Loading
#### Overheating
#### Slow Performance
#### Battery Life
#### Swollen Battery
#### Frozen System
#### Cannot Broadcast to an External Monitor
#### No Sound from Speakers
#### Connectivity and Data Usage Issues
#### GPS and Location Services Problems
#### System Lockout
#### Encryption Problems
### Securing Mobile Devices
#### BYOD vs. Corporate-Owned Devices
#### Profile Security Requirements
#### Preventing Physical Damage
#### Combating Malware
#### Dealing with Loss
#### Recovering from Theft
#### Securing Your Data
### Mobile OS and Application Security Issues
#### Troubleshooting Tools
#### Risks, Symptoms, and Clues
## Printers and Multifuction Devices
### Printer and Multifunction Device Components and Technologies
#### Printers
#### Scanners
#### Copy and Fax Components
#### Automatic Document Feeders
#### Connectivity
### The Laser Printing Process
#### Processing
#### Charging
#### Exposing
#### Developing
#### Transferring
#### Fusing
#### Cleaning
### Installing a Multifuction Device
#### Setting Up Printers in Windows
#### Configuring Print Settings
#### Optimizing Print Performance
#### Managing Public/Shared/Networked Devices
### Troubleshooting Printers
#### Troubleshooting General Issues
#### Troubleshooting Impact Printers
#### Troubleshooting Thermal Printers
#### Troubleshooting Inkjet Printers
#### Troubleshooting Laser Printers
#### Troubleshooting 3-D Printers
## Securing Computers
### Analyzing Threats
#### Unauthorized Access
#### Social Engineering
#### Denial of Service
#### Data Destruction
#### Administrative Access
#### System Crash/Hardware Failure
#### Physical Theft
#### Malware
#### Environmental Threats
### Security Concepts and Technologies
#### Access Control
#### Data Classification and Compliance
#### Licensing
#### Incident Response
### Network Security
#### Malicious Software
#### Malware Signs and Symptoms
#### Malware Prevention and Recovery
#### Firewalls
#### Internet Appliances
#### Authentication and Encryption
#### Wireless Issues
## Operational Procedures
### Documentation Best Practices
#### Network Documentation
#### Company Policies
#### Inventory Management
### Managing Change Managment
#### Change Managment Process
#### Implementing Change(Scenario)
### Disaster Prevention and Security
#### Power Protection
#### Backup and Recovery Procedure
#### Account Recovery

