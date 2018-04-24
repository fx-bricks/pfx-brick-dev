# Interface Control Document (ICD)

The Interface Control Document (ICD) describes in detail the communication format between the PFx Brick and a USB or BLE connected host. The document also includes explanations for how data is stored in the PFx Brick, including event/actions and the file system as well data formats.

The ICD is structured as follows:

## Device Identity / Discovery

The PFx Brick is a USB HID compliant device. The details of the USB device class are described as well as the USB endpoint specifications.

The PFx Brick BLE GATT services are described so that a BLE connected host can discover and connect to an advertised PFx Brick.

## Memory Map / File System

A description of how the flash memory is organized in the PFx Brick is provided. Since most of the flash memory is used by the file system, there is a comprehensive description of the file system structure and access methods.

## Event / Action Data Structures

The fundamental behaviour of the PFx Brick is to perform Actions in response to Events.  The Actions are stored in an Event Look-Up-Table (LUT).  Comprehensive descriptions of both events and actions are provided.

## Command Messages

There are many different commands which can be used to interact with the PFx Brick.  They are organized into a few functional categories including:

1. Operation and Configuration 
2. Event/Action LUT 
3. Audio 
4. Service 
5. File System
6. Bluetooth
7. Notifications
8. Low-Level Test


Details of every command message and expected responses from the PFx Brick are described.

## Code Tables

The end of the document includes numerical code tables for items such as Product ID, Error codes, Status Codes, etc.

