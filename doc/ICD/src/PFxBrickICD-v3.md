---
title: PFx Brick USB & Bluetooth LE Host Interface Control Document Revision 3.36
date: Dec 8, 2020
author: Fx Bricks
toc: yes
revision: 3.38
doc_no: 11 80 17 10001
---

\pagebreak

\section*{Revision Notes}

Changes made to each version of this document are summarized in the table below.

\renewcommand{\arraystretch}{1.5}
\begin{tabular}{ | c | p{13.8cm} | }
  \hline
  Rev & Change Notes  \\
  \hline
  2.1  & The \lstinline|PFX_CMD_GET_ICD_REV| message was added so that firmware can report which revision of ICD it conforms with. \\
       & The \lstinline|COMMAND_IR_LOCKOUT_TOGGLE| command was added to the \lstinline|COMMAND| byte of event/action definition. \\
       & The \lstinline|MOTOR_ACTION_ID| definitions for \lstinline|MOTOR_STOP| and \lstinline|MOTOR_COAST| were redefined to \lstinline|MOTOR_ESTOP| and \lstinline|MOTOR_STOP| respectively. \\
       & New PFX settings bit added to the PFx Brick configuration called Audio DRC. \\
       & The \lstinline|PFX_CMD_WRITE_SN| and \lstinline|PFX_CMD_READ_SN| messages were added to manage PFx Brick serial number assignment. \\
  \hline
  2.2  & Added description for the traffic light combo light f/x. \\
  \hline
  2.3  & Added new message \lstinline|PFX_CMD_GET_CURRENT_STATE| to report internal operating state of motors, lights, audio, etc. \\
  \hline
  2.4  & Modified the format of the \lstinline|PFX_CMD_GET_CURRENT_STATE| message to report motor PWM speed. \\
       &  Corrected the numeric definitions of \lstinline|BAR_STYLE| used with the sound bar light f/x. \\
  \hline
  2.5  & Added new message \lstinline|PFX_CMD_GET_IRRX_STATUS| message to report low level data from the IR receiver processor. \\
  \hline
  2.6  & Added new message \lstinline|PFX_CMD_SET_AUDIO_EQ| message to set audio equalization levels.  The valid range for bass/treble EQ values has been set to -20 to +20 dB in the configuration. \\
       & Modified the \lstinline|PFX_CMD_GET_CURRENT_STATE| message format to send the internal millisecond counter data. \\
  \hline
  2.7  & Added new parameter \lstinline|SWEEP_STYLE| for the \lstinline|COMBOFX_LINEAR_SWEEP| and \lstinline|COMBOFX_BARGRAPH_SWEEP| combination light f/x. \\
  \hline
  2.8  & Added new \lstinline|MOTOR_STEP| parameter for Lego compatible 7 step operation. \\
       & Added new \lstinline|COMBOFX_LAVA_LAMP| combo light f/x \\
       & Added new \lstinline|WHELEN_STYLE| parameter for a random program of flashing sequences. \\
  \hline
  2.9  & Added new motor configuration bit "TLG Mode" to add emulation of the Lego IR receiver motor control. \\
  \hline
\end{tabular}

\renewcommand{\arraystretch}{1.5}
\begin{tabular}{ | c | p{13.8cm} | }
  \hline
  Rev & Change Notes  \\
  \hline
  3.0  & Revised the \lstinline|PFX_CMD_GET_STATUS| message to include comprehensive product identification.  This includes a new fields for USB PID, Product Number, Product Descriptor, a new 4-byte Serial Number, and a new 2-byte Firmware Version. \\
       & Deprecated the Product ID, Hardware Version, Firmware Version, and Serial Number fields in the the \lstinline|PFX_CMD_GET_CONFIG| message. \\
       & Revised the \lstinline|PFX_CMD_WRITE_SN| and \lstinline|PFX_CMD_READ_SN| messages to accommodate the new 4-byte serial number format. \\
       & Added new \lstinline|COMMAND| bytes to the event/action LUT. \\
       & Renamed \lstinline|EVT_DEFAULT_EVENT| to \lstinline|EVT_STARTUP_EVENT1| and added 3 more startup events. \\
  \hline
  3.1  & Revised the \lstinline|PFX_CMD_GET_ICD_REV| message to support a 2-byte revision numbering scheme. \\
  \hline
  3.11 & Added a new \lstinline|RETRIGGER| parameter to the \lstinline|SOUNDFX_PLAY_ONCE| sound f/x. \\
       & Added new \lstinline|COMBOFX_LASER_CANNON| combination light f/x. \\
       & Corrected the description of \lstinline|EVT_STARTUP_EVENTx| for both the \lstinline|PFX_CMD_GET_EVENT_ACTION, PFX_CMD_SET_EVENT_ACTION| messages. \\
  \hline
  3.12 & Changed the format of the \lstinline|PFX_CMD_GET_AUDIO_LUT_ENTRY| message to also return the start address of the audio sample data. The File Size field now represents the Data Size of audio sample data, not the total file size.  These changes reflect internal changes in the firmware to be tolerant of different WAV file formats including LIST and INFO chunks. \\
       & Changed the format of the \lstinline|PFX_CMD_ADD_AUDIO_DATA| message to report progress information for lengthy flash erase operations which result in a \lstinline|PFX_ERR_TRANSFER_BUSY_WAIT| status response code. \\
  \hline
  3.13 & Added suggested default values for all of the light f/x. \\
  \hline
  3.14 & Added new \lstinline|LIGHTFX_BROKEN_LIGHT| single light f/x. \\
       & Added new \lstinline|LIGHTFX_STATUS_INDICATOR| single light f/x. \\
       & Revised the definition of the light output 7 for emergency flashers from solid to 2x flasher. \\
       & Added a Silent flag for the \lstinline|PFX_CMD_GET_ICD_REV| message so that it can be used for covert connection monitoring. \\
  \hline
  3.15 & Added new \lstinline|LIGHTFX_SOUND_MODULATED| single light f/x. \\
       & Added new \lstinline|FLICKER_ON| parameter to \lstinline|LIGHTFX_ON_OFF_TOGGLE| light f/x. \\
       & Added new definition to \lstinline|LIGHT_PARAM4| for single light f/x to assert output state beyond simple toggle on/off. \\
       & Increased the audio LUT size from 16 to 32 entries. \\
  \hline
  3.16 & Added new \lstinline|LIGHTFX_MOTOR_MODULATED| single light f/x. \\
       & Corrected the parameter definition for \lstinline|LIGHTFX_SCIFI_ENGINE_GLOW| \\
  \hline
\end{tabular}

\pagebreak

\renewcommand{\arraystretch}{1.5}
\begin{tabular}{ | c | p{13.8cm} | }
  \hline
  Rev & Change Notes  \\
  \hline
  3.17 & Added new \lstinline|COMMAND_RESTART| command \\
       & Added additional response data to the \lstinline|PFX_CMD_GET_CURRENT_STATE| command \\
       & Changed references of PFXBrick to PFx Brick to match product naming conventions \\
  \hline
  3.20  & Updated the memory map to show the addition a File Allocation Table file system and removal of the Audio LUT structure. \\
        & Added a description of a newly introduced file system applied to the flash memory.  New USB command messages have been added to interact with the file system \\
        & Deprecated the following messages associated with audio file access: \lstinline|PFX_CMD_ADD_AUDIO_FILE|, \lstinline|PFX_CMD_ADD_AUDIO_DATA|, \lstinline|PFX_CMD_ADD_AUDIO_DONE|, \lstinline|PFX_CMD_GET_AUDIO_FILE|, \lstinline|PFX_CMD_GET_AUDIO_DATA|, \lstinline|PFX_CMD_ERASE_AUDIO_LUT| \\
        & Added an error code reference for file system access commands \\
        & Deprecated the \lstinline|PFX_CMD_DIAG_LED| command \\
        & Changed the command byte value of \lstinline|PFX_CMD_GET_ICD_REV| to 0x08 from 0x00 since 0x00 seems to be a reserved report byte usage value for USB HID report packets \\
        & Changed the format of the configuration data in \lstinline|PFX_CMD_SET_CONFIG| and \lstinline|PFX_CMD_GET_CONFIG| to support optional individual brightness adjustments for each lighting channel. \\
        & Changed the format of the \lstinline|PFX_CMD_GET_STATUS| message to include new fields for USB VID and firmware build no. \\
  \hline
  3.21  & Changed the \lstinline|PFX_CMD_FILE_FORMAT_FS| message to specify different formatting modes. \\
        & Added a new request to the \lstinline|PFX_CMD_FILE_DIR| command. \\
        & Changed the \lstinline|PFX_CMD_GET_CURRENT_STATE| message to add more status parameters. \\
  \hline
  3.22  & Changed the \lstinline|PFX_CMD_FILE_GET_FS_STATE| message to report both free and empty sectors. \\
  \hline
  3.23  & Added an \lstinline|INVERT| parameter to \lstinline|LIGHTFX_SOUND_MODULATED| single light effect. \\
  \hline
  3.24  & Changed product ID and corresponding descriptors.  Added product ID reference table as an appendix. \\
        & Added new motor actions \lstinline|MOTOR_SET_SPD_TIMED|, \lstinline|MOTOR_OSCILLATE|, \lstinline|MOTOR_OSCILLATE_BIDIR|, \lstinline|MOTOR_OSCILLATE_BIDIR_WAIT|, \lstinline|MOTOR_RANDOM|, \lstinline|MOTOR_RANDOM_BIDIR|, \lstinline|MOTOR_SOUND_MODULATED| \\
        & Added new motor parameters \lstinline|DURATION| and \lstinline|MOTOR_PERIOD| \\
        & Extended the definition of the \lstinline|MOTOR_SPEED| parameter to allow for higher resolution set speed. \\
        & Added support for additional IR remote controls:  LEGO® RC Train remote, Sparkfun COM-11759 mini IR remote, and Adafruit 389 mini IR remote. These definitions expand the Event/Action LUT. \\
  \hline
\end{tabular}
\pagebreak

\pagebreak

\renewcommand{\arraystretch}{1.5}
\begin{tabular}{ | c | p{13.8cm} | }
  \hline
  Rev & Change Notes  \\
  \hline
  3.25  & Added new Bluetooth communications commands \lstinline|PFX_CMD_GET_BT_STATUS|, \lstinline|PFX_CMD_SET_BT_POWER|, \lstinline|PFX_CMD_SEND_BT_UART|, \lstinline|PFX_CMD_RECEIVE_BT_UART|  \\
  \hline
  3.30  & Changed the format of the configuration data in \lstinline|PFX_CMD_SET_CONFIG| and \lstinline|PFX_CMD_GET_CONFIG| to support new parameters. \\
        & Specification of the user-defined name has been moved from the configuration messages to two new messages: \lstinline|PFX_CMD_SET_NAME| and \lstinline|PFX_CMD_GET_NAME| \\
        & Added new section discussing the Bluetooth interface services and message format \\
        & Added an introduction to this document to reinforce the commonality of both USB and BLE interfaces for remote configuration and control \\
  \hline
  3.31  & Added a new command \lstinline|PFX_CMD_SEND_EVENT| to simulate remote control events over USB or BLE. \\
        & Expanded the definition of the \lstinline|MOTOR_PERIOD|  parameter to specify both an ON and OFF duration. \\
  \hline
  3.32  & Added the notificaiton mechanism to allow USB and BLE connected hosts to subscribe to notifications from the PFx Brick. This adds the \lstinline|PFX_CMD_SET_NOTIFICATIONS| and \lstinline|PFX_MSG_NOTIFICATION| commands to the host control interface. \\
  \hline
  3.33  & Added new \lstinline|SOUND_FX_ID:  SOUND_FX_PLAY_IDX_MOTOR| for realistic motor/prime mover sound effects based on sampled sound files indexed by changes in motor speed. \\
        & Added new new \lstinline|SOUND_FX_ID:  SOUND_FX_PLAY_RAND| to randomly playback a specified sound file continuously. \\
        & Changed the format of the configuration data in \lstinline|PFX_CMD_SET_CONFIG| and \lstinline|PFX_CMD_GET_CONFIG| to store speed boundaries between indexed motor speed sounds. \\
        & Added new \lstinline|TRAFFIC_STYLE| type "European 2". \\
  \hline
  3.34  & Added new \lstinline|TRAFFIC_STYLE| type "European 2 with pedestrian crossing" \\
        & Changed the format of the \lstinline|PFX_CMD_GET_CURRENT_STATE| return message \\
        & Added new items to the \lstinline|SOURCE1| parameter \\
        & Deprecated the namespace prefix of \lstinline|PFX_USB_CMD_| and replaced it with the more appropriate \lstinline|PFX_CMD_| prefix. All references to either namespace are considered synonymous. \\
        & Changed the format of the \lstinline|PFX_CMD_FILE_DIR| response message to include the request type in the response to simplify parsing by the host. \\
  \hline
  3.35  & Deprecated the \lstinline|PFX_CMD_GET_AUDIO_LUT_ENTRY, PFX_CMD_GET_AUDIO_CAPACITY| messages \\
        & Added new \lstinline|PFX_CMD_FILE_DIR| request type \lstinline|PFX_DIR_REQ_SET_ATTR_MASKED_ID| \\
        & Expanded the definition of the file "User Attributes" field to tag files for use with indexed motor sound samples \\
  \hline
\end{tabular}
\pagebreak

\renewcommand{\arraystretch}{1.5}
\begin{tabular}{ | c | p{13.8cm} | }
  \hline
  Rev & Change Notes  \\
  \hline
  3.36  & Changed the \lstinline|SOUNDFX_STOP| definition to stop audio playback of the file specified in \lstinline|SOUND_FILE_ID| rather than all audio playback. \\
        & Deprecated the \lstinline|PFX_CMD_GET_LAST_IR_MSG|, \lstinline|PFX_CMD_VERIFY_CONFIG|, \lstinline|PFX_CMD_VERIFY_EVENT_LUT| messages \\
        & Added new error code \lstinline|PFX_ERR_TRAP_BROWNOUT_RST| \\
        & Corrected the \lstinline|PFX_CMD_READ_I2C|, \lstinline|PFX_CMD_WRITE_I2C| messages description to conform with actual firmware implementation. \\
        & Changed the USB PID to the officially sublicensed PID from Microchip for the PFx Brick. \\
  \hline
  3.37  & Removed the 2x auxiliary flasher (on light ch. 7) for \lstinline|EVT_COMBOFX_EMCY_TWSONIC|, \lstinline|EVT_COMBOFX_EMCY_WHELEN| combo light effects \\
        & Added \lstinline|TRANSITION| parameter as \lstinline|LIGHT_PARAM5| to the \lstinline|EVT_COMBOFX_ALT_FLASH| combo light effect to specify behaviour when toggling effect \\
        & Added \lstinline|EVT_COMBOFX_DRAGSTER| combo light effect \\
        & Added \lstinline|EVT_COMBOFX_FORMULA1| combo light effect \\
        & Added \lstinline|EVT_COMBOFX_RUNWAY| combo light effect \\
        & Rename \lstinline|TRAFFIC_STYLE| "European 2" to "International" \\
        & Added new \lstinline|TRAFFIC_STYLE| "International 2" \\
        & Added new \lstinline|MOTOR_SET_SERVO| to \lstinline|MOTOR_ACTION_ID| to set servo motor position \\
        & Added new \lstinline|MOTOR_POS| motor parameter to specify servo motor position \\
        & Added new step size for servo motor increments in the \lstinline|MOTOR_STEP| parameter \\
        & Added new script language support for the PFx Brick \\
        & Added new \lstinline|COMMAND_RUN_SCRIPT| to the \lstinline|COMMAND| byte of event/action. \\
        & Added new \lstinline|PFX_CMD_RUN_SCRIPT| message to execute a script file \\
        & Added a new User Attribute for file system to mark text files for use with scripting \\
        & Added new error codes \\
        & Changed the format of the \lstinline|PFX_CMD_GET_CURRENT_STATE| message response \\
        & Added 3 new request types for the \lstinline|PFX_CMD_FILE_DIR| command message: \lstinline|PFX_DIR_REQ_GET_NAMED_FILE_ID|, \lstinline|PFX_DIR_REQ_GET_SMALL_DIR_ID|, \lstinline|PFX_DIR_REQ_GET_SMALL_DIR_IDX| \\
        & Re-organized the document by putting reference descriptions of the memory map, file system, etc. at the end \\
  \hline
\end{tabular}
\pagebreak

\renewcommand{\arraystretch}{1.5}
\begin{tabular}{ | c | p{13.8cm} | }
  \hline
  Rev & Change Notes  \\
  \hline
  3.38  & Added new file attributes for multiple gated playback sound files. \\
  \hline
\end{tabular}
\pagebreak

# Introduction

The PFx Brick injects new possibilites of animation and control for LEGO® models by offering rich capabilities for controlling Power Functions motors, diverse lighting effects and for the first time, user defined sound effects.  These features have a wide range of operational possibilies and characteristics.  In order to use and configure these features to a user's desired application, a host computer or mobile device uses a software application to make this process simple and efficient.  Fx Bricks offers the PFx App to perform this function; however, it is possible for any 3rd party to make a software application to interact with the PFx Brick as well.

In order for a host application to interact with the PFx Brick, it must connect to the PFx Brick via either the standard USB interface or optionally with a Bluetooth Low Energy (BLE) connection.  Both of these physical interfaces offer a common command and control message facility described in this Interface Control Document (ICD).

# PFx Brick USB HID Device Class

The PFx Brick firmware includes a USB HID compliant interface device for communications with USB attached hosts.  This will allow host applications to configure and update any attached PFx Brick without the need for custom device drivers.  An attached PFx Brick should automatically trigger the host operating system to enumerate the PFx Brick within the USB stack and recognize it as a USB HID compliant device with custom endpoints.

## PFx Brick Vendor and Product ID (VID/PID)

The PFx Brick unoffical vendor ID is 0x04D8 (Microchip Inc.'s registered VID)
The PFx Brick USB product ID is 0xEF74 (Microchip vendor sublicensed PID for the PFx Brick)

To find the PFx Brick using the HID API, the following code could be used:

```
device = hid_open(0x04D8, 0xEF74, NULL);
```

## Message Packet Format

USB HID message packets are exchanged via two buffers:

1. OUT endpoint 64 bytes (data from the host)
2. IN endpoint 64 bytes (data to the host)

The PFx Brick will respond to commands issued by the host using a set of customized command messages.  The format of these message packets is described in this document.  These messages facilitate a wide range of functionality and will continue to evolve over the lifecycle of the PFx Brick.

\pagebreak

# Bluetooth Low Energy

Certain PFx Brick models are fitted with a Bluetooth Low Energy (BLE) v.4.2 compliant interface.  This interface allows connected BLE hosts to control and interact with the PFx Brick identically to a USB connected host.  The messages described in this document are identically formatted for transport via USB and/or BLE.

The BLE interface on the PFx Brick is configured to operate as a "transparent UART".  That is, it provides the same functionality as a bi-directional asychronous serial interface.  The PFx Brick advertises this as a BLE compliant GATT service with characteristics assigned to transmit and receive operations.  Additionally, the PFx Brick also offers the standardized Bluetooth Device Information service GATT for detailed identification of the PFx Brick.

The BLE GATT services which the PFx Brick advertises are as follows:

\medskip
\renewcommand{\arraystretch}{1.5}
\begin{tabular}{ | l | l | l |}
  \hline
  Service UUID & \multicolumn{2}{|l|}{\ttfamily 0x180A} \\
  Service      & \multicolumn{2}{|l|}{Device Information}   \\
  \hline
          & Characteristic UUID       & \ttfamily 0x2A29 \\
          & Characteristic Descriptor & Manufacturer Name String  \\
  \cline{2-3}
          & Characteristic UUID       & \ttfamily 0x2A24 \\
          & Characteristic Descriptor & Model Number String  \\
  \cline{2-3}
          & Characteristic UUID       & \ttfamily 0x2A25 \\
          & Characteristic Descriptor & Serial Number String  \\
  \cline{2-3}
          & Characteristic UUID       & \ttfamily 0x2A27 \\
          & Characteristic Descriptor & Hardware Revision String  \\
  \cline{2-3}
          & Characteristic UUID       & \ttfamily 0x2A26 \\
          & Characteristic Descriptor & Firmware Revision String \\
  \cline{2-3}
          & Characteristic UUID       & \ttfamily 0x2A28 \\
          & Characteristic Descriptor & Software Revision String  \\
  \cline{2-3}
          & Characteristic UUID       & \ttfamily 0x2A23 \\
          & Characteristic Descriptor & System ID   \\
  \cline{2-3}
          & Characteristic UUID       & \ttfamily 0x2A2A \\
          & Characteristic Descriptor & IEEE Regulatory Certification   \\
  \hline
\end{tabular}
\normalsize

\renewcommand{\arraystretch}{1.5}
\begin{tabular}{ | l | l | l |}
  \hline
  Service UUID & \multicolumn{2}{|l|}{\ttfamily 49535343-FE7D-4AE5-8FA9-9FAFD205E455} \\
  Service      &  \multicolumn{2}{|l|}{Transparent UART}   \\
  \hline
          & Characteristic UUID       & \ttfamily 49535343-1E4D-4BD9-BA61-23C647249616 \\
          & Characteristic Descriptor & UART Receive  \\
          & Characteristic Properties & Write Without Response Write Notify Indicate  \\
  \cline{2-3}
          & Characteristic UUID       & \ttfamily 49535343-8841-43F4-A8D4-ECBE34729BB3 \\
          & Characteristic Descriptor & UART Transmit  \\
          & Characteristic Properties & Write Without Response Write  \\
  \cline{2-3}
          & Characteristic UUID       & \ttfamily 49535343-A4C8-39B3-2F49-511CFF073B7E \\
          & Characteristic Descriptor & UART Transmit (with response) \\
          & Characteristic Properties & Write Notify  \\
  \hline
\end{tabular}
\normalsize
\medskip

The PFx Brick normally advertises its presence periodically so that it can be discovered by a connecting host. Once discovered, a host can connect to the PFx Brick and ask for service descriptors for both the Device Information and Transparent UART.  It can then send and receive ICD messages with the Transparent UART service by using the UART Receive and Transmit characteristics.

\pagebreak

## Message Packet Format

BLE message packets are exchanged via two buffers which are part of the UART Transmit and Receive charactersitics.  Internally, these buffers are limited to 20 bytes each.  Therefore, the standard 64 byte ICD messages will be broken up into an integral number of 20 byte transactions to perform the transfer.  From the point of view of the PFx Brick, this process is transparent.  However, for the connecting host, extra processing will be required to assemble/disassemble ICD messages into 20 byte payloads.

Messages are sent to the PFx Brick via the `UART Transmit` service characteristic.  The format of the message block is as follows:

\medskip

\begin{bytefield}[bitwidth=\widthof{0x5B~},endianness=little]{16}
  \bitheader{0-15} \\
  \bitbox{1}{0x5B} & \bitbox{1}{0x5B} & \bitbox{1}{0x5B} & \bitbox{13}{ICD message data}\\
  \bitbox[]{16}{$\vdots$ \\[1ex]} \\
  \bitheader[lsb=51]{51-66} \\
  \wordbox{1}{ICD message data (up to 64)} \\
  \bitheader[lsb=67]{67-69} \\
  \bitbox{1}{0x5D} & \bitbox{1}{0x5D} & \bitbox{1}{0x5D} \\
\end{bytefield}

Note that all messages sent to the PFx Brick are pre-delimited with 3x `"["` characters (91 decimal, 0x5B hex) and post-delimited with 3x `"]"` characters (93 decimal, 0x5D hex).

The PFx Brick always sends a response to every transmitted message it receives.  These responses are sent as raw data bytes without any pre or post delimiters in exactly the same format as they would be for USB connected hosts.

\pagebreak

# Host Command Messages

The USB HID class supports the exchange of message buffers between the host and a device of up to 64 bytes. The PFx Brick message definition consists of various command messages which originate from the host.  The structure of these messages is as follows:
\bigskip
\begin{bytefield}[bitwidth=\widthof{0x03~},endianness=little]{16}
  \bitheader{0-15} \\
  \bitbox{1}{\tiny CMD Byte} & \bitbox{15}{ Data bytes 0-14 } \\
  \bitbox[]{16}{$\vdots$ \\[1ex]} \\
  \bitheader[lsb=48]{48-63} \\
  \wordbox{1}{ Data bytes 49-62} \\
\end{bytefield}

The CMD byte is a numeric literal which specifies the command.  A command message may have up to 63 additional data bytes associated with it depending on its purpose.  A description of each command is given below along with the format of a device responses if applicable.  The device response will prefix its response in byte 0 with the CMD byte xor-ed with 0x80, i.e. it will send the command byte back with the MSB set to '1'.

The following tables show the host CMD bytes grouped by functional category. Also shown is the applicability and/or support of each message within the different software operational contexts. For example, the bootloader application context will not have support for every message since it has limited resources to for processing.

\medskip

**Operation and Configuration Commands**

\renewcommand{\arraystretch}{1.5}
\begin{tabular}{ | c | p{7.7cm} | c | c | c | }
  \hline
      &                                   & \multicolumn{3}{|c|}{Context} \\ \cline{3-5}
  CMD & Nmemonic                          & Firmware & Bootloader & Host App  \\
  \hline
  0x08 & \lstinline|PFX_CMD_GET_ICD_REV|          & y        & y          & y \\
  0x01 & \lstinline|PFX_CMD_GET_STATUS|            & y        & y          & y \\
  0x02 & \lstinline|PFX_CMD_SET_FACTORY_DEFAULTS| & y        &            & y \\
  0x03 & \lstinline|PFX_CMD_GET_CONFIG|            & y        &            & y \\
  0x04 & \lstinline|PFX_CMD_SET_CONFIG|            & y        &            & y \\
  0x06 & \lstinline|PFX_CMD_GET_CURRENT_STATE|    & y        &            & y \\
  0x07 & \lstinline|PFX_CMD_GET_NAME|              & y        &            & y \\
  0x09 & \lstinline|PFX_CMD_SET_NAME|              & y        &            & y \\
  \hline
\end{tabular}
\normalsize
\medskip
\pagebreak

**Event/Action LUT Commands**

\renewcommand{\arraystretch}{1.5}
\begin{tabular}{ | c | p{7.7cm} | c | c | c | }
  \hline
      &                                   & \multicolumn{3}{|c|}{Context} \\ \cline{3-5}
  CMD & Nmemonic                          & Firmware & Bootloader & Host App  \\
  \hline
  0x11 & \lstinline|PFX_CMD_GET_EVENT_ACTION|          & y        &            & y \\
  0x12 & \lstinline|PFX_CMD_SET_EVENT_ACTION|          & y        &            & y \\
  0x13 & \lstinline|PFX_CMD_TEST_ACTION|                & y        &            & y \\
  0x15 & \lstinline|PFX_CMD_SEND_EVENT|                 & y        &            & y \\
  \hline
\end{tabular}
\normalsize
\medskip

**Audio Commands**

\renewcommand{\arraystretch}{1.5}
\begin{tabular}{ | c | p{7.7cm} | c | c | c | }
  \hline
      &                                   & \multicolumn{3}{|c|}{Context} \\ \cline{3-5}
  CMD & Nmemonic                          & Firmware & Bootloader & Host App  \\
  \hline
  0x20 & \lstinline|PFX_CMD_INC_VOLUME|            & y        &            & y \\
  0x21 & \lstinline|PFX_CMD_DEC_VOLUME|            & y        &            & y \\
  0x2A & \lstinline|PFX_CMD_SET_AUDIO_EQ|         & y        &            & y \\
  \hline
\end{tabular}
\normalsize
\medskip

**Service Commands**

\renewcommand{\arraystretch}{1.5}
\begin{tabular}{ | c | p{7.7cm} | c | c | c | }
  \hline
      &                                   & \multicolumn{3}{|c|}{Context} \\ \cline{3-5}
  CMD & Nmemonic                          & Firmware & Bootloader & Host App  \\
  \hline
  0x30 & \lstinline|PFX_CMD_LOAD_FIRMWARE_FILE|  & y        & y          & y \\
  0x31 & \lstinline|PFX_CMD_LOAD_FIRMWARE_DATA|  & y        & y          & y \\
  0x32 & \lstinline|PFX_CMD_LOAD_FIRMWARE_DONE|  & y        & y          & y \\
  0x34 & \lstinline|PFX_CMD_READ_BOOTCONFIG|      &          & y          &  \\
  0x37 & \lstinline|PFX_CMD_REBOOT|                & y        & y          & y \\
  \hline
\end{tabular}
\normalsize

\pagebreak

**File System Access Commands**

\renewcommand{\arraystretch}{1.5}
\begin{tabular}{ | c | p{7.7cm} | c | c | c | }
  \hline
      &                                         & \multicolumn{3}{|c|}{Context} \\ \cline{3-5}
  CMD & Nmemonic                                & Firmware & Bootloader & Host App  \\
  \hline
  0x40 & \lstinline|PFX_CMD_FILE_OPEN|              & y        &            &  y \\
  0x41 & \lstinline|PFX_CMD_FILE_CLOSE|             & y        &            &  y \\
  0x42 & \lstinline|PFX_CMD_FILE_READ|              & y        &            &  y \\
  0x43 & \lstinline|PFX_CMD_FILE_WRITE|             & y        &            &  y \\
  0x44 & \lstinline|PFX_CMD_FILE_SEEK|              & y        &            &  y \\
  0x45 & \lstinline|PFX_CMD_FILE_DIR|               & y        &            &  y \\
  0x46 & \lstinline|PFX_CMD_FILE_REMOVE|            & y        &            &  y \\
  0x47 & \lstinline|PFX_CMD_FILE_FORMAT_FS|        & y        &            &  y \\
  0x48 & \lstinline|PFX_CMD_FILE_GET_FS_STATE|    & y        &            &  y \\
  0x4B & \lstinline|PFX_CMD_RUN_SCRIPT|             & y        &            &  y \\
  \hline
\end{tabular}
\normalsize
\medskip

**Bluetooth Interface Commands**

\renewcommand{\arraystretch}{1.5}
\begin{tabular}{ | c | p{7.7cm} | c | c | c | }
  \hline
      &                                         & \multicolumn{3}{|c|}{Context} \\ \cline{3-5}
  CMD & Nmemonic                                & Firmware & Bootloader & Host App  \\
  \hline
  0x50 & \lstinline|PFX_CMD_GET_BT_STATUS|            & y        &            &   \\
  0x51 & \lstinline|PFX_CMD_SET_BT_POWER|             & y        &            &   \\
  0x52 & \lstinline|PFX_CMD_SEND_BT_UART|             & y        &            &   \\
  0x53 & \lstinline|PFX_CMD_RECEIVE_BT_UART|          & y        &            &   \\
  \hline
\end{tabular}
\normalsize
\medskip

**Notification Commands**

\renewcommand{\arraystretch}{1.5}
\begin{tabular}{ | c | p{7.7cm} | c | c | c | }
  \hline
      &                                         & \multicolumn{3}{|c|}{Context} \\ \cline{3-5}
  CMD & Nmemonic                                & Firmware & Bootloader & Host App  \\
  \hline
  0x60 & \lstinline|PFX_CMD_SET_NOTIFICATIONS|           & y        &            & y  \\
  0x61 & \lstinline|PFX_MSG_NOTIFICATION|                 & y        &            & y  \\
  \hline
\end{tabular}
\normalsize
\medskip

\pagebreak

**Low Level Test/Debug Commands**

\renewcommand{\arraystretch}{1.5}
\begin{tabular}{ | c | p{7.7cm} | c | c | c | }
  \hline
      &                                   & \multicolumn{3}{|c|}{Context} \\ \cline{3-5}
  CMD & Nmemonic                          & Firmware & Bootloader & Host App  \\
  \hline
  0x70 & \lstinline|PFX_CMD_STATUS_LED|           & y        &            &  \\
  0x72 & \lstinline|PFX_CMD_WRITE_SPI|            & y        &            &  \\
  0x73 & \lstinline|PFX_CMD_READ_SPI|             & y        &            &  \\
  0x74 & \lstinline|PFX_CMD_WRITE_I2C|            & y        &            &  \\
  0x75 & \lstinline|PFX_CMD_READ_I2C|             & y        &            &  \\
  0x76 & \lstinline|PFX_CMD_READ_FLASH|           & y        &            &  \\
  0x77 & \lstinline|PFX_CMD_GET_IRRX_STATUS|     & y        &            &  \\
  \hline
\end{tabular}
\normalsize

\pagebreak

## `PFX_CMD_GET_ICD_REV`

This command queries the revision number of the Interface Control Document/Specification (ICD) that the PFx Brick supports.  The returned version number will correspond to the revision number of this document.  This will give both firmware and host software development a common reference point for determining compatibility.  The ICD revision number is independent of both the firmware revision and host software revision/build state.  It is possible that several consecutive versions of firmware may support a common revision of ICD.

**Host command packet:**

\begin{bytefield}[bitwidth=\widthof{SILENT~},endianness=little]{5}
  \bitheader{0-4} \\
  \bitbox{1}{0x08} & \bitbox{1}{0x60} & \bitbox{1}{0x0D} & \bitbox{1}{0x01} & \bitbox{1}{Silent} \\
\end{bytefield}

**Device response packet:**

\begin{bytefield}[bitwidth=\widthof{Status~},endianness=little]{3}
  \bitheader{0-2} \\
  \bitbox{1}{0x88} & \bitbox{2}{Revision} \\
\end{bytefield}

The ICD revision is encoded in BCD (binary coded decimal).  The major code is in the first byte (byte 1) and the minor code is in the second byte (byte 2), e.g. v.3.14 would be encoded as `0x03 0x14`.

The `Silent` flag can be used to disable the blink indication of the PFx Brick status LED when responding to this message.  Note that it only disables the blink indication for this message--all other messages will blink the status LED as usual.  A value of 1 disables the blink notificaiton, all other values will show the blink indication.  This flag is included so that a host can periodically poll the PFx Brick in order to maintain its connection status, without incurring visually distracting status LED blink activity.

\pagebreak

## `PFX_CMD_GET_STATUS`

This command queries the fundamental operational state of the PFx Brick. Normally, the PFx Brick is running its main application firmware.  However, the PFx Brick is designed to have its firmware upgraded in the field by the end user with a host PC application.  This functionality requires a permanent firmware component called a *bootloader*.  The bootloader resides permanently in the PFx Brick and is executed after reset or a power cycle.  The bootloader checks to see if valid application firmware has been loaded onto the PFx Brick.  If present, it immediately transfers execution to the application firmware.  However, if no application firmware is present or corrupted, the bootloader continues to operate the PFx Brick in *Service* mode.  This mode has just enough functionality to allow a USB host to load a new application firmware binary image.  If successfully loaded, the PFx Brick will restart and then launch the new firmware image.

Additionally, the main application firmware also allows the host to load a new firmware image. In actual fact, the firmware "stages" the new firmware in flash memory, and if successfully loaded, will reboot the PFx Brick.  Upon reboot, the bootloader will detect a new "staged" firmware image and attempt to replace the existing firmware with the new one.  If successful, the new firmware will execute.  If unsuccessful, then at least the PFx Brick will remain in *Service* mode so that another attempt at loading firmware can be made.

One of the goals of the `PFX_CMD_GET_STATUS` command is simply to determine if the PFx Brick is operating normally with its main application firmware or is running the bootloader in Service mode.  Based on this determination, the host will know which workflows are permissible. For example, if operating in Service mode, then most USB host commands will simply not work.  The only actions that should be exposed to the user are for selecting and loading a new application firmware image.

Lastly, the `PFX_CMD_GET_STATUS` command can be used to determine the specific PFx Brick part number and serial number.  This information will be useful for determining the device capabilities, e.g. number of motor channels, storage capacity, etc. as well determining which firmware is compatible with the device.  Furthermore, a 24 character product descriptor is included which definitively describes the product identity.  Note that the part number and product descriptor are *different* than the USB PID (Product ID).  One USB PID may in fact be used to represent a family of PFx Brick procucts.  Rather than exhaust the limited availability of USB PID numbers, the Part Number/Product Descriptor pair can be used to detemine the specific PFx Brick type that is connected.

**Host command packet:**

\begin{bytefield}[bitwidth=\widthof{0xAA~},endianness=little]{8}
  \bitheader{0-7} \\
  \bitbox{1}{0x01} & \bitbox{1}{0xA5} & \bitbox{1}{0x5A} & \bitbox{1}{0x6E} & \bitbox{1}{0x40} & \bitbox{1}{0x54} & \bitbox{1}{0xA4} & \bitbox{1}{0xE5} \\
\end{bytefield}

**Device response packet:**

\begin{bytefield}[bitwidth=\widthof{STatus~},endianness=little]{13}
  \bitheader{0-12} \\
  \bitbox{1}{0x81} & \bitbox{1}{Status} & \bitbox{1}{Error} & \bitbox{2}{USB \\ VID} & \bitbox{2}{USB \\ PID} & \bitbox{2}{Part \\ Number} & \bitbox{4}{Serial \\ Number}  \\
\end{bytefield}

\begin{bytefield}[endianness=little,bitwidth=0.042\linewidth]{24}
  \bitheader[lsb=13]{13-36} \\
  \wordbox{1}{Left justified 24 character product descriptor UTF8 encoded}\\
\end{bytefield}

\begin{bytefield}[bitwidth=\widthof{Status~},endianness=little]{4}
  \bitheader[lsb=37]{37-40} \\
  \bitbox{2}{Firmware \\ Version} & \bitbox{2}{Firmware \\ Build No.} \\
\end{bytefield}

\pagebreak

**Status Codes**
\medskip

\renewcommand{\arraystretch}{1.5}
\begin{tabular}{ | c | l | p{7.5cm} | }
  \hline
  Status & Code & Description \\
  \hline
  0x00 & \lstinline|PFX_STATUS_NORMAL|           & if the PFx Brick is running its main application firmware, i.e. normal operation \\
  0x33 & \lstinline|PFX_STATUS_NORMAL_PENDING| & PFx Brick is running in normal mode with a new application firmware image loaded into staging and pending upgrade \\
  0x55 & \lstinline|PFX_STATUS_SERVICE|          & PFx Brick is running in Service mode with no errors, i.e. a typical state for a new uninitialized PFx Brick \\
  0x53 & \lstinline|PFX_STATUS_SERVICE_PENDING| & PFx Brick is running in Service mode with a new application firmware image loaded into staging and pending upgrade \\
  0x5B & \lstinline|PFX_STATUS_SERVICE_BUSY|    & Running in Service mode, busy performing firmware upgrade \\
  \hline
\end{tabular}
\medskip

**Error Codes**
\medskip

\renewcommand{\arraystretch}{1.5}
\begin{tabular}{ | c | l | p{7.0cm} | }
  \hline
  Error & Code & Description \\
  \hline
  0x00 & \lstinline|PFX_ERR_NONE|                    & no errors  \\
  0x04 & \lstinline|PFX_ERR_SPKR_SHORTCIR_FAULT|   & Short circuit detected on speaker output \\
  0x06 & \lstinline|PFX_ERR_TRANSFER_CRC_MISMATCH| & Error loading firmware from host into staging memory space \\
  0x08 & \lstinline|PFX_ERR_DAC_OVERTEMP_FAULT|    & Overtemperature condition \\
  0x0B & \lstinline|PFX_ERR_BLE_FAULT|              & Bluetooth radio module fault \\
  0x80 & \lstinline|PFX_ERR_UPGRADE_FAIL|           & Error copying staged firmware into active operational flash program memory space \\
  0x0A & \lstinline|PFX_ERR_TRAP_BROWNOUT_RST|     & Reset error due to brownout power condition  \\
  0x10 & \lstinline|PFX_ERR_TRAP_CONFLICT|          & Reset error due a trap conflict  \\
  0x20 & \lstinline|PFX_ERR_TRAP_ILLEGAL_OPCODE|   & Reset error due to illegal OP code execution \\
  0x40 & \lstinline|PFX_ERR_TRAP_CONFIG_MISMATCH|  & Reset error due configuration mismatch \\
  \hline
\end{tabular}
\medskip

\pagebreak

**USB VID/PID**
\medskip

The USB VID (Vendor ID) and PID (Product ID) is part of the standard USB assigned VID/PID pair used to enumerate USB devices.

**Serial Number**
\medskip

The serial number is 4 bytes and each PFx Brick will be assigned a unique cryptographically random serial number.  The serial number may originate from a unique ID register value embedded in a flash memory device (if available) or it may be assigned by the bootloader after it has been installed.

**Firmware Version / Build No.**
\medskip

The firmware version number occupies 2 bytes.  The version number is BCD encoded with first byte (byte 37) representing the major version number and the second byte (byte 38) representing the minor version number, e.g. v.3.14 would be encoded as 0x03 0x14.  The Build No. complements the version number by indicating a specific build within a series of releases.  It is encoded as a verbatim 16-bit value.

\pagebreak

**Part Number / Part Descriptors**
\medskip

The Part Number is a unique 2-byte value which corresponds to a distinct SKU product. Each product Part Number has a corresponding Product Descriptor.  The descriptor is an unambiguous product name encoded as UTF-8 character strings.

\renewcommand{\arraystretch}{1.5}
\begin{tabular}{ | p{1.3cm} | l | p{8.8cm} | }
  \hline
  Part Number   & Product Descriptor       & Description \\
  \hline
  0x1201        & PFx Brick alpha           & First pre-production prototype PFx Brick with 2x motor channels (using the DRV8839), 8x light channel with discrete pico light connectors, and sound. \\
  0x1202        & PFx Brick beta            & Second pre-production prototype PFx Brick with 2x motor channels (using the DRV8835), 8x light channels on the standard 10-pin lighting dock connector, and sound. \\
  0x1203        & PFx Brick gamma          & Third pre-production prototype with 2x motor channels (using the DRV8833), 8x light channels on the standard 10-pin lighting dock connector, and sound. \\
  0x1204        & PFx Brick delta IR       & Fourth pre-production prototype with 2x motor channels (using the DRV8833), 8x light channels on the standard 10-pin lighting dock connector, and sound. \\
  0x9204        & PFx Brick delta          & Fourth pre-production prototype with 2x motor channels (using the DRV8833), Bluetooth interface, 8x light channels on the standard 10-pin lighting dock connector, and sound. \\
  0x2204        & \textbf{PFx Brick IR 4 MB}  & Production version of the 4 MB PFx Brick IR with 2x motor channels, 8x light channels, and sound. \\
  0x2208        & \textbf{PFx Brick IR 8 MB}  & 8 MB PFx Brick IR \\
  0x2216        & \textbf{PFx Brick IR 16 MB}  & 16 MB PFx Brick IR \\
  0xA204        & \textbf{PFx Brick 4 MB}  & Production version of the 4 MB PFx Brick with Bluetooth interface, 2x motor channels, 8x light channels, and sound. \\
  0xA208        & \textbf{PFx Brick 8 MB}  & 8 MB PFx Brick \\
  0xA216        & \textbf{PFx Brick 16 MB}  & 16 MB PFx Brick \\
  \hline
  0x1701        & PFXLite alpha      & Pre-production economy PFx Brick with light f/x only (8x channels with 10-pin dock connector). It has no plastic enclosure, but has stud mounting holes for integration into a model. \\
  0x2702        & \textbf{PFXLite}   & Production economy PFx Brick with light f/x only. \\
  \hline
  0x1401        & PFx Brick Pro alpha       & Pre-production PFx Brick with 4x motor channels, 8x light channels, and sound. \\
  0x2404        & \textbf{PFx Brick Pro 4 MB}    & Production 4 MB PFx Brick with 4x motor channels, 8x light channels, and sound. \\
  0x2408        & \textbf{PFx Brick Pro 8 MB}   & 8 MB PFx Brick Pro \\
  0x2410        & \textbf{PFx Brick Pro 16 MB}  & 16 MB PFx Brick Pro \\
  \hline
\end{tabular}

\pagebreak


## `PFX_CMD_SET_FACTORY_DEFAULTS`

Resets the global configuration, event look-up table and file system with factory default values. This command will overwrite the current configuration of the PFx Brick and cannot be undone.

**Host command packet:**

\begin{bytefield}[bitwidth=\widthof{0xAA~},endianness=little]{8}
  \bitheader{0-7} \\
  \bitbox{1}{0x02} & \bitbox{1}{0xAA} & \bitbox{1}{0x55} & \bitbox{1}{0xDE} & \bitbox{1}{0xAD} & \bitbox{1}{0xBE} & \bitbox{1}{0xEF} & \bitbox{1}{0x02} \\
\end{bytefield}

**Device response packet:**

\begin{bytefield}[bitwidth=\widthof{0xAA~},endianness=little]{1}
  \bitheader{0} \\
  \bitbox{1}{0x82} \\
\end{bytefield}

\pagebreak

## `PFX_CMD_GET_CONFIG`

Retrieves global configuration data from the PFx Brick.

**Host command packet:**

\begin{bytefield}[bitwidth=\widthof{BrigHTNESS~},endianness=little]{1}
  \bitheader{0} \\
  \bitbox{1}{0x03} \\
\end{bytefield}

**Device response packet:**

\begin{bytefield}[bitwidth=\widthof{BrigHTNESS~},endianness=little]{7}
  \bitheader{0-6} \\
  \bitbox{1}{0x83} & \bitbox{1}{Light Ch 1 Brightness} & \bitbox{1}{Light Ch 2 Brightness} & \bitbox{1}{Light Ch 3 Brightness} & \bitbox{1}{Light Ch 4 Brightness} & \bitbox{1}{Light Ch 5 Brightness} & \bitbox{1}{Light Ch 6 Brightness} \\
\end{bytefield}

\begin{bytefield}[bitwidth=\widthof{brightness~},endianness=little]{8}
  \bitheader[lsb=7]{7-14} \\
  \bitbox{1}{Notch Count} & \bitbox{1}{Notch 1-2 Bound} & \bitbox{1}{Notch 2-3 Bound} & \bitbox{1}{Notch 3-4 Bound} & \bitbox{1}{Notch 4-5 Bound} & \bitbox{1}{Notch 5-6 Bound} & \bitbox{1}{Notch 6-7 Bound} & \bitbox{1}{Notch 7-8 Bound} \\
\end{bytefield}

\begin{bytefield}[endianness=little,bitwidth=0.0527\linewidth]{11}
  \bitheader[lsb=15]{15-25} \\
  \wordbox{1}{Reserved}\\
\end{bytefield}

\begin{bytefield}[bitwidth=\widthof{BBBIRIGHTNESS~},endianness=little]{5}
  \bitheader[lsb=26]{26-30} \\
  \bitbox{1}{IR Auto Off} & \bitbox{1}{BLE Auto Off} & \bitbox{1}{\footnotesize BLE \\ Disconnect Motor} & \bitbox{1}{\footnotesize BLE \\ Advertisement Power} & \bitbox{1}{\footnotesize BLE \\ Session Power}  \\
\end{bytefield}

\begin{bytefield}[bitwidth=\widthof{BrigHTNESS~},endianness=little]{7}
  \bitheader[lsb=31]{31-37} \\
   \bitbox{1}{Light Ch 7 Brightness} & \bitbox{1}{Light Ch 8 Brightness} & \bitbox{1}{PF Light A Brightness} & \bitbox{1}{PF Light B  Brightness} & \bitbox{1}{Audio Bass} & \bitbox{1}{Audio Treble} & \bitbox{1}{PFX Settings} \\
\end{bytefield}

\begin{bytefield}[bitwidth=\widthof{BrigHTNESS~},endianness=little]{6}
  \bitheader[lsb=38]{38-43} \\
  \bitbox{1}{Motor A Config} & \bitbox{1}{Motor A \\ vMin} & \bitbox{1}{Motor A \\ vMid} & \bitbox{1}{Motor A \\ vMax} & \bitbox{1}{Motor A \\ Accel} & \bitbox{1}{Motor A \\ Decel} \\
\end{bytefield}

\begin{bytefield}[bitwidth=\widthof{BrigHTNESS~},endianness=little]{6}
  \bitheader[lsb=44]{44-49} \\
  \bitbox{1}{Motor B Config} & \bitbox{1}{Motor B \\ vMin} & \bitbox{1}{Motor B \\ vMid} & \bitbox{1}{Motor B \\ vMax} & \bitbox{1}{Motor B \\ Accel} & \bitbox{1}{Motor B \\ Decel} \\
\end{bytefield}

\begin{bytefield}[bitwidth=\widthof{BrigHTNESS~},endianness=little]{6}
  \bitheader[lsb=50]{50-55} \\
  \bitbox{1}{Motor C Config} & \bitbox{1}{Motor C \\ vMin} & \bitbox{1}{Motor C \\ vMid} & \bitbox{1}{Motor C \\ vMax} & \bitbox{1}{Motor C \\ Accel} & \bitbox{1}{Motor C \\ Decel} \\
\end{bytefield}

\begin{bytefield}[bitwidth=\widthof{BrigHTNESS~},endianness=little]{6}
  \bitheader[lsb=56]{56-61} \\
  \bitbox{1}{Motor D Config} & \bitbox{1}{Motor D \\ vMin} & \bitbox{1}{Motor D \\ vMid} & \bitbox{1}{Motor D \\ vMax} & \bitbox{1}{Motor D \\ Accel} & \bitbox{1}{Motor D \\ Decel} \\
\end{bytefield}

\begin{bytefield}[bitwidth=\widthof{BrigHTNESS~},endianness=little]{2}
  \bitheader[lsb=62]{62-63} \\
  \bitbox{1}{Default Volume} & \bitbox{1}{Default Brightness} \\
\end{bytefield}

\pagebreak

**Light Ch Brightness**

These bytes were formally reserved and are now used to represent individual startup brightness values for each light channel.  This includes 8x brightness values for the dedicated light output ports and 2x brightness values for lights attached to the PF Motor channel connectors A and B.  Setting individual brightness values is optional.  Normally, all channels are set to the master `Default Brightness` value in byte 63.  However, if `Default Brightness` is set to zero (0x00), then the individual brightness values for each channel will apply.  Having individual default brightness control is useful for situations where relative brightness for each light output is mismatched due to installation, colour, electrical resistance, etc.

**Notch Count**

The `Notch Count` value specifies how many power "notches" or levels are to be used for simulated engine sound Fx which are indexed by motor speed.  This value is only relevant when used with the `SOUND_FX_PLAY_IDX_MOTOR` sound Fx.  When this sound Fx is used, up to 8 distinct power levels or notches can be represented by sound files.  The selection of a power notch is defined by a desired motor channel's speed.  The boundaries between adjacent power notches represent a monotonically changing motor speed.  The `Notch 1-2 Bound` represents the motor speed which defines boundary between power notch 1 and 2 and so on.  Typically, Notch 1 represents "idle" or minimum motor speed and `Notch Count` represents maximum motor speed.  Typically the boundaries between power notches represent evenly spaced intervals of motor speed.

**IR Auto Off**

The infrared sensor and IR message processing can be configured to automatically turn off and be disabled after a specified interval of time with no activity.  This can be a useful feature to either save power or to increase the immunity of the PFx Brick to unintended IR messages.

```
0x00 = Never, IR sensor always enabled
0x01 = Automatic disable after 1 minute of no activity
0x02 = Automatic disable after 5 minutes of no activity
0x03 = Disable immediately after startup (always disabled)
```

**BLE Auto Off**

The Bluetooth interface can be configured to automatically turn off and be disabled after a specified interval of time with no activity.  This can be a useful feature to either save power or reduce radio spectrum congestion.

```
0x00 = Never, BLE interface always enabled
0x01 = Automatic disable after 1 minute of no activity
0x02 = Automatic disable after 5 minutes of no activity
0x03 = Disable immediately after startup (always disabled)
```

**BLE Disconnect Motor**

If a PFx Brick is being remotely operated by a Bluetooth connected host, there is always the possibility of unintentional disconnection of the radio link due to interference, radio range, or other factors. When a disconnection occurs, the user has no means of controlling a model until reconnected.  In the case of models which are mobile such as trains or cars, this could lead to a "run-away" model situation.  In order to avoid this scenario, the PFx Brick can be configured to either continue operating the motors normally or turn off all motors in the event of a BLE disconnection.

```
0x00 = Continue to operate motors normally
0x01 = Turn off all motor channels on a BLE disconnection event
```

**BLE Advertisement Power**
**BLE Session Power**

The transmitter power of the BLE radio can be adjusted in order to trade-off energy consumption and radio range performance. The BLE radio operates in two basic modes: Advertisement and Connected Session.  During Advertisement, the BLE radio will periodically transmit advertisement signals notifying nearby hosts that the PFx Brick is on and available for connection.  During a connected session, the BLE radio is used to send messages between the PFx Brick and a connected host for remote control.  The transmitter power of both of these modes can be adjusted to trade off energy usage and radio performance.

```
Range between 0x00~0x05 where
0x00 = Maximum transmitter power
0x05 = Minimum transmitter power
```

**Audio Bass/Treble**

The audio subsystem will have adjustable spectral EQ for bass and treble.  The level is specified as a 2's complement signed 8-bit value relative to a nominal value of 0 dB.  The adjustable range is therefore -128 to +127 dB; however, in practice it is limited to -20 to +20 dB.

\smallskip

**PFX Settings**

The PFx Brick has some device specific settings which can be customized by the user.  They are encoded as bitfields within the `PFX Settings` byte as follows:
\bigskip

\begin{bytefield}[bitwidth=\widthof{Reserved~},endianness=big]{8}
  \bitheader{0-7} \\
  \bitbox{1}{Reserved} & \bitbox{1}{Audio DRC} & \bitbox{2}{Lockout/sleep mode} & \bitbox{2}{Auto power down mode} & \bitbox{1}{Volume beep} & \bitbox{1}{Status LED} \\
\end{bytefield}

where

```
Status LED    :  0 = Normally on, wink off with activity
                 1 = Normally off, wink on with activity
Volume Beep   :  0 = No beep sound with change in audio volume
                 1 = Audible beep sound with every change in audio volume
Auto Power
Down Mode     : 00 = No automatic power down
                01 = Automatic power down/sleep after 30 minutes
                10 = Automatic power down/sleep after 60 minutes
                11 = Automatic power down/sleep after 3 hours
Lockout/Sleep
Mode          : 00 = Lockout/sleep disabled
                01 = Toggle lockout/sleep with 4-double taps on channel 1 only
                10 = Toggle lockout/sleep with 4-double taps on any channel
                11 = synonymous with 00 (disabled)

Audio DRC     :  0 = Automatic audio Dynamic Range Control (DRC) off
                 1 = Automatic audio DRC on

```

\pagebreak

**Motor Configuration**
Each motor output on the PFx Brick can be customized by the user for different motor speed and momentum behaviour.  These settings apply to each specific motor output connector channel on the PFx Brick.  Up to 4x motor channels (A,B,C,D) can be configured; however, the initial version of the PFx Brick has only 2x motor channels fitted (A & B).  The settings for channels C & D are placeholders for future 4x channel PFx Bricks.

The motor configuration byte is defined as follows:
\medskip

\begin{bytefield}[rightcurly=.,rightcurlyspace=0pt,bitwidth=\widthof{Torque~}]{8}
  \bitheader{0-7} \\
  \bitbox{5}{Reserved} & \bitbox{1}{TLG Mode} & \bitbox{1}{Torque Comp} & \bitbox{1}{Invert} \\
\end{bytefield}

where

```
Invert      : 0 = Motor polarity normal
              1 = Motor polarity reversed
              Motors with the same polarity will rotate in the same direction.
Torque Comp : 0 = High frequency PWM at all speeds (default)
              1 = Low frequency PWM for starting motor with additional torque
                  High freq PWM at all other speeds
TLG Mode    : 0 = Normal high resolution PWM motor control (default)
              1 = Lego IR receiver compatibility mode. Motor driven with low
                  frequency 1 kHz PWM with 7 speed steps in each direction
                  emulating the operation of the Lego IR receiver.
```

**vMin, vMid, vMax**

These parameters define the shape of the motor speed curve.  Normally, motor speed is set directly proportional to user commanded speed (linear).  However, this relationship can be modified with alternative speed curves.  Examples include parabolically increasing speed curves with more resolution at slower speeds or inverse parabolic curves with rapid initial acceleration.  The shape of the curve is a smooth spline-fitted curve between points `vMin`, `vMid`, and `vMax`.  `vMin` should be chosen to represent the minimum starting speed of the motor and `vMax` should represent the maximum applied motor speed.  Speed values are absolute values between 0 (no speed) up to 255 (maximum speed).  This allows the motor to be "clamped" to a maximum speed below the absolute full voltage maximum (255).  `vMid` can be chosen to represent the shape of the speed curve.  If `vMid` is midway between `vMin` and `vMax`, then the curve will be a standard linear straight line through all three points.  If `vMid` is biased toward `vMin`, then the curve will be approximately parabolic with emphasis on low-speed control.  Conversely, if `vMid` is biased towards `vMax`, then the speed curve will have an initial rapid increase of speed up to a asymptopic convergence to `vMax`.

**Acceleration/Deceleration**

The rate at which the user commanded speed and actual motor speed is applied is normally instantaneous.  However, momentum or inertia effects can be simulated by setting the acceleration and deceleration factors for increasing and decreasing speed behaviour respectively.  For example, a motorized train could have realistic slow acceleration from start and progressive smooth braking to a stop.  For no accel/decel effects, these values can be set to 0.  Accel/decel factors can be specified from a minimum of 1 up to 255 representing acceleration/deceleration in units of TBD/s.

\pagebreak

**Default Volume**

Configuration for the default audio volume to apply after power up.  The valid range is 0x00~0xFF corresponding to minimum and maximum volume respectively.

**Default Brightness**

Configuration for the default global light output brightness to apply after power up. The valid range is 0x00~0xFF corresponding to minimum and maximum brightness respectively.

\pagebreak

## `PFX_CMD_SET_CONFIG`

Overwrites the PFx Brick global configuration data.  The PFx Brick will store the new configuration to flash memory.

**Host command packet:**

\begin{bytefield}[bitwidth=\widthof{BrigHTNESS~},endianness=little]{1}
  \bitheader{0} \\
  \bitbox{1}{0x04} \\
\end{bytefield}

\begin{bytefield}[bitwidth=\widthof{brightness~},endianness=little]{8}
  \bitheader[lsb=1]{1-8} \\
  \bitbox{1}{Notch Count} & \bitbox{1}{Notch 1-2 Bound} & \bitbox{1}{Notch 2-3 Bound} & \bitbox{1}{Notch 3-4 Bound} & \bitbox{1}{Notch 4-5 Bound} & \bitbox{1}{Notch 5-6 Bound} & \bitbox{1}{Notch 6-7 Bound} & \bitbox{1}{Notch 7-8 Bound} \\
\end{bytefield}

\begin{bytefield}[endianness=little,bitwidth=0.0527\linewidth]{11}
  \bitheader[lsb=9]{9-19} \\
  \wordbox{1}{Reserved}\\
\end{bytefield}

\begin{bytefield}[bitwidth=\widthof{BBBIRIGHTNESS~},endianness=little]{5}
  \bitheader[lsb=20]{20-24} \\
  \bitbox{1}{IR Auto Off} & \bitbox{1}{BLE Auto Off} & \bitbox{1}{\footnotesize BLE \\ Disconnect Motor} & \bitbox{1}{\footnotesize BLE \\ Advertisement Power} & \bitbox{1}{\footnotesize BLE \\ Session Power}  \\
\end{bytefield}

\begin{bytefield}[bitwidth=\widthof{BrigHTNESS~},endianness=little]{3}
  \bitheader[lsb=25]{25-27} \\
  \bitbox{1}{Audio Bass} & \bitbox{1}{Audio Treble} & \bitbox{1}{PFX Settings} \\
\end{bytefield}

\begin{bytefield}[bitwidth=\widthof{BrigHTNESS~},endianness=little]{6}
  \bitheader[lsb=28]{28-33} \\
  \bitbox{1}{Motor A Config} & \bitbox{1}{Motor A \\ vMin} & \bitbox{1}{Motor A \\ vMid} & \bitbox{1}{Motor A \\ vMax} & \bitbox{1}{Motor A \\ Accel} & \bitbox{1}{Motor A \\ Decel} \\
\end{bytefield}

\begin{bytefield}[bitwidth=\widthof{BrigHTNESS~},endianness=little]{6}
  \bitheader[lsb=34]{34-39} \\
  \bitbox{1}{Motor B Config} & \bitbox{1}{Motor B \\ vMin} & \bitbox{1}{Motor B \\ vMid} & \bitbox{1}{Motor B \\ vMax} & \bitbox{1}{Motor B \\ Accel} & \bitbox{1}{Motor B \\ Decel} \\
\end{bytefield}

\begin{bytefield}[bitwidth=\widthof{BrigHTNESS~},endianness=little]{6}
  \bitheader[lsb=40]{40-45} \\
  \bitbox{1}{Motor C Config} & \bitbox{1}{Motor C \\ vMin} & \bitbox{1}{Motor C \\ vMid} & \bitbox{1}{Motor C \\ vMax} & \bitbox{1}{Motor C \\ Accel} & \bitbox{1}{Motor C \\ Decel} \\
\end{bytefield}

\begin{bytefield}[bitwidth=\widthof{BrigHTNESS~},endianness=little]{6}
  \bitheader[lsb=46]{46-51} \\
  \bitbox{1}{Motor D Config} & \bitbox{1}{Motor D \\ vMin} & \bitbox{1}{Motor D \\ vMid} & \bitbox{1}{Motor D \\ vMax} & \bitbox{1}{Motor D \\ Accel} & \bitbox{1}{Motor D \\ Decel} \\
\end{bytefield}

\begin{bytefield}[bitwidth=\widthof{BrigHTNESS~},endianness=little]{2}
  \bitheader[lsb=52]{52-53} \\
  \bitbox{1}{Default Volume} & \bitbox{1}{Default Brightness} \\
\end{bytefield}

\begin{bytefield}[bitwidth=\widthof{BrigHTNESS~},endianness=little]{6}
  \bitheader[lsb=54]{54-59} \\
  \bitbox{1}{Light Ch 1 Brightness} & \bitbox{1}{Light Ch 2 Brightness} & \bitbox{1}{Light Ch 3 Brightness} & \bitbox{1}{Light Ch 4 Brightness} & \bitbox{1}{Light Ch 5 Brightness} & \bitbox{1}{Light Ch 6 Brightness} \\
\end{bytefield}

\begin{bytefield}[bitwidth=\widthof{BrigHTNESS~},endianness=little]{4}
  \bitheader[lsb=60]{60-63} \\
  \bitbox{1}{Light Ch 7 Brightness} & \bitbox{1}{Light Ch 8 Brightness} & \bitbox{1}{PF Light A Brightness} & \bitbox{1}{PF Light B Brightness} \\
\end{bytefield}

\pagebreak

**Device response packet:**

\begin{bytefield}[bitwidth=\widthof{BrigHTNESS~},endianness=little]{1}
  \bitheader{0} \\
  \bitbox{1}{0x84} \\
\end{bytefield}

\pagebreak

## `PFX_CMD_GET_CURRENT_STATE`

This message asks the PFx Brick to report its current internal operating state. This includes data such as the current motor target and operating speed, light output states, audio playback status, etc. This information can be useful for test purposes in order to verify that the PFx Brick is correctly responding to event/actions. It is also useful for simple passive monitoring for informational purposes.

\medskip

**Host command packet:**

\begin{bytefield}[bitwidth=\widthof{0x05~},endianness=little]{1}
  \bitheader{0} \\
  \bitbox{1}{0x06} \\
\end{bytefield}


**Device response packet:**

\begin{bytefield}[bitwidth=\widthof{Brightness~},endianness=little]{3}
  \bitheader{0-2} \\
  \bitbox{1}{0x86} & \bitbox{1}{Brightness} & \bitbox{1}{Volume} \\
\end{bytefield}

\begin{bytefield}[bitwidth=\widthof{PWMSpeed~},endianness=little]{8}
  \bitheader[lsb=3]{3-10} \\
  \footnotesize
  \bitbox{1}{Motor A direction} & \bitbox{1}{Motor A target speed} & \bitbox{1}{Motor A current speed} & \bitbox{1}{Motor A PWM speed} & \bitbox{1}{Motor B direction} & \bitbox{1}{Motor B target speed} & \bitbox{1}{Motor B current speed} & \bitbox{1}{Motor B PWM speed}\\
\end{bytefield}

\begin{bytefield}[bitwidth=\widthof{PWMSpeed~},endianness=little]{8}
  \bitheader[lsb=11]{11-18} \\
  \footnotesize
  \bitbox{1}{Motor C direction} & \bitbox{1}{Motor C target speed} & \bitbox{1}{Motor C current speed} & \bitbox{1}{Motor C PWM speed} & \bitbox{1}{Motor D direction} & \bitbox{1}{Motor D target speed} & \bitbox{1}{Motor D current speed} & \bitbox{1}{Motor D PWM speed}\\
\end{bytefield}

\begin{bytefield}[bitwidth=\widthof{CURRENTSPEED~},endianness=little]{2}
  \bitheader[lsb=19]{19-20} \\
  \footnotesize
  \bitbox{1}{Light Ch 1-8 Active Mask} & \bitbox{1}{PF Light Ch A-D Active Mask} \\
\end{bytefield}

\begin{bytefield}[bitwidth=\widthof{PWMSpeed~},endianness=little]{8}
  \bitheader[lsb=21]{21-28} \\
  \footnotesize
  \bitbox{1}{Light Ch 1 target level} & \bitbox{1}{Light Ch 2 \\ target level}  & \bitbox{1}{Light Ch 3 \\ target level} & \bitbox{1}{Light Ch 4 \\ target level} & \bitbox{1}{Light Ch 5 \\ target level} & \bitbox{1}{Light Ch 6 \\ target level} & \bitbox{1}{Light Ch 7 \\ target level} & \bitbox{1}{Light Ch 8 \\ target level} \\
\end{bytefield}

\begin{bytefield}[bitwidth=\widthof{CurrentSpeed~},endianness=little]{4}
  \bitheader[lsb=29]{29-32} \\
  \footnotesize
  \bitbox{1}{PF Light Ch A target level} & \bitbox{1}{PF Light Ch B \\ target level}  & \bitbox{1}{PF Light Ch C \\ target level} & \bitbox{1}{PF Light Ch D \\ target level} \\
\end{bytefield}

\begin{bytefield}[bitwidth=\widthof{TargetLevel~},endianness=little]{8}
  \bitheader[lsb=33]{33-40} \\
  \footnotesize
  \bitbox{1}{Light Ch 1 current level} & \bitbox{1}{Light Ch 2 \\ current level}  & \bitbox{1}{Light Ch 3 \\ current level} & \bitbox{1}{Light Ch 4 \\ current level} & \bitbox{1}{Light Ch 5 \\ current level} & \bitbox{1}{Light Ch 6 \\ current level} & \bitbox{1}{Light Ch 7 \\ current level} & \bitbox{1}{Light Ch 8 \\ current level} \\
\end{bytefield}

\begin{bytefield}[bitwidth=\widthof{CurrentSpeed~},endianness=little]{4}
  \bitheader[lsb=41]{41-44} \\
  \footnotesize
  \bitbox{1}{PF Light Ch A current level} & \bitbox{1}{PF Light Ch B \\ current level}  & \bitbox{1}{PF Light Ch C \\ current level} & \bitbox{1}{PF Light Ch D \\ current level} \\
\end{bytefield}

\pagebreak

\begin{bytefield}[bitwidth=\widthof{CURrentSpeed~},endianness=little]{4}
  \bitheader[lsb=45]{45-48} \\
  \bitbox{1}{Audio Ch 0 \\ mode} & \bitbox{1}{Audio Ch 0 \\ file ID} & \bitbox{1}{Audio Ch 1 \\ mode} & \bitbox{1}{Audio Ch 1 \\ file ID} \\
\end{bytefield}

\begin{bytefield}[bitwidth=\widthof{CURrentSpeed~},endianness=little]{4}
  \bitheader[lsb=49]{49-52} \\
  \bitbox{1}{Audio Ch 2 \\ mode} & \bitbox{1}{Audio Ch 2 \\ file ID} & \bitbox{1}{Audio Ch 3 \\ mode} & \bitbox{1}{Audio Ch 3 \\ file ID} \\
\end{bytefield}

\begin{bytefield}[bitwidth=\widthof{CURrentSpeed~},endianness=little]{4}
  \bitheader[lsb=53]{53-56} \\
  \bitbox{2}{millisec count} & \bitbox{2}{slow 1 sec count} \\
\end{bytefield}

\begin{bytefield}[bitwidth=\widthof{CURrentSpeed~},endianness=little]{5}
  \bitheader[lsb=57]{57-61} \\
  \bitbox{1}{Status Latch 1} & \bitbox{1}{Status Latch 2} & \bitbox{1}{File system state} & \bitbox{1}{Current \\ audio peak} & \bitbox{1}{Current \\ audio notch} \\
\end{bytefield}

\begin{bytefield}[bitwidth=\widthof{CURrentSpeed~},endianness=little]{2}
  \bitheader[lsb=62]{62-63} \\
  \bitbox{1}{Script exec \\ state} & \bitbox{1}{Script exec \\ line} \\
\end{bytefield}

\pagebreak

## `PFX_CMD_GET_NAME`

The device name is user configurable identifier which can be changed at any time.  It allows the owner of multiple PFx Bricks to uniquely assign a convenient name for each PFx Brick.  The device name is a UTF8 encoded string up to 24 bytes long left justified within the 24 byte block.  Unused characters should be padded with zeros (0x00).

\medskip

**Host command packet:**

\begin{bytefield}[bitwidth=\widthof{RESULT~},endianness=little]{1}
  \bitheader{0} \\
  \bitbox{1}{0x07} \\
\end{bytefield}

**Device response packet:**

\begin{bytefield}[bitwidth=\widthof{RESULT~},endianness=little]{1}
  \bitheader{0} \\
  \bitbox{1}{0x87}  \\
\end{bytefield}

\begin{bytefield}[endianness=little,bitwidth=0.042\linewidth]{24}
  \bitheader[lsb=1]{1-24} \\
  \wordbox{1}{Left justified 24 character name UTF8 encoded}\\
\end{bytefield}

## `PFX_CMD_SET_NAME`

This message sets the user assigned name of the PFx Brick.  The name is 24 bytes long and is UTF8 encoded.  Unused characters should be padded with zeros (0x00).

\medskip

**Host command packet:**

\begin{bytefield}[bitwidth=\widthof{RESULT~},endianness=little]{1}
  \bitheader{0} \\
  \bitbox{1}{0x09} \\
\end{bytefield}

\begin{bytefield}[endianness=little,bitwidth=0.042\linewidth]{24}
  \bitheader[lsb=1]{1-24} \\
  \wordbox{1}{Left justified 24 character name UTF8 encoded}\\
\end{bytefield}

**Device response packet:**

\begin{bytefield}[bitwidth=\widthof{RESULT~},endianness=little]{1}
  \bitheader{0} \\
  \bitbox{1}{0x89}  \\
\end{bytefield}

\pagebreak

## `PFX_CMD_GET_EVENT_ACTION`

The message allows the host to read the contents of the event LUT for a specific IR remote event and IR channel.

\medskip

**Host command packet:**

\begin{bytefield}[bitwidth=\widthof{upperbyte~},endianness=little]{3}
  \bitheader{0-2} \\
  \bitbox{1}{0x11} & \bitbox{1}{Event ID} & \bitbox{1}{Channel} \\
\end{bytefield}
or alternatively synonymous with:
\begin{bytefield}[bitwidth=\widthof{upperbyte~},endianness=little]{3}
  \bitheader{0-2} \\
  \bitbox{1}{0x11} & \bitbox{1}{Address \\ {[6:2]}} & \bitbox{1}{Address \\ {[1:0]}} \\
\end{bytefield}

**Device response packet:**

\begin{bytefield}[bitwidth=\widthof{upperbyte~},endianness=little]{1}
  \bitheader{0} \\
  \bitbox{1}{0x91} \\
\end{bytefield}

\begin{bytefield}[bitwidth=\widthof{LLLIGHT\_PF\_OUTPUT\_MASK~},endianness=little]{2}
  \bitheader[lsb=1]{1-2} \\
  \bitbox{1}{COMMAND} & \bitbox{1}{MOTOR\_ACTION\_ID}  \\
\end{bytefield}

\begin{bytefield}[bitwidth=\widthof{LLLIGHT\_PF\_OUTPUT\_MASK~},endianness=little]{2}
  \bitheader[lsb=3]{3-4} \\
  \bitbox{1}{MOTOR\_PARAM1} & \bitbox{1}{MOTOR\_PARAM2} \\
\end{bytefield}

\begin{bytefield}[bitwidth=\widthof{LLLIGHT\_PF\_OUTPUT\_MASK~},endianness=little]{2}
  \bitheader[lsb=5]{5-6} \\
  \bitbox{1}{LIGHT\_FX\_ID} & \bitbox{1}{LIGHT\_OUTPUT\_MASK} \\
\end{bytefield}

\begin{bytefield}[bitwidth=\widthof{LLLIGHT\_PF\_OUTPUT\_MASK~},endianness=little]{2}
  \bitheader[lsb=7]{7-8} \\
  \bitbox{1}{LIGHT\_PF\_OUTPUT\_MASK} & \bitbox{1}{LIGHT\_PARAM1} \\
\end{bytefield}

\begin{bytefield}[bitwidth=\widthof{LLLIGHT\_PF\_OUTPUT\_MASK~},endianness=little]{2}
  \bitheader[lsb=9]{9-10} \\
  \bitbox{1}{LIGHT\_PARAM2} & \bitbox{1}{LIGHT\_PARAM3} \\
\end{bytefield}

\begin{bytefield}[bitwidth=\widthof{LLLIGHT\_PF\_OUTPUT\_MASK~},endianness=little]{2}
  \bitheader[lsb=11]{11-12} \\
  \bitbox{1}{LIGHT\_PARAM4} & \bitbox{1}{LIGHT\_PARAM5} \\
\end{bytefield}

\begin{bytefield}[bitwidth=\widthof{LLLIGHT\_PF\_OUTPUT\_MASK~},endianness=little]{2}
  \bitheader[lsb=13]{13-14} \\
  \bitbox{1}{SOUND\_FX\_ID} & \bitbox{1}{SOUND\_FILE\_ID} \\
\end{bytefield}

\begin{bytefield}[bitwidth=\widthof{LLLIGHT\_PF\_OUTPUT\_MASK~},endianness=little]{2}
  \bitheader[lsb=15]{15-16} \\
  \bitbox{1}{SOUND\_PARAM1} & \bitbox{1}{SOUND\_PARAM2} \\
\end{bytefield}

\pagebreak
where the `Event ID` is defined as:
\medskip
\renewcommand{\arraystretch}{1.5}
\begin{tabular}{ | c | l | }
  \hline
  Event ID & MNEMONIC \\
  \hline
  0x00 & \lstinline|EVT_8879_TWO_BUTTONS|  \\
  0x01 & \lstinline|EVT_8879_LEFT_BUTTON|  \\
  0x02 & \lstinline|EVT_8879_RIGHT_BUTTON| \\
  0x03 & \lstinline|EVT_8879_LEFT_INC|     \\
  0x04 & \lstinline|EVT_8879_LEFT_DEC|     \\
  0x05 & \lstinline|EVT_8879_RIGHT_INC|    \\
  0x06 & \lstinline|EVT_8879_RIGHT_DEC|    \\
  0x07 & \lstinline|EVT_8885_LEFT_FWD|     \\
  0x08 & \lstinline|EVT_8885_LEFT_REV|     \\
  0x09 & \lstinline|EVT_8885_RIGHT_FWD|    \\
  0x0A & \lstinline|EVT_8885_RIGHT_REV|    \\
  0x0B & \lstinline|EVT_8885_LEFT_CTROFF|  \\
  0x0C & \lstinline|EVT_8885_RIGHT_CTROFF|  \\
  0x0D & \lstinline|EVT_EV3_BEACON| \\
  0x0E & \lstinline|EVT_TEST_EVENT|     \\
  0x0F & \lstinline|EVT_STARTUP_EVENT| \\
  0x10 & \lstinline|EVT_STARTUP_EVENT2|  \\
  \hline
\end{tabular}

\bigskip
`Channel` is the requested IR channel enumerated as 0,1,2,3 corresponding to the labelled IR channels of 1,2,3,4 respectively.  For the `EVT_TEST_EVENT` the `Channel` byte is ignored.  For the `EVT_STARTUP_EVENT` the `Channel` byte specifies one of the four startup events enumerated as 0,1,2,3 corresponding to starup events 1,2,3,4 respectively.  Similarly, for `EVT_STARTUP_EVENT2` the `Channel` byte refers to starup events 5,6,7,8.

\pagebreak

## `PFX_CMD_SET_EVENT_ACTION`

The message allows the host to set the contents of the event LUT for a specific IR remote event and IR channel.

\medskip

**Host command packet:**

\begin{bytefield}[bitwidth=\widthof{upperbyte~},endianness=little]{3}
  \bitheader{0-2} \\
  \bitbox{1}{0x12} & \bitbox{1}{Event ID} & \bitbox{1}{Channel} \\
\end{bytefield}

or alternatively synonymous with:

\begin{bytefield}[bitwidth=\widthof{upperbyte~},endianness=little]{3}
  \bitheader{0-2} \\
  \bitbox{1}{0x12} & \bitbox{1}{Address \\ {[6:2]}} & \bitbox{1}{Address \\ {[1:0]}} \\
\end{bytefield}

\begin{bytefield}[bitwidth=\widthof{LLLIGHT\_PF\_OUTPUT\_MASK~},endianness=little]{2}
  \bitheader[lsb=3]{3-4} \\
  \bitbox{1}{COMMAND} & \bitbox{1}{MOTOR\_ACTION\_ID}  \\
\end{bytefield}

\begin{bytefield}[bitwidth=\widthof{LLLIGHT\_PF\_OUTPUT\_MASK~},endianness=little]{2}
  \bitheader[lsb=5]{5-6} \\
  \bitbox{1}{MOTOR\_PARAM1} & \bitbox{1}{MOTOR\_PARAM2} \\
\end{bytefield}

\begin{bytefield}[bitwidth=\widthof{LLLIGHT\_PF\_OUTPUT\_MASK~},endianness=little]{2}
  \bitheader[lsb=7]{7-8} \\
  \bitbox{1}{LIGHT\_FX\_ID} & \bitbox{1}{LIGHT\_OUTPUT\_MASK} \\
\end{bytefield}

\begin{bytefield}[bitwidth=\widthof{LLLIGHT\_PF\_OUTPUT\_MASK~},endianness=little]{2}
  \bitheader[lsb=9]{9-10} \\
  \bitbox{1}{LIGHT\_PF\_OUTPUT\_MASK} & \bitbox{1}{LIGHT\_PARAM1} \\
\end{bytefield}

\begin{bytefield}[bitwidth=\widthof{LLLIGHT\_PF\_OUTPUT\_MASK~},endianness=little]{2}
  \bitheader[lsb=11]{11-12} \\
  \bitbox{1}{LIGHT\_PARAM2} & \bitbox{1}{LIGHT\_PARAM3} \\
\end{bytefield}

\begin{bytefield}[bitwidth=\widthof{LLLIGHT\_PF\_OUTPUT\_MASK~},endianness=little]{2}
  \bitheader[lsb=13]{13-14} \\
  \bitbox{1}{LIGHT\_PARAM4} & \bitbox{1}{LIGHT\_PARAM5} \\
\end{bytefield}

\begin{bytefield}[bitwidth=\widthof{LLLIGHT\_PF\_OUTPUT\_MASK~},endianness=little]{2}
  \bitheader[lsb=15]{15-16} \\
  \bitbox{1}{SOUND\_FX\_ID} & \bitbox{1}{SOUND\_FILE\_ID} \\
\end{bytefield}

\begin{bytefield}[bitwidth=\widthof{LLLIGHT\_PF\_OUTPUT\_MASK~},endianness=little]{2}
  \bitheader[lsb=17]{17-18} \\
  \bitbox{1}{SOUND\_PARAM1} & \bitbox{1}{SOUND\_PARAM2} \\
\end{bytefield}

**Device response packet:**

\begin{bytefield}[bitwidth=\widthof{upperbyte~},endianness=little]{1}
  \bitheader{0} \\
  \bitbox{1}{0x92} \\
\end{bytefield}

\pagebreak

where the `Event ID` is defined as:
\medskip
\renewcommand{\arraystretch}{1.5}
\begin{tabular}{ | c | l | }
  \hline
  Event ID & MNEMONIC \\
  \hline
  0x00 & \lstinline|EVT_8879_TWO_BUTTONS|  \\
  0x01 & \lstinline|EVT_8879_LEFT_BUTTON|  \\
  0x02 & \lstinline|EVT_8879_RIGHT_BUTTON| \\
  0x03 & \lstinline|EVT_8879_LEFT_INC|     \\
  0x04 & \lstinline|EVT_8879_LEFT_DEC|     \\
  0x05 & \lstinline|EVT_8879_RIGHT_INC|    \\
  0x06 & \lstinline|EVT_8879_RIGHT_DEC|    \\
  0x07 & \lstinline|EVT_8885_LEFT_FWD|     \\
  0x08 & \lstinline|EVT_8885_LEFT_REV|     \\
  0x09 & \lstinline|EVT_8885_RIGHT_FWD|    \\
  0x0A & \lstinline|EVT_8885_RIGHT_REV|    \\
  0x0B & \lstinline|EVT_8885_LEFT_CTROFF|  \\
  0x0C & \lstinline|EVT_8885_RIGHT_CTROFF|  \\
  0x0D & \lstinline|EVT_EV3_BEACON| \\
  0x0E & \lstinline|EVT_TEST_EVENT|     \\
  0x0F & \lstinline|EVT_STARTUP_EVENT| \\
  0x10 & \lstinline|EVT_STARTUP_EVENT2|  \\
  \hline
\end{tabular}

\bigskip
`Channel` is the requested IR channel enumerated as 0,1,2,3 corresponding to the labelled IR channels of 1,2,3,4 respectively.  For the `EVT_TEST_EVENT` the `Channel` byte is ignored.  For the `EVT_STARTUP_EVENT` the `Channel` byte specifies one of the four startup events enumerated as 0,1,2,3 corresponding to starup events 1,2,3,4 respectively.  Similarly, for `EVT_STARTUP_EVENT2` the `Channel` byte refers to starup events 5,6,7,8.

\pagebreak

## `PFX_CMD_TEST_ACTION`

Allows a host to test an event/action.  The specified action is performed immediately and is not stored in the event LUT.  The format of the action definition is identical to event/actions stored in the event LUT.

\medskip

**Host command packet:**

\begin{bytefield}[bitwidth=\widthof{Action~},endianness=little]{1}
  \bitheader{0} \\
  \bitbox{1}{0x13} \\
\end{bytefield}

\begin{bytefield}[bitwidth=\widthof{LLLIGHT\_PF\_OUTPUT\_MASK~},endianness=little]{2}
  \bitheader[lsb=1]{1-2} \\
  \bitbox{1}{COMMAND} & \bitbox{1}{MOTOR\_ACTION\_ID}  \\
\end{bytefield}

\begin{bytefield}[bitwidth=\widthof{LLLIGHT\_PF\_OUTPUT\_MASK~},endianness=little]{2}
  \bitheader[lsb=3]{3-4} \\
  \bitbox{1}{MOTOR\_PARAM1} & \bitbox{1}{MOTOR\_PARAM2} \\
\end{bytefield}

\begin{bytefield}[bitwidth=\widthof{LLLIGHT\_PF\_OUTPUT\_MASK~},endianness=little]{2}
  \bitheader[lsb=5]{5-6} \\
  \bitbox{1}{LIGHT\_FX\_ID} & \bitbox{1}{LIGHT\_OUTPUT\_MASK} \\
\end{bytefield}

\begin{bytefield}[bitwidth=\widthof{LLLIGHT\_PF\_OUTPUT\_MASK~},endianness=little]{2}
  \bitheader[lsb=7]{7-8} \\
  \bitbox{1}{LIGHT\_PF\_OUTPUT\_MASK} & \bitbox{1}{LIGHT\_PARAM1} \\
\end{bytefield}

\begin{bytefield}[bitwidth=\widthof{LLLIGHT\_PF\_OUTPUT\_MASK~},endianness=little]{2}
  \bitheader[lsb=9]{9-10} \\
  \bitbox{1}{LIGHT\_PARAM2} & \bitbox{1}{LIGHT\_PARAM3} \\
\end{bytefield}

\begin{bytefield}[bitwidth=\widthof{LLLIGHT\_PF\_OUTPUT\_MASK~},endianness=little]{2}
  \bitheader[lsb=11]{11-12} \\
  \bitbox{1}{LIGHT\_PARAM4} & \bitbox{1}{LIGHT\_PARAM5} \\
\end{bytefield}

\begin{bytefield}[bitwidth=\widthof{LLLIGHT\_PF\_OUTPUT\_MASK~},endianness=little]{2}
  \bitheader[lsb=13]{13-14} \\
  \bitbox{1}{SOUND\_FX\_ID} & \bitbox{1}{SOUND\_FILE\_ID} \\
\end{bytefield}

\begin{bytefield}[bitwidth=\widthof{LLLIGHT\_PF\_OUTPUT\_MASK~},endianness=little]{2}
  \bitheader[lsb=15]{15-16} \\
  \bitbox{1}{SOUND\_PARAM1} & \bitbox{1}{SOUND\_PARAM2} \\
\end{bytefield}

**Device response packet:**

\begin{bytefield}[bitwidth=\widthof{Action~},endianness=little]{1}
  \bitheader{0} \\
  \bitbox{1}{0x93} \\
\end{bytefield}

\pagebreak

## `PFX_CMD_SEND_EVENT`

This message triggers an action from the event/action LUT by specifying an event index into the LUT.  The event index corresponds to an equivalent received IR event and can be used to simulate IR events from USB or BLE connected hosts.

\medskip

**Host command packet:**

\begin{bytefield}[bitwidth=\widthof{Action~},endianness=little]{2}
  \bitheader{0} \\
  \bitbox{1}{0x15} & \bitbox{1}{Event \\ Index} \\
\end{bytefield}

`Event Index` is the address into the event/action LUT. It can also be interpreted as `Event ID` in bits [6:2] and `Channel` in bits[1:0] to form a composite `Event Index` address.

\medskip

**Device response packet:**

\medskip

\begin{bytefield}[bitwidth=\widthof{Action~},endianness=little]{1}
  \bitheader{0} \\
  \bitbox{1}{0x95} \\
\end{bytefield}

\pagebreak


## `PFX_CMD_INC_VOLUME`

This message increases the sound volume one increment.

\medskip

**Host command packet:**

\begin{bytefield}[bitwidth=\widthof{0xD1~},endianness=little]{1}
  \bitheader{0} \\
  \bitbox{1}{0x20} \\
\end{bytefield}


**Device response packet:**

\begin{bytefield}[bitwidth=\widthof{0xD1~},endianness=little]{1}
  \bitheader{0} \\
  \bitbox{1}{0xA0} \\
\end{bytefield}


## `PFX_CMD_DEC_VOLUME`

This message decreases the sound volume one increment.

\medskip

**Host command packet:**

\begin{bytefield}[bitwidth=\widthof{0xD2~},endianness=little]{1}
  \bitheader{0} \\
  \bitbox{1}{0x21} \\
\end{bytefield}


**Device response packet:**

\begin{bytefield}[bitwidth=\widthof{0xD2~},endianness=little]{1}
  \bitheader{0} \\
  \bitbox{1}{0xA1} \\
\end{bytefield}

\pagebreak

## `PFX_CMD_SET_AUDIO_EQ`

This message can be used to set the audio equalization levels for bass and treble as well as setting the state of the automatic Dynamic Range Control (DRC).  These values are applied immediately but do not override the default settings stored in the configuration.  The values stored in configuration are applied immediately after startup.  This message can then be used to set different bass/treble values during operation with a connected USB host.

\medskip

**Host command packet:**

\medskip

\begin{bytefield}[bitwidth=\widthof{TREBLE~},endianness=little]{4}
  \bitheader{0-3} \\
  \bitbox{1}{0x2A} & \bitbox{1}{Bass Level} & \bitbox{1}{Treble Level} & \bitbox{1}{DRC} \\
\end{bytefield}

**Device response packet:**

\medskip

\begin{bytefield}[bitwidth=\widthof{Treble~},endianness=little]{1}
  \bitheader{0} \\
  \bitbox{1}{0xAA} \\
\end{bytefield}

The values for `Bass Level` and `Treble Level` are valid as 2's complement numbers from -20 to 20 inclusive representing the gain/attenuation in dB with a nominal value of 0 dB.

The DRC value is either 0 or 1 reprsenting off or on respectively.

\pagebreak

## `PFX_CMD_LOAD_FIRMWARE_FILE`

This message is the mandatory start message to initiate the transfer of a new firmware image file from the host to the PFx Brick.  After this message one or more `PFX_CMD_LOAD_FIRMWARE_DATA` messages will follow containing the verbatim data content of the firmware image file.  Finally, after all of the data has been transferred with multiple `PFX_CMD_LOAD_FIRMWARE_DATA` messages, a final `PFX_CMD_LOAD_FIRMWARE_DONE` message is sent to terminate the transfer.  After each message, the PFx Brick will respond with an acknowlegement packet to pace the transfer from the host.

The total size of the file in bytes must be specified so that the PFx Brick can pre-allocate the flash memory sectors ahead of the write operations which will follow this message.

This message will not actually replace the running firmware application.  Rather, it transfers the new firmware image into a "staging" area.  After rebooting the PFx Brick, the bootloader will detect the new firmware image and attempt to replace the existing firmware.  The `PFX_CMD_REBOOT` command can be used to force the reboot process in order to complete the firmware replacement.

**PFX Encrypted Firmware Format**

The PFx Brick firmware update process is both secure and robust. This is achieved with 128-bit AES encryption of the firmware payload data and CRC32 verification of the decrypted data.  The decryption of the data is performed on the PFx Brick itself so that all data in transit via the USB interface is securely transferred.  Furthermore, CRC32 checking is perfomed after transferring the firmware image into its staging area and again after replacing the active firmware image.

The file format used to transfer firmware image files is a custom format derived from the Intel HEX file format. The PFx Brick firmware is compiled by the Microchip MPLAB X IDE and its linker script generates a standard Intel HEX file describing the firmware application binary. When decoded, this file describes binary data contained in three distinct locations in the PFx Brick microcontroller NVRAM flash memory:

1. IVT Table (Interrupt Vector Table)  0x000 - 0x1FE
2. Application Firmware 0x200-0x1FFFE
3. Configuration Flash Fuses 0xF80000-0xF81000

A CRC32 code is computed over all of the bytes in the IVT and Application Firmware spaces.  The Configuration Flash Fuse data is discarded.  All of the data bytes in the IVT and Application Firmware spaces are encrypted with AES 128-bit encryption with zero padding if required to acheive an integer multiple of 16 bytes.

The PFX Encrypted Firmware file is then written as follows:

\begin{bytefield}[bitwidth=\widthof{FILE~},endianness=little]{8}
  \bitheader{0-7} \\
  \bitbox{4}{Byte Count} & \bitbox{4}{CRC32}\\
\end{bytefield}
\begin{bytefield}[bitwidth=\widthof{FILE~},endianness=little]{8}
  \bitheader[lsb=8]{8-15} \\
  \bitbox{4}{IVT Start} & \bitbox{4}{IVT Length}\\
\end{bytefield}
\begin{bytefield}[bitwidth=\widthof{FILE~},endianness=little]{8}
  \bitheader[lsb=16]{16-23} \\
  \bitbox{4}{App Start} & \bitbox{4}{App Length}\\
\end{bytefield}
\begin{bytefield}[bitwidth=\widthof{FILE~},endianness=little]{8}
  \bitheader[lsb=24]{24-31} \\
  \bitbox{4}{Cfg Start} & \bitbox{4}{Cfg Length}\\
\end{bytefield}
\begin{bytefield}[bitwidth=\widthof{FILE~},endianness=little]{4}
  \bitheader[lsb=32]{32-35} \\
  \bitbox{4}{Reset Vector} \\
\end{bytefield}
\begin{bytefield}[bitwidth=\widthof{FILE~},endianness=little]{8}
  \bitheader[lsb=36]{36-43} \\
  \bitbox{8}{Encrypted data bytes}\\
  \bitbox[]{4}{$\vdots$ \\[1ex]} \\
\end{bytefield}

where,

`Byte Count` = total number of data bytes in the IVT and Application firmware spaces

`CRC32` = the CRC32 code computed over the IVT and Application spaces

`IVT Start` = start address of IVT space (word aligned/2-byte boundary)

`IVT Length` = number of 3-byte words in IVT space

`App Start` = start address of Application (word aligned/2-byte boundary)

`App Length` = number of 3-byte words in Application space

`Cfg Start` = start address of Configuration space (word aligned)

`Cfg Length` = number of 3-byte words in Configuration space

`Reset Vector` = start address of application contained at IVT address 0x0000

\pagebreak

**Host command packet:**

\begin{bytefield}[bitwidth=\widthof{FILE~},endianness=little]{16}
  \bitheader{0-15} \\
  \bitbox{1}{0x30} & \bitbox{1}{File type} & \bitbox{4}{Total file size [31:0]} & \bitbox{4}{CRC32 [31:0]} & \bitbox{2}{IVT size} & \bitbox{4}{App size} \\
\end{bytefield}

\medskip

where,

`File type` = 0 for PFx encrypted Intel HEX file format, 1 for Microchip blob format

`CRC32` is the computed CRC-32 (IEEE 802.3 Ethernet version) over the
entire firmware image file.  The polynomial implemented is:

x32 + x26 + x23 + x22 + x16 + x12 + x11 + x10 + x8 + x7 + x5 + x4 + x2 + x + 1

Commonly this is represented as 0xEDB88320 (or 0x04C11DB7 for big endian)

`IVT size` = number of 3-byte words in IVT space
`App size` = number of 3-byte words in Application space

\medskip

**Device response packet:**

\begin{bytefield}[bitwidth=\widthof{UNIQUE~},endianness=little]{3}
  \bitheader{0,1} \\
  \bitbox{1}{0xB0} & \bitbox{2}{Status} \\
\end{bytefield}


\renewcommand{\arraystretch}{1.5}
\begin{tabular}{ | c | l | p{7.5cm} | }
  \hline
  Status & Code & Description \\
  \hline
  0x00 & \lstinline|PFX_ERR_TRANSFER_REQUEST_OK|  & load firmware file request is ok  \\
  0x03 & \lstinline|PFX_ERR_TRANSFER_TOO_BIG|     & file size exceeds free capacity of the firmware staging area \\
  \hline
\end{tabular}

\pagebreak

## `PFX_CMD_LOAD_FIRMWARE_DATA`

One or more of these messages is sent after the `PFX_CMD_LOAD_FIRMWARE_FILE` message containing the raw byte-for-byte verbatim content of the firmware image file densely packed into every data byte.

**Host command packet:**

\begin{bytefield}[bitwidth=\widthof{0x6B~},endianness=little]{16}
  \bitheader{0-15} \\
  \bitbox{1}{0x31} & \bitbox{15}{Firmware Image File Data Bytes} \\
  \bitbox[]{16}{$\vdots$ \\[1ex]} \\
  \bitheader[lsb=48]{48-63} \\
  \wordbox{1}{Firmware Image File Data Bytes} \\
\end{bytefield}

**Device response packet:**

\begin{bytefield}[bitwidth=\widthof{0xEB~},endianness=little]{3}
  \bitheader{0,1} \\
  \bitbox{1}{0xB1} & \bitbox{2}{Status} \\
\end{bytefield}

\renewcommand{\arraystretch}{1.5}
\begin{tabular}{ | c | l | p{8.0cm} | }
  \hline
  Status & Code & Description \\
  \hline
  0x00 & \lstinline|PFX_ERR_NONE|              & transfer of firmware payload data ok \\
  0x04 & \lstinline|PFX_ERR_TRANSFER_INVALID| & data transfer session is invalid (usually due to a missing \lstinline|PFX_CMD_LOAD_FIRMWARE_FILE| packet)  \\
  0x07 & \lstinline|PFX_ERR_TRANSFER_BUSY_WAIT| & data transfer of this packet should wait and try again due to an active time-sensitive write or erase operation. The host should reattempt to send the same data packet and check the Status byte. \\
  \hline
\end{tabular}

\pagebreak

## `PFX_CMD_LOAD_FIRMWARE_DONE`

This message is sent after the final `PFX_CMD_LOAD_FIRMWARE_DATA` message to signal the termination of the firmware file transfer. The host should check the returned error code to ensure that the file transfer was successful.

**Host command packet:**

\begin{bytefield}[bitwidth=\widthof{0xEC~},endianness=little]{1}
  \bitheader{0} \\
  \bitbox{1}{0x32} \\
\end{bytefield}

**Device response packet:**

\begin{bytefield}[bitwidth=\widthof{0xEC~},endianness=little]{3}
  \bitheader{0,1} \\
  \bitbox{1}{0xB2} & \bitbox{2}{Status} \\
\end{bytefield}

\renewcommand{\arraystretch}{1.5}
\begin{tabular}{ | c | l | p{8.0cm} | }
  \hline
  Status & Code & Description \\
  \hline
  0x00 & \lstinline|PFX_ERR_NONE|              & firmware file transfer completed with no errors \\
  0x04 & \lstinline|PFX_ERR_TRANSFER_INVALID|       & data transfer session is invalid (usually due to a missing \lstinline|PFX_CMD_LOAD_FIRMWARE_FILE| packet)  \\
  0x06 & \lstinline|PFX_ERR_TRANSFER_CRC_MISMATCH| & computed CRC32 of received firmware image does not match provided CRC32 code \\
  \hline
\end{tabular}

\pagebreak

## `PFX_CMD_READ_BOOTCONFIG`

This message allows the host to read back the contents of bootloader status and control values stored in the microcontroller NVRAM.  These values are used to coordinate the firmware upgrade process between the bootloader and the host as well as storing the operational state of the PFx Brick.

**Host command packet:**

\begin{bytefield}[bitwidth=\widthof{0xEC~},endianness=little]{1}
  \bitheader{0} \\
  \bitbox{1}{0x34} \\
\end{bytefield}

**Device response packet:**

\begin{bytefield}[bitwidth=\widthof{0xEC~},endianness=little]{1}
  \bitheader{0} \\
  \bitbox{1}{0xB4} \\
\end{bytefield}

\begin{bytefield}[bitwidth=\widthof{0xBB1~},endianness=little]{4}
  \bitheader[lsb=1]{1-4} \\
  \bitbox{4}{MAGIC\_NUMBER}  \\
\end{bytefield}

\begin{bytefield}[bitwidth=\widthof{0xBB1~},endianness=little]{4}
  \bitheader[lsb=5]{5-8} \\
  \bitbox{4}{STATE}  \\
\end{bytefield}

\begin{bytefield}[bitwidth=\widthof{0xBB1~},endianness=little]{4}
  \bitheader[lsb=9]{9-12} \\
  \bitbox{4}{FILESIZE\_UPPER}  \\
\end{bytefield}

\begin{bytefield}[bitwidth=\widthof{0xBB1~},endianness=little]{4}
  \bitheader[lsb=13]{13-16} \\
  \bitbox{4}{FILESIZE\_LOWER}  \\
\end{bytefield}

\begin{bytefield}[bitwidth=\widthof{0xBB1~},endianness=little]{4}
  \bitheader[lsb=17]{17-20} \\
  \bitbox{4}{CRCIN\_UPPER}  \\
\end{bytefield}

\begin{bytefield}[bitwidth=\widthof{0xBB1~},endianness=little]{4}
  \bitheader[lsb=21]{21-24} \\
  \bitbox{4}{CRCIN\_LOWER}  \\
\end{bytefield}
\pagebreak


## `PFX_CMD_REBOOT`

Reboots the PFx Brick. This command should only be issued to initiate the upgrade of application firmware after it has been successfully transferred and staged into the PFx Brick.

Note that immediately after issuing this command, the reboot process will terminate the current USB HID communication session.  The host application will not be able to communicate with the PFx Brick unless it periodically attempts to re-open a new USB HID session.  The host operating system USB stack will continue to re-enumerate the PFx Brick when it restarts and the host application should then be able to re-negotiate a new USB HID session.  It will be important for the host application to check the PFx Brick status (i.e. with the `PFX_CMD_GET_STATUS` command) after re-connection in order to determine whether the PFx Brick is running in Normal mode, Service mode, or if any errors are present in the firmware upgrade process.

**Host command packet:**

\begin{bytefield}[bitwidth=\widthof{0xAA~},endianness=little]{8}
  \bitheader{0-7} \\
  \bitbox{1}{0x37} & \bitbox{1}{0x5A} & \bitbox{1}{0xA5} & \bitbox{1}{0xD0} & \bitbox{1}{0xBE} & \bitbox{1}{0xB0} & \bitbox{1}{0x04} & \bitbox{1}{0x77} \\
\end{bytefield}

**Device response packet:**

\begin{bytefield}[bitwidth=\widthof{0xAA~},endianness=little]{1}
  \bitheader{0} \\
  \bitbox{1}{0xB7} \\
\end{bytefield}

\pagebreak


## `PFX_CMD_FILE_OPEN`

The PFx Brick File System is a simple block-oriented file storage facility which allows files of any content to be transfered to and from the connected host. The primary function of this file system is to store audio files; however, it is general purpose enough to be used for storage of any file type for future applications.

Access to the file system is provided by a set of conventional file I/O methods such as open, close, read, write, etc.  Before any file can be accessed, it must be opened.  This will ensure that pointers to the file data content for read and write operations are initialized to a known state.  Open files must also be closed when the host has completed any read or write tasks.  This ensures any buffered data is safely committed back to the file system and the state of file handles and directories remain consistent.

The `PFX_CMD_FILE_OPEN` command opens a virtual file handle to a file for host file I/O.  If the specified file does not exist, then it is created by reserving a directory entry for the file and empty storage sectors are allocated for the file.  Unlike other file systems, the creation of a new file requires that the file size be known in advance for preallocation.  If the host connects to the PFx Brick via more than one USB HID interface session, each session is granted its own virtual file handle.  Futhermore, there is only one file handle per USB HID interface.

**Host command packet:**
\medskip
\begin{bytefield}[bitwidth=\widthof{UNIQUE~},endianness=little]{7}
  \bitheader{0-6} \\
  \bitbox{1}{0x40} & \bitbox{1}{Unique File ID} & \bitbox{1}{Mode} & \bitbox{4}{Total file size [31:0]} \\
\end{bytefield}

\begin{bytefield}[bitwidth=\widthof{0x76~},endianness=little]{16}
  \bitheader[lsb=7]{7-22} \\
  \bitbox{16}{Left justified 32 character file name UTF8 encoded} \\
  \bitheader[lsb=23]{23-38} \\
  \wordbox{1}{ } \\
\end{bytefield}

**Device response packet:**
\medskip
\begin{bytefield}[bitwidth=\widthof{UNIQUE~},endianness=little]{2}
  \bitheader{0-1} \\
  \bitbox{1}{0xC0} & \bitbox{1}{Status} \\
\end{bytefield}

The `Mode` parameter is specified as the logical-OR of the following flags:

\renewcommand{\arraystretch}{1.5}
\begin{tabular}{ | c | l | p{7.5cm} | }
  \hline
  Mode & Flag & Description \\
  \hline
  0x01 & \lstinline|PFX_FILE_READ|      & open file with read access  \\
  0x02 & \lstinline|PFX_FILE_WRITE|     & open file with write access \\
  0x04 & \lstinline|PFX_FILE_CREATE|    & create a new file with ID and size  \\
  \hline
\end{tabular}

\bigskip
If a new file is created with `PFX_FILE_CREATE` mode flag, then the specified file ID must be unique and the total file size must be specified in bytes.  Optionally, a 32 character UTF-8 filename can be specified with the file create request.  This name appears in the file directory.  If the name is not specified, the request will still succeed and the file can be renamed at any other time after it is created.  If the file ID is already in use, then the file open request will not succeed.  File open requests on existing files (without the create flag) only need to specify the file ID and do not need to specify file name or size.

If the file specified by ID is valid, then a virual file handle will be retained on the PFx associated with the USB interface channel that made the request.  This file handle can then be used to perform subsequent read and write file operations.

The file open request will return a status code which indicates either success or error according to the table below.  Note that these error codes are shared among all of the file system access commands and returned in the `Status` byte.  These error codes are also repeated in the Error Code section at the end of this document.

\bigskip
\renewcommand{\arraystretch}{1.5}
\begin{tabular}{ | c | l | p{7.5cm} | }
  \hline
  Status & Code & Description \\
  \hline
  0x00 & \lstinline|PFX_ERR_NONE|                   & file system operation ok \\
  0xF0 & \lstinline|PFX_ERR_FILE_SYSTEM_ERR|      & overall file system error \\
  0xF1 & \lstinline|PFX_ERR_FILE_INVALID|          & file request was invalid or file is invalid  \\
  0xF2 & \lstinline|PFX_ERR_FILE_OUT_OF_RANGE|   & file access request is outside of file size  \\
  0xF3 & \lstinline|PFX_ERR_FILE_READ_ONLY|       & file creation or write access denied \\
  0xF4 & \lstinline|PFX_ERR_FILE_TOO_BIG|         & requested file creation is too big  \\
  0xF5 & \lstinline|PFX_ERR_FILE_NOT_FOUND|       & requested file ID is not found \\
  0xF6 & \lstinline|PFX_ERR_FILE_NOT_UNIQUE|      & requested file creation ID is already used  \\
  0xF7 & \lstinline|PFX_ERR_FILE_LOCKED_BUSY|     & file system is locked or busy  \\
  0xF8 & \lstinline|PFX_ERR_FILE_SYSTEM_FULL|     & file system full \\
  0xF9 & \lstinline|PFX_ERR_FILE_SYSTEM_TIMEOUT|  & file access operation time out \\
  0xFA & \lstinline|PFX_ERR_FILE_INVALID_ADDRESS| & file system request resulted in an invalid memory address \\
  0xFB & \lstinline|PFX_ERR_FILE_NEXT_SECTOR|     & file system FAT points to an invalid sector \\
  0xFC & \lstinline|PFX_ERR_FILE_ACCESS_DENIED|   & file system operation denied or prohibited \\
  0xFF & \lstinline|PFX_ERR_FILE_EOF|              & file access has reached the end of the file \\
  \hline
\end{tabular}

\pagebreak

## `PFX_CMD_FILE_CLOSE`

The `PFX_CMD_FILE_CLOSE` command closes the virtual file handle to a file which was opened with the `PFX_CMD_FILE_OPEN` command.  It is important to close a file especially after any write operations.  This is to ensure that any buffered or cached data is committed to the file system so that no written data is lost.

\medskip

**Host command packet:**

\begin{bytefield}[bitwidth=\widthof{Unique~},endianness=little]{2}
  \bitheader{0-1} \\
  \bitbox{1}{0x41} & \bitbox{1}{File ID} \\
\end{bytefield}

**Device response packet:**

\begin{bytefield}[bitwidth=\widthof{Unique~},endianness=little]{2}
  \bitheader{0-1} \\
  \bitbox{1}{0xC1} & \bitbox{1}{Status} \\
\end{bytefield}

\pagebreak

## `PFX_CMD_FILE_READ`

The `PFX_CMD_FILE_READ` command is used to read file data sequentially from the current file read pointer location.  Each read file operation advances the file pointer by how many file bytes have been retrieved. This ensures consecutive read operations maintain continuity along the file data stream.

\medskip

**Host command packet:**

\begin{bytefield}[bitwidth=\widthof{Unique~},endianness=little]{3}
  \bitheader{0-1} \\
  \bitbox{1}{0x42} & \bitbox{1}{File ID} & \bitbox{1}{nBytes} \\
\end{bytefield}

**Device response packet:**

\begin{bytefield}[bitwidth=\widthof{Unique~},endianness=little]{12}
  \bitheader{0-11} \\
  \bitbox{1}{0xC2} & \bitbox{1}{Status} & \bitbox{10}{Received file data bytes}\\
  \bitbox[]{12}{$\vdots$ \\[1ex]} \\
  \bitheader[lsb=52]{52-63} \\
  \wordbox{1}{Received file data bytes (up to 62)} \\
\end{bytefield}

The `nBytes` field specifies up to how many data bytes should be read (valid range is 1-62).

The returned `Status` byte is either an error code or the number of bytes (1-62) contained in this packet.

\pagebreak

## `PFX_CMD_FILE_WRITE`

The `PFX_CMD_FILE_WRITE` command is used to write file data sequentially from the current file write pointer location.  Each write file operation advances the file pointer by how many file bytes have been written. This ensures consecutive write operations maintain continuity along the file data stream.

\medskip

**Host command packet:**

\begin{bytefield}[bitwidth=\widthof{Unique~},endianness=little]{12}
  \bitheader{0-11} \\
  \bitbox{1}{0x43} & \bitbox{1}{File ID} & \bitbox{1}{nBytes} & \bitbox{9}{Data Bytes to Write} \\
  \bitbox[]{12}{$\vdots$ \\[1ex]} \\
  \bitheader[lsb=52]{52-63} \\
  \wordbox{1}{Data Bytes to Write} \\
\end{bytefield}

**Device response packet:**

\begin{bytefield}[bitwidth=\widthof{Unique~},endianness=little]{2}
  \bitheader{0-1} \\
  \bitbox{1}{0xC3} & \bitbox{1}{Status} \\
\end{bytefield}

The `nBytes` field specifies up to how many data bytes should be read (valid range is 1-62).

The returned `Status` byte error code indicates if write operaton was successful.

\pagebreak

## `PFX_CMD_FILE_SEEK`

The `PFX_CMD_FILE_SEEK` command is used to reposition the file access pointer to any location within the file.  The position is specified as an absolute value in bytes relative to the start of the file.

**Host command packet:**
\medskip
\begin{bytefield}[bitwidth=\widthof{UNIQUE~},endianness=little]{6}
  \bitheader{0-5} \\
  \bitbox{1}{0x44} & \bitbox{1}{File ID} & \bitbox{4}{File byte position [31:0]} \\
\end{bytefield}

**Device response packet:**
\medskip
\begin{bytefield}[bitwidth=\widthof{UNIQUE~},endianness=little]{2}
  \bitheader{0-1} \\
  \bitbox{1}{0xC4} & \bitbox{1}{Status} \\
\end{bytefield}

\pagebreak

## `PFX_CMD_FILE_DIR`

The `PFX_CMD_FILE_DIR` command is used to interact with the file system directory.  The file directory contains a list of files currently stored on the file system along with several attributes and data fields.  This command can be used request different types of directory information such as the number of files, free space, individual file directory entries, etc.  It can also be used to modify the directory entry of a stored file.

\bigskip

**Host command packet:**

\medskip
\begin{bytefield}[bitwidth=\widthof{INIQUE~},endianness=little]{6}
  \bitheader{0-2} \\
  \bitbox{1}{0x45} & \bitbox{1}{Request} & \bitbox{4}{File ID, index, optional parameters, ...} \\
\end{bytefield}
\medskip

The `Request` byte can be specified as follows:

\medskip
\renewcommand{\arraystretch}{1.5}
\begin{tabular}{ | c | l | p{7.5cm} | }
  \hline
  Status & Code & Description \\
  \hline
  0x00 & \lstinline|PFX_DIR_REQ_GET_FILE_COUNT|     & Get number of files  \\
  0x01 & \lstinline|PFX_DIR_REQ_GET_FREE_SPACE|     & Get free space and total capacity  \\
  0x02 & \lstinline|PFX_DIR_REQ_GET_DIR_ENTRY_IDX|  & Get directory entry at index  \\
  0x03 & \lstinline|PFX_DIR_REQ_GET_DIR_ENTRY_ID|   & Get directory entry of File ID  \\
  0x04 & \lstinline|PFX_DIR_REQ_ADD_AUDIO_FILE_ID|  & Add audio meta data to directory for File ID  \\
  0x05 & \lstinline|PFX_DIR_REQ_RENAME_FILE_ID|     & Rename File ID  \\
  0x06 & \lstinline|PFX_DIR_REQ_SET_ATTR_ID|        & Set attributes for File ID  \\
  0x07 & \lstinline|PFX_DIR_REQ_SET_USER_DATA1_ID|  & Set UserData1 attributes for File ID  \\
  0x08 & \lstinline|PFX_DIR_REQ_SET_USER_DATA2_ID|  & Set UserData2 attributes for File ID   \\
  0x09 & \lstinline|PFX_DIR_REQ_COMPUTE_CRC32_ID|   & Compute CRC32 for File ID  \\
  0x0A & \lstinline|PFX_DIR_REQ_SET_ATTR_MASKED_ID| & Set attributes with mask for File ID  \\
  0x0B & \lstinline|PFX_DIR_REQ_GET_NAMED_FILE_ID|  & Get File ID for file name  \\
  0x0C & \lstinline|PFX_DIR_REQ_GET_SMALL_DIR_ID|   & Get compact file info of File ID  \\
  0x0D & \lstinline|PFX_DIR_REQ_GET_SMALL_DIR_IDX|  & Get compact file info at index  \\
  \hline
\end{tabular}

\bigskip

**Device response packets**

**Request 0x00 - Get Number of Files**

\medskip
\begin{bytefield}[bitwidth=\widthof{INIQUE~},endianness=little]{5}
  \bitheader{0-3} \\
  \bitbox{1}{0xC5} & \bitbox{1}{Request} & \bitbox{1}{Status} & \bitbox{2}{File Count[15:0]} \\
\end{bytefield}

**Request 0x01 - Get Free Space / Capacity**

\medskip
\begin{bytefield}[bitwidth=\widthof{INIQUE~},endianness=little]{11}
  \bitheader{0-10} \\
  \bitbox{1}{0xC5} & \bitbox{1}{Request} & \bitbox{1}{Status} & \bitbox{4}{Bytes Free[31:0]} & \bitbox{4}{Bytes Capacity[31:0]}\\
\end{bytefield}

**Request 0x02 - Get Directory Entry at Index**

**Request 0x03 - Get Directory Entry of File ID**

\medskip
\begin{bytefield}[bitwidth=\widthof{INIQUE~},endianness=little]{10}
  \bitheader{0-9} \\
  \bitbox{1}{0xC5} & \bitbox{1}{Request} & \bitbox{1}{Status} & \bitbox{1}{File ID} & \bitbox{4}{File Size[31:0]} & \bitbox{2}{First Sector[15:0]}  \\
\end{bytefield}

\begin{bytefield}[bitwidth=\widthof{INIQUE~},endianness=little]{10}
  \bitheader[lsb=10]{10-19} \\
  \bitbox{2}{Attributes [15:0]} & \bitbox{4}{UserData1 [31:0]} & \bitbox{4}{UserData2 [31:0]}  \\
\end{bytefield}

\begin{bytefield}[bitwidth=\widthof{INIQUE~},endianness=little]{4}
  \bitheader[lsb=20]{20-23} \\
  \bitbox{4}{CRC32[31:0]}  \\
\end{bytefield}

\begin{bytefield}[bitwidth=\widthof{0xA2~},endianness=little]{16}
  \bitheader[lsb=24]{24-39} \\
  \bitbox{16}{Left justified 32 character file name UTF8 encoded} \\
  \bitheader[lsb=40]{40-55} \\
  \wordbox{1}{ } \\
\end{bytefield}

**Request 0x04 - Add Audio Meta Data to Directory with ID**

This command will trigger the file system to read the specified file and extract meta data associated with an audio WAV file.  This meta data is then written to the directory in the `Attributes`, `UserData1`, and `UserData2` fields.

\medskip

**Request 0x05 - Rename File with ID**

Changes the 32 character filename of the specified file.  The filename data bytes should be contained in bytes 3 to 34 of the host command packet.

\medskip

**Request 0x06 - Set Attributes with ID**

Changes the `Attributes` field of the file directory entry.  The `Attributes[15:0]` data bytes should be contained in bytes 3 and 4 of the host command packet.

**Request 0x0A - Set Attributes with ID, masked**

Changes the `Attributes` field of the file directory entry.  The `Attributes[15:0]` data bytes should be contained in bytes 3 and 4 of the host command packet and a bit mask should be contained in bytes 5 and 6.  The only bits that are changed in the `Attributes` field are the bits specified with the bit mask.  This allows non-destructive modification of attributes by only specifying the bits that require changing.  For example a command to modify the file type of file ID `0x77` to WAV would be as follows: `0x45 0x0A 0x77 0x00 0x00 0xFF 0x00`, i.e. only `User Attributes[15:8]` is set to `0x00` because of the bit mask `0xFF00`.

\medskip

**Request 0x07 - Set UserData1 with ID**

**Request 0x08 - Set UserData2 with ID**

Changes the `UserData1/2` fields of the file directory entry.  The `UserData1/2[31:0]` data bytes should be contained in bytes 3 to 6 of the host command packet.

\pagebreak

**Request 0x09 - Compute CRC32 with ID**

Computes the CRC32 hash code of the specified file and stores it into the file directory.  Normally, the CRC32 code is automatically computed when a file that is being written is closed.  This command can be used force the recalculation of the CRC32 code.  Note that the computation of the CRC32 code is performed as a background process and may take several seconds to complete for large files.  The CRC32 code is set to zero before a new computation is performed.  This can be used to monitor the progress of the CRC32 computation since it will revert to a non-zero value when it is completed.

\medskip

**Request 0x0B - Get File ID for Filename**

Attempts to find the file ID of a specified filename.  The filename data bytes should be contained in bytes 3 to 34 of the host command packet and byte 2 should contain the length of filename.  If the filename is found, then it is returned in the `Status` field, otherwise an error code indicating `PFX_ERR_FILE_NOT_FOUND` or `PFX_ERR_FILE_NOT_UNIQUE` may be returned.

\medskip

**Request 0x0C - Get Compact File Info with ID**

**Request 0x0D - Get Compact File Info with Index**

This message returns two consecutive file directory entries in a compact form within one message.  This directory request type is available for the benefit of Bluetooth mobile hosts needing to enumerate sound files quickly by reducing the number of BLE transactions and bandwidth.  The message returns only essential file information such as size, attributes, and a truncated version of the filename.  The message also packs two entries starting at the index of requested file and if it exists, the next consecutive file directory entry.

\medskip
\begin{bytefield}[bitwidth=\widthof{INIQUE~},endianness=little]{10}
  \bitheader{0-9} \\
  \bitbox{1}{0xC5} & \bitbox{1}{Request} & \bitbox{1}{Status} & \bitbox{1}{File ID 1} & \bitbox{4}{File Size 1 [31:0]} & \bitbox{2}{Attributes 1 [15:0]}  \\
\end{bytefield}

\begin{bytefield}[bitwidth=\widthof{0xJ~},endianness=little]{23}
  \bitheader[lsb=10]{10-32} \\
  \bitbox{23}{Left justified 23 character file name 1 UTF8 encoded} \\
\end{bytefield}

\begin{bytefield}[bitwidth=\widthof{INIQUE~},endianness=little]{7}
  \bitheader[lsb=33]{33-39} \\
  \bitbox{1}{File ID 2} & \bitbox{4}{File Size 2 [31:0]} & \bitbox{2}{Attributes 2 [15:0]}  \\
\end{bytefield}

\begin{bytefield}[bitwidth=\widthof{0xJ~},endianness=little]{23}
  \bitheader[lsb=40]{40-62} \\
  \bitbox{23}{Left justified 23 character file name 2 UTF8 encoded} \\
\end{bytefield}

\bigskip

The `Status` byte contains the result code of the directory operation request which should nominally be 0x00 indicating success.


\medskip

\begin{bytefield}[bitwidth=\widthof{INIQUE~},endianness=little]{3}
  \bitheader{0-2} \\
  \bitbox{1}{0xC5} & \bitbox{1}{Request} & \bitbox{1}{Status} \\
\end{bytefield}

\pagebreak

## `PFX_CMD_FILE_REMOVE`

The `PFX_CMD_FILE_REMOVE` command deletes a file from the file system.  The file is specified by its unique File ID.

\medskip

**Host command packet:**

\begin{bytefield}[bitwidth=\widthof{Unique~},endianness=little]{2}
  \bitheader{0-1} \\
  \bitbox{1}{0x46} & \bitbox{1}{File ID} \\
\end{bytefield}

**Device response packet:**

\begin{bytefield}[bitwidth=\widthof{Unique~},endianness=little]{2}
  \bitheader{0-1} \\
  \bitbox{1}{0xC6} & \bitbox{1}{Status} \\
\end{bytefield}

\pagebreak


## `PFX_CMD_FILE_FORMAT_FS`

The `PFX_CMD_FILE_FORMAT_FS` command erases and re-initializes the entire file system.  After this command is performed, the PFx Brick will automatically start to pre-erase the file storage space on the flash memory. During this process, the host can continue to access the file system; however, response times will be reduced due to the arbitration that must take place to interleave access to the flash memory.  The process of pre-erasing memory usually takes less than one minute and after it is completed, full response time will be restored.

\medskip

**Host command packet:**

\begin{bytefield}[bitwidth=\widthof{Unique~},endianness=little]{5}
  \bitheader{0-4} \\
  \bitbox{1}{0x47} & \bitbox{1}{0xEA} & \bitbox{1}{0x5E} & \bitbox{1}{0x88} & \bitbox{1}{Mode} \\
\end{bytefield}

\medskip

**Device response packet:**

\begin{bytefield}[bitwidth=\widthof{Unique~},endianness=little]{2}
  \bitheader{0-1} \\
  \bitbox{1}{0xC7} & \bitbox{1}{Status} \\
\end{bytefield}

\bigskip

The `Mode` parameter can be used to specify one of two formatting modes:

```
0 = Fast Format:  erases only occupied sectors
1 = Complete:  erases all sectors
```

\pagebreak

## `PFX_CMD_FILE_GET_FS_STATE`

The `PFX_CMD_FILE_GET_FS_STATE` command reports low-level operational status information of the file system.  This data is mainly used for test and debug purposes; however, it could be used for useful status updates.

\medskip

**Host command packet:**

\begin{bytefield}[bitwidth=\widthof{UNIQUE~},endianness=little]{1}
  \bitheader{0} \\
  \bitbox{1}{0x48} \\
\end{bytefield}

\medskip

**Device response packet:**

\begin{bytefield}[bitwidth=\widthof{UNIQUE~},endianness=little]{8}
  \bitheader{0-7} \\
  \bitbox{1}{0xC8} & \bitbox{1}{nFiles} & \bitbox{1}{State} & \bitbox{1}{Flags} & \bitbox{2}{Current Erase Sector} & \bitbox{2}{Initial Time Count} \\
\end{bytefield}

\begin{bytefield}[bitwidth=\widthof{UNIQUE~},endianness=little]{10}
  \bitheader[lsb=8]{8-17} \\
  \bitbox{2}{Autosync Dir Time} & \bitbox{2}{Autosync FAT Time} & \bitbox{2}{Sector Capacity} & \bitbox{2}{Free Sectors} & \bitbox{2}{Empty Sectors}  \\
\end{bytefield}

\bigskip

The `nFiles` byte reports the number of files contained in the file system.

The `State` byte reports the state of the finite state machine which operates the file system.

The `Flags` byte reports operational state flags of the file system.

The `Current Erase Sector` field reports the current sector of the garbage collection process.  This value will change continuously representing the on-going scanning of FAT looking for freed sectors to erase.

The `Initial Time Count` field reports the initial timer value of time out counters.

The `Autosync Dir Time` and `Autosync FAT Time` fields report the timer values of the autosync hold-off before any autosync processes commit file system changes to flash memory.

`Sector Capacity` reports the total available storage capacity in 4096 byte sectors of the file system.  The total byte capacity can be computed by multiplying this value by 4096.

`Free Sectors` reports the sum of free and empty sectors.  Sectors are 4096 byte storage blocks of the file system.  The free byte capacity can be computed by multiplying this value by 4096.  When a file is removed or if the file system is formatted, occupied sectors are de-allocated from the file system and marked as free.  These free sectors can be made available for storage after the file system recovers the sectors by erasing them in an automated garbage collection process.  After free sectors are erased, they become empty sectors available for re-allocation for new files.

`Empty Sectors` reports the remaining available empty sectors.  Empty sectors can be allocated for the creation of new files.  The available byte capacity can be computed by multiplying this value by 4096.

\pagebreak

## `PFX_CMD_RUN_SCRIPT`

The `PFX_CMD_RUN_SCRIPT` command starts execution of a script file stored in the file system.  The file is specified by its unique File ID.

\medskip

**Host command packet:**

\begin{bytefield}[bitwidth=\widthof{Unique~},endianness=little]{2}
  \bitheader{0-1} \\
  \bitbox{1}{0x4B} & \bitbox{1}{File ID} \\
\end{bytefield}

**Device response packet:**

\begin{bytefield}[bitwidth=\widthof{Unique~},endianness=little]{2}
  \bitheader{0-1} \\
  \bitbox{1}{0xCB} & \bitbox{1}{Status} \\
\end{bytefield}

The `Status` byte contains the result code of this command and should nominally be 0x00 indicating success.

If the `File ID` byte is set to 0xFF, then the current running script will be stopped.

\pagebreak

## `PFX_CMD_STATUS_LED`

This message allows the host to either poll or set the state of the status LED.

\medskip

**Host command packet:**

\medskip

\begin{bytefield}[bitwidth=\widthof{upperbyte~},endianness=little]{3}
  \bitheader{0-2} \\
  \bitbox{1}{0x70} & \bitbox{1}{get=0 set=1} & \bitbox{1}{on=1 off=0} \\
\end{bytefield}


To get the state of the LED, byte 1 is 0.
To set the state of the LED, byte 1 is non-zero, and byte 2 turns the LED off if 0, and on otherwise.

\medskip

**Device response packet:**

\medskip

\begin{bytefield}[bitwidth=\widthof{upperbyte~},endianness=little]{2}
  \bitheader{0-1} \\
  \bitbox{1}{0xF0} & \bitbox{1}{LED \\ State} \\
\end{bytefield}

LED state = 0 if LED is off, non-zero if LED is on.

\pagebreak

## `PFX_CMD_WRITE_SPI`

This message allows the host to perform a write command over the SPI bus connected to the flash memory.  This permits very low level access to the flash memory device for test and debug purposes.

\medskip

**Host command packet:**

\medskip

\begin{bytefield}[bitwidth=\widthof{0xFF~},endianness=little]{16}
  \bitheader{0-15} \\
  \bitbox{1}{0x72} & \bitbox{1}{\tiny num Bytes} & \bitbox{14}{SPI data bytes}\\
  \bitbox[]{16}{$\vdots$ \\[1ex]} \\
  \bitheader[lsb=48]{48-63} \\
  \wordbox{1}{SPI data bytes (up to 62)} \\
\end{bytefield}

`numBytes(n)` specifies how many payload SPI bytes are contained in this packet (<=62)
each byte in the desired SPI transfer follows up to the specified numBytes.

\medskip

**Device response packet:**

\medskip

\begin{bytefield}[bitwidth=\widthof{0xFF~},endianness=little]{1}
  \bitheader{0} \\
  \bitbox{1}{0xF2} \\
\end{bytefield}

\pagebreak


## `PFX_CMD_READ_SPI`

This message allows the host to perform a write command over the SPI bus and read back a corresponding SPI response.  This permits very low level access to the flash memory device for test and debug purposes.

\medskip

**Host command packet:**

\medskip

\begin{bytefield}[bitwidth=\widthof{0xFF~},endianness=little]{16}
  \bitheader{0-15} \\
  \bitbox{1}{0x73} & \bitbox{1}{\tiny num Bytes (n)} & \bitbox{1}{\tiny Rx num Bytes (m)} \bitbox{13}{SPI data bytes}\\
  \bitbox[]{16}{$\vdots$ \\[1ex]} \\
  \bitheader[lsb=48]{48-63} \\
  \wordbox{1}{SPI data bytes (up to 61)} \\
\end{bytefield}

`numBytes(n)` specifies how many payload SPI bytes are contained in this packet (<=61)

`numBytes(m)` specifies how many response SPI bytes are expected in return (<=62) each byte in the desired SPI transfer follows up to the specified numBytes.

\medskip

**Device response packet:**

\medskip

\begin{bytefield}[bitwidth=\widthof{0xFF~},endianness=little]{16}
  \bitheader{0-15} \\
  \bitbox{1}{0xF3} & \bitbox{1}{\tiny num Bytes (m)} & \bitbox{14}{Received SPI data bytes}\\
  \bitbox[]{16}{$\vdots$ \\[1ex]} \\
  \bitheader[lsb=48]{48-63} \\
  \wordbox{1}{Received SPI data bytes (up to 62)} \\
\end{bytefield}

`numBytes(m)` specifies how many response payload SPI bytes are contained in this packet (<=62)

\pagebreak


## `PFX_CMD_WRITE_I2C`

This message allows the host to perform a write command over the I2C bus. This permits very low level access to connected I2C devices such as the audio DSP/DAC for test and debug purposes.

\medskip

**Host command packet:**

\medskip

\begin{bytefield}[bitwidth=\widthof{ADDRESS~},endianness=little]{4}
  \bitheader{0-3} \\
  \bitbox{1}{0x74} & \bitbox{1}{Dev Address} & \bitbox{1}{Reg Address} & \bitbox{1}{Data}\\
\end{bytefield}

`Dev Address` is the I2C 7-bit device address of the audio DSP/DAC device.  Normally this is 0x30 for the Texas Instruments TLV320DAC3120 fitted to the PFx Brick.

`Reg Address` is the address of the register within the I2C device that is desired to be accessed.

`Data` is the value to write to the specified I2C register.

\medskip

**Device response packet:**

\medskip

\begin{bytefield}[bitwidth=\widthof{ADDRESS~},endianness=little]{1}
  \bitheader{0} \\
  \bitbox{1}{0xF4} \\
\end{bytefield}

\pagebreak

## `PFX_CMD_READ_I2C`

This message allows the host to read a device register over the I2C bus. This permits very low level access to connected I2C devices such as the audio DSP/DAC for test and debug purposes.

\medskip

**Host command packet:**

\medskip

\begin{bytefield}[bitwidth=\widthof{ADDRESS~},endianness=little]{3}
  \bitheader{0-2} \\
  \bitbox{1}{0x75} & \bitbox{1}{Dev Address} & \bitbox{1}{Reg Address} \\
\end{bytefield}

`Dev Address` is the I2C 7-bit device address of the audio DSP/DAC device.  Normally this is 0x30 for the Texas Instruments TLV320DAC3120 fitted to the PFx Brick.

`Reg Address` is the address of the register within the I2C device that is desired to be accessed.

\medskip

**Device response packet:**

\medskip

\begin{bytefield}[bitwidth=\widthof{Bytes~},endianness=little]{16}
  \bitheader{0-15} \\
  \bitbox{1}{0xF5} & \bitbox{1}{\small num Bytes (m)} & \bitbox{14}{Received I2C data bytes}\\
  \bitbox[]{16}{$\vdots$ \\[1ex]} \\
  \bitheader[lsb=48]{48-63} \\
  \wordbox{1}{Received I2C data bytes (up to 62)} \\
\end{bytefield}

`numBytes(m)` specifies how many response payload I2C bytes are contained in this packet (<=62)

\pagebreak


## `PFX_CMD_READ_FLASH`

This message allows the host to read back the contents of the flash memory device starting at specified address up to 63 additional byte locations.

\medskip

**Host command packet:**

\medskip

\begin{bytefield}[bitwidth=\widthof{Address~},endianness=little]{6}
  \bitheader{0-5} \\
  \bitbox{1}{0x76} & \bitbox{4}{Address[31:0]} & \bitbox{1}{\small numBytes n} \\
\end{bytefield}

`Address[31:0]` is a 32-bit byte aligned address

`numBytes(n)` specifies how many bytes to read starting at address (1<=n<64)

\medskip

**Device response packet:**

\medskip

\begin{bytefield}[bitwidth=\widthof{0xFF~},endianness=little]{16}
  \bitheader{0-15} \\
  \bitbox{1}{0xF6} & \bitbox{15}{Flash data bytes} \\
  \bitbox[]{16}{$\vdots$ \\[1ex]} \\
  \bitheader[lsb=48]{48-63} \\
  \wordbox{1}{ Flash data bytes } \\
\end{bytefield}

byte 1 is data as read from `Address[31:0]`
byte 2 is data as read from `Address[31:0]+1` and so on

\pagebreak

## `PFX_CMD_GET_IRRX_STATUS`

This command retreives detailed low level data from the IR receiver protocol processor. This message may or may not be supported for a particular PFx Brick due to the overhead required to capture the data. The return message from the PFx Brick will indicate if there is valid data available.

\medskip

**Host command packet:**

\medskip

\begin{bytefield}[bitwidth=\widthof{0xAA~},endianness=little]{1}
  \bitheader{0} \\
  \bitbox{1}{0x77} \\
\end{bytefield}

\medskip

**Device response packet:**

\medskip

\begin{bytefield}[bitwidth=\widthof{TIMEOUT~},endianness=little]{6}
  \bitheader[lsb=0]{0-5}  \\
  \bitbox{1}{0xF7} & \bitbox{1}{Status} & \bitbox{2}{IR Data} & \bitbox{2}{Prev IR Data} \\
\end{bytefield}

\begin{bytefield}[bitwidth=\widthof{TIMEOUT~},endianness=little]{8}
  \bitheader[lsb=6]{6-13}  \\
  \bitbox{2}{Timeout Count} & \bitbox{2}{LRC Error Count} & \bitbox{2}{Unknown Count} & \bitbox{2}{Start Too Short} \\
\end{bytefield}

\begin{bytefield}[bitwidth=\widthof{TIMEOUT~},endianness=little]{8}
  \bitheader[lsb=14]{14-21}  \\
  \bitbox{2}{Start Too Long} & \bitbox{2}{Bit Too Short} & \bitbox{2}{Bit Too Long} & \bitbox{2}{Bit Too Long Idx} \\
\end{bytefield}

\begin{bytefield}[bitwidth=\widthof{TIMEOUT~},endianness=little]{8}
  \bitheader[lsb=22]{22-29}  \\
  \bitbox{2}{Good Start Len} & \bitbox{2}{Prev Good Start Len} & \bitbox{2}{Bad Start Len} & \bitbox{2}{Prev Bad Start Len} \\
\end{bytefield}

`Status` is 1 if IR protocol data is available in bytes 6-29 contained in this message.  If `Status` is 0, then bytes 6-29 do not contain valid data since it is unsupported by the version of PFx Brick queried.

The `IR Data` and `Prev IR Data` fields are always valid independent of the value of `Status`.

\pagebreak

## `PFX_CMD_GET_BT_STATUS`

This command gets the operational status of the Bluetooth interface module.

**Host command packet:**

\begin{bytefield}[bitwidth=\widthof{PRESENT~},endianness=little]{1}
  \bitheader{0} \\
  \bitbox{1}{0x50} \\
\end{bytefield}

**Device response packet:**

\begin{bytefield}[bitwidth=\widthof{PRESENT~},endianness=little]{3}
  \bitheader[lsb=0]{0-2}  \\
  \bitbox{1}{0xD0} & \bitbox{1}{Present} & \bitbox{1}{Sleep} \\
\end{bytefield}

`Present` = 0 if no Bluetooth interface is installed, 1 = Bluetooth interface available

`Sleep` = 0 if Bluetooth module is active, 1 = Bluetooth module is in power saving sleep mode

## `PFX_CMD_SET_BT_POWER`

This command sets the power mode of the Bluetooth interface module.

**Host command packet:**

\begin{bytefield}[bitwidth=\widthof{PRESENT~},endianness=little]{2}
  \bitheader{0-1} \\
  \bitbox{1}{0x51} & \bitbox{1}{Sleep} \\
\end{bytefield}

`Sleep` = 1 puts the Bluetooth interface module into low power sleep mode and disables the Bluetooth module.  Setting `Sleep` to 0 wakes up the Bluetooth module for normal operation.

**Device response packet:**

\begin{bytefield}[bitwidth=\widthof{PRESENT~},endianness=little]{1}
  \bitheader[lsb=0]{0}  \\
  \bitbox{1}{0xD1} \\
\end{bytefield}

\pagebreak

## `PFX_CMD_SEND_BT_UART`

This command sends an ASCII message to the Bluetooth interface module UART.

**Host command packet:**

\begin{bytefield}[bitwidth=\widthof{0x72~},endianness=little]{16}
  \bitheader{0-15} \\
  \bitbox{1}{0x52} & \bitbox{1}{\small num Bytes} & \bitbox{14}{UART data bytes}\\
  \bitbox[]{16}{$\vdots$ \\[1ex]} \\
  \bitheader[lsb=48]{48-63} \\
  \wordbox{1}{UART data bytes (up to 62)} \\
\end{bytefield}

`numBytes` specifies how many payload bytes are contained in this packet (<=62)
each byte in the desired UART message follows up to the specified numBytes.

**Device response packet:**

\begin{bytefield}[bitwidth=\widthof{0x72~},endianness=little]{1}
  \bitheader{0} \\
  \bitbox{1}{0xD2} \\
\end{bytefield}

## `PFX_CMD_RECEIVE_BT_UART`

This message reads back the contents of the receive buffer from the Bluetooth module UART.

**Host command packet:**

\begin{bytefield}[bitwidth=\widthof{0xAA~},endianness=little]{1}
  \bitheader{0} \\
  \bitbox{1}{0x53} \\
\end{bytefield}

**Device response packet:**

\begin{bytefield}[bitwidth=\widthof{0xD3~},endianness=little]{16}
  \bitheader{0-15} \\
  \bitbox{1}{0xD3} & \bitbox{1}{\small num Bytes} & \bitbox{14}{Received data bytes}\\
  \bitbox[]{16}{$\vdots$ \\[1ex]} \\
  \bitheader[lsb=48]{48-63} \\
  \wordbox{1}{Received data bytes (up to 62)} \\
\end{bytefield}

`numBytes` specifies how many bytes are contained in this packet (<=62)

\pagebreak

## `PFX_CMD_SET_NOTIFCATIONS`

This message configures the notification service in the PFx Brick.

**Host command packet:**

\begin{bytefield}[bitwidth=\widthof{Action~},endianness=little]{2}
  \bitheader{0-1} \\
  \bitbox{1}{0x60} & \bitbox{1}{Flags} \\
\end{bytefield}

A detailed description of the `Flags` field can be found in section \ref{notifications} of this document.


**Device response packet:**

\begin{bytefield}[bitwidth=\widthof{Action~},endianness=little]{1}
  \bitheader{0} \\
  \bitbox{1}{0xE0} \\
\end{bytefield}

\pagebreak

## `PFX_MSG_NOTIFICATION`

These messages are sent asynchronously from the PFx Brick after notifications have been configured by a connected host using the `PFX_CMD_SET_NOTIFCATIONS` command.  Each notification message contains information about one notification event.  Therefore, if the host subscribes to two or more notifcations, then multiple notification messages can be expected from the PFx Brick, one or more for each event.  Unlike the command to set notifications which represent the logical-OR of multiple notifications, the notification messages themselves are sent individually, one for each desired notification.

The format of the notification message from the PFx Brick is as follows:

\medskip
\begin{bytefield}[bitwidth=\widthof{NOTIFICATION~},endianness=little]{3}
  \bitheader{0-2} \\
  \bitbox{1}{0x61} & \bitbox{1}{Notification} & \bitbox{1}{Data}\\
\end{bytefield}

The `Notification` field represents the notification type. The `Data` field optionally contains extra qualifying data if applicable.

\medskip
\renewcommand{\arraystretch}{1.5}
\begin{tabular}{ | l | l | p{5cm} | }
  \hline
  Notification & MNEMONIC                        & Data \\
  \hline
  0x01 & \lstinline|PFX_NOTIFICATION_AUDIO_PLAY_DONE| & File ID of audio file \\
  0x02 & \lstinline|PFX_NOTIFICATION_AUDIO_PLAY|      & File ID of audio file \\
  0x04 & \lstinline|PFX_NOTIFICATION_MOTORA_CURR_SPD| & Current motor speed \\
  0x08 & \lstinline|PFX_NOTIFICATION_MOTORA_STOP|     & n/a \\
  0x10 & \lstinline|PFX_NOTIFICATION_MOTORB_CURR_SPD| & Current motor speed \\
  0x20 & \lstinline|PFX_NOTIFICATION_MOTORB_STOP|     & n/a \\
  \hline
\end{tabular}

\pagebreak

# Scripting Actions

As of ICD version 3.37 (and PFx Brick firmware versions 1.40+), the ability to execute complex actions and behaviours defined in script files was added.  Script files are simple, human readable text files stored in the PFx Brick file system.  These files conform to a simple script language syntax described later in this document.  The scripting capability can be summarized as follows:

1. Scripts are ASCII text files stored in the PFx Brick file system.
2. Scripts execute one at a time. Executing another script will terminate the current script and start the new one.
3. Scripts can be executed either by using an Event/Action (with the `COMMAND` byte) or with the ICD message `PFX_CMD_RUN_SCRIPT`.
4. Script execution is sequential line-by-line from the start of the file to the end.  At the end, the script will either stop or repeat if a repeat command is the last line.
5. Script lines with bad syntax are ignored and script execution will continue to the next line.

## Loading Scripts

Script files can be loaded on to the PFx Brick using the PFx App or by using other 3rd party software to copy files from a host PC to the PFx Brick.  A script file will have a name and file ID on the PFx Brick file system.  The unique file ID must be known in order to execute a script (see the file system section for more information).

Creating script files or making changes to a script must be made on a host PC using any standard text editor (e.g. Windows Notepad, macOS Text Editor, etc.)  To modify a script file, the old one must be removed from the PFx Brick file system and then replaced with a new copy (with the same file ID).

## Executing Scripts

Script files can be executed in one of two ways:

1. Using an Event/Action
2. Using the `PFX_CMD_RUN_SCRIPT` ICD message via USB or BLE.

### Event/Action Script Execution

The Event/Action data structure `COMMAND` byte (0) can be set to `COMMAND_RUN_SCRIPT` (0x09) and the script file ID can be specified in the `SOUND_FILE_ID` byte (13).  When a IR remote action is configured this way, it will trigger the execution of the specified script file.  Therefore, a simple event from a remote control can trigger a very complex sequence of actions defined by the script.

### ICD Message

The `PFX_CMD_RUN_SCRIPT` ICD message can be sent to the PFx Brick via a USB or BLE connected host to trigger the execution of a script file.  A unique file ID must be specified in the message to indicate which script file to execute.

## Script Syntax

The PFx Brick script language syntax is a simple human readable free form text file format.  Script files can contain comments and arbitrary amounts of whitespace in addition to the recognized script keywords.  Script file execution is sequential and proceeds line by line from the start of the file to the end.  This implies that all logical script commands must be terminated with a either a linefeed (0x0A) and/or carriage return character (0x0D).

\medskip

\lstset{language=pfx}

### Comments

Comment lines start with either a `#` character (similar to python) or `//` characters (similar to C++). Comments should not be used in line with a command.

~~~
# Valid comment
// Another valid comment
light 1 on  # not a valid comment location
~~~

### Keywords

The script syntax uses case sensitive keyword commands and specifiers.  There are several primary keywords which act as commands and many secondary keywords used for specifying sub-commands, parameters values and options.

The primary keyword commands are as follows:

~~~
light channels commands
motor channels commands
sound commands
ir parameters
wait parameters
repeat
run
stop
~~~

The secondary command and parameter keywords are as follows:

~~~
play, fade, all, on, off, flash, loop, left, right, up, down,
ch, speed, fx, vol, bass, treble, bright, joy, beep, button
~~~

\pagebreak

### Numeric Values

Many commands and options require specified numeric quantities.  The script syntax supports both integer and decimal values.  The following are examples of valid numeric quantities:

~~~
0 127 -55 0.010 35.75 -90.5
~~~

Additionally, integer values may be specified in hexadecimal (base16) prefixed with the characters `0x`.

~~~
0x0 0xABCD 0x32
~~~


For commands which support a list of values, a list is specified as a group of comma separated numbers enclosed in matching square brackets:

~~~
[0, 1, 2, 3]
~~~

### Strings

Some commands also support the use of strings--typically for specifying items such as filenames.  Strings are UTF-8 formatted and enclosed within double quotations marks \lstinline|"|.

~~~
"This is a string"
~~~


\pagebreak

## Command Reference

\begin{tabular}{  p{15cm}   }
\makecell{
\hline
\\
\bfseries{Light Commands} \\
\\
\lstinline|light channels commands| \\
\\
\lstinline|channels| can be specified as a single channel number 1-8, a list of channels enclosed with \\
\Verb|[]| parenthesis, or the keyword \lstinline|all| \\
\\
\lstinline|commands| are a combination of the following keywords and values: \\
\lstinline|on| - turn on light channel(s) \\
\lstinline|off| - turn off light channel(s) \\
\lstinline|fade <time>| - fade time (0 to 10.0 seconds). \\
\lstinline|flash <ontime> [offtime]| - periodic flashing light (0.05 to 60.0 seconds) \\
\lstinline|bright <value>| - set brightness (0 to 255) \\
\lstinline|fx <id> [parameters]| - performs light action \lstinline|<id>| as \lstinline|LIGHT_FX_ID| with specified parameters \\
if \lstinline|channels| = \lstinline|all| then \lstinline|<id>| is a combo id \\
\\
\lstinline|light 1 on| \\
\lstinline|light [1,4,8] off fade 0.5| \\
\lstinline|light [2,4] flash 0.1 0.4 fade 0.1| \\
\lstinline|light all bright 128| \\
\lstinline|light [6,7] fx 0x0C [1,0,3,0,0]| \\
\\
\hline
\\
\bfseries{Sound Commands} \\
\\
\lstinline|sound command|\\
\\
\lstinline|command| is one of the following keywords: \\
\lstinline|play fileID| - start playback of \lstinline|fileID| \\
\lstinline|stop fileID| - stop playback of \lstinline|fileID| \\
\lstinline|play fileID| \lstinline|repeat| - continuous playback of \lstinline|fileID| \\
\lstinline|play fileID| \lstinline|loop <value>| - plays \lstinline|fileID| for \lstinline|value| times \\
\lstinline|vol <value>| - set volume (0 to 255) \\
\lstinline|bass <value>| - set bass (-20 to 20) \\
\lstinline|beep| - short beep sound \\
\lstinline|treble <value>| - set treble (-20 to 20) \\
\lstinline|fx fileID <id> [parameters]| - performs sound action \lstinline|<id>| as \lstinline|SOUND_FX_ID| with \\
specified parameters \\
\\
\lstinline|fileID| can be specified either as a numeric \\
file ID or string containing the filename.\\
\\
\lstinline|sound play 3 loop 5| \\
\lstinline|sound play "Siren1.wav"| \\
\lstinline|sound vol 160| \\
\lstinline|sound treble -6| \\
\lstinline|sound fx 9 0x04 0 0| \\
\\
\hline
}
\end{tabular}
\pagebreak

\begin{tabular}{  p{15cm}   }
\makecell{
\hline
\\
\bfseries{Motor Commands} \\
\lstinline|motor channels command| \\
\\
\lstinline|channels| can be specified as a single channel number 1 or 2 (or as \lstinline|a| and \lstinline|b|), a list of channels \\
enclosed with \Verb|[]| parenthesis, or the keyword \lstinline|all| \\
\\
\lstinline|command| is one of the following keywords: \\
\lstinline|stop| - stop motor channel(s) \\
\lstinline|speed <value>| - motor speed (-255 to 255), +speed is forward, -speed is reverse direction \\
\lstinline|servo <value>| - servo motor angle (-90 to 90) \\
\lstinline|fx <id> [parameters]| - performs motor action \lstinline|<id>| as \lstinline|MOTOR_FX_ID| with specified parameters \\
\\
\lstinline|motor all stop| \\
\lstinline|motor a speed -50| \\
\lstinline|motor 2 servo 45| \\
\lstinline|motor 1 fx 0x07 0x03 0| \\
\\
\hline
\\
\bfseries{IR Commands} \\
\\
\lstinline|ir on| - activates the IR sensor \\
\lstinline|ir off| - disables the IR sensor \\
\\
\hline
\\
\bfseries{Execution Control} \\
\\
Delay execution and wait for event to resume: \\
\lstinline|wait <time>| - pause (0.05 to unlimited sec) \\
\lstinline|wait sound fileID| - pause execution until sound file \lstinline|fileID| has stopped playing \\
\lstinline|wait ir parameters| - pause execution until IR event has been received \\
where \lstinline|parameters| can be any combination of: \\
\lstinline|joy| - joystick remote, \lstinline|speed| - speed remote, \lstinline|up,down,left,right,button| - remote actions \\
\lstinline|ch <value>| - IR channel \\
\\
Redirect execution to same or different script: \\
\lstinline|repeat| - repeat execution of current script \\
\lstinline|run fileID| - execute script with \lstinline|fileID| \\
\lstinline|stop| - stops the script at the current line \\
\\
\lstinline|wait 3.0| \\
\lstinline|wait sound 5| \\
\lstinline|wait ir joy left up| \\
\lstinline|wait ir speed ch 4 left button| \\
\lstinline|stop| \\
\lstinline|run 3| \\
\lstinline|run "MyScript.txt"| \\
\\
\hline
} \\
\end{tabular}

\pagebreak

## Examples

~~~
# Traffic light sequence
#
# Ch 1: Red, Ch 2: Yellow, Ch 3: Green
# Ch 4: Don't Walk, Ch 5: Walk
# reset all light channels
light all off
# Red phase
light [1,4] on
light [2,3,5] off fade 0.2
wait 8.0
# Green phase
light [1,4] off fade 0.2
light [3,5] on
wait 8.0
# Pedestrian crossing warning
light 5 off fade 0.1
light 4 flash 0.4 fade 0.1
wait 5
# Yellow
light 3 off fade 0.2
light [2,4] on
wait 4
# Start the sequence again
repeat
~~~

~~~
# Motorized musical procession
#
# Vehicle with motor, lights and music; Triggered by IR remote

# Start with everything off
light all off
sound stop all
motor all off

# Wait for joystick remote ch 1 right up
wait ir joy ch 1 right up

# Play sound and move
motor a speed 30
light all on
sound play "MySong.wav"

# Wait until song is finished, stop and repeat
wait sound "MySong.wav"
motor a stop
repeat
~~~

\pagebreak

\lstset{language=}

# Event/Action Data Structures

The fundamental behaviour of the PFx Brick is to perform actions in response to received IR and/or Bluetooth interface events. Actions are encoded in a data structure called the event look up table (LUT). The actions performed are indexed by a corresponding event trigger into the event LUT, i.e. the event LUT is "addressed" by message events. This section will describe event LUT and the many associated fields and parameters.

## Event Encoding

The events sent by IR remotes and/or Bluetooth interface cue corresponding actions stored in the event look up table.  These actions include controlling motors, light f/x and sound.  Some event actions may depend on the current state of other items, e.g. the change of direction on a motor channel may depend on its current speed.

The event LUT address format used internally by the PFx Brick is as follows:
\bigskip

\begin{bytefield}[bitwidth=\widthof{Reserved~},endianness=big]{8}
  \bitheader{0-7} \\
  \bitbox{1}{Reserved} & \bitbox{5}{Event ID} & \bitbox{2}{IR Channel} \\
\end{bytefield}


**LEGO® Power Funcitons IR Remotes**
\medskip
\renewcommand{\arraystretch}{1.5}
\begin{tabular}{ | c | c | l | }
  \hline
  Address & Event ID & MNEMONIC \\
  \hline
  0x00-0x03 & 0x00 & \lstinline|EVT_8879_TWO_BUTTONS|  \\
  0x04-0x07 & 0x01 & \lstinline|EVT_8879_LEFT_BUTTON|  \\
  0x08-0x0B & 0x02 & \lstinline|EVT_8879_RIGHT_BUTTON| \\
  0x0C-0x0F & 0x03 & \lstinline|EVT_8879_LEFT_INC|     \\
  0x10-0x13 & 0x04 & \lstinline|EVT_8879_LEFT_DEC|     \\
  0x14-0x17 & 0x05 & \lstinline|EVT_8879_RIGHT_INC|    \\
  0x18-0x1B & 0x06 & \lstinline|EVT_8879_RIGHT_DEC|    \\
  0x1C-0x1F & 0x07 & \lstinline|EVT_8885_LEFT_FWD|     \\
  0x20-0x23 & 0x08 & \lstinline|EVT_8885_LEFT_REV|     \\
  0x24-0x27 & 0x09 & \lstinline|EVT_8885_RIGHT_FWD|    \\
  0x28-0x2B & 0x0A & \lstinline|EVT_8885_RIGHT_REV|    \\
  0x2C-0x2F & 0x0B & \lstinline|EVT_8885_LEFT_CTROFF|  \\
  0x30-0x33 & 0x0C & \lstinline|EVT_8885_RIGHT_CTROFF|  \\
  0x34-0x37 & 0x0D & \lstinline|EVT_EV3_BEACON| \\
  \hline
\end{tabular}

\pagebreak

Following the Power Functions IR remote events, there are special event LUT entries reserved for other purposes as follows:
\bigskip
\renewcommand{\arraystretch}{1.5}
\begin{tabular}{ | c | c | l | p{6.5cm} | }
  \hline
  Address & Event ID & MNEMONIC & Description \\
  \hline
  0x38 & 0x0E & \lstinline|EVT_TEST_EVENT|      & Used for testing actions sent by a USB connected host \\
  0x3C & 0x0F & \lstinline|EVT_STARTUP_EVENT1|  & Used for storing start-up actions performed after power on \\
  0x3D & 0x0F & \lstinline|EVT_STARTUP_EVENT2|  &   \\
  0x3E & 0x0F & \lstinline|EVT_STARTUP_EVENT3|  &   \\
  0x3F & 0x0F & \lstinline|EVT_STARTUP_EVENT4|  &   \\
  0x40 & 0x10 & \lstinline|EVT_STARTUP_EVENT5|  &   \\
  0x41 & 0x10 & \lstinline|EVT_STARTUP_EVENT6|  &   \\
  0x42 & 0x10 & \lstinline|EVT_STARTUP_EVENT7|  &   \\
  0x43 & 0x10 & \lstinline|EVT_STARTUP_EVENT8|  &   \\
  \hline
\end{tabular}
\medskip

**LEGO® RC Train IR Remote**

The RC Train remote was black with 4 yellow buttons.  The buttons are labelled Up, Down, Horn, and Stop.  A channel selector switch allows you to select channels labelled 1, 2, 3, 1+2+3.  These channels correspond to 0, 1, 2, 3 respectively within the event LUT.

\medskip
\renewcommand{\arraystretch}{1.5}
\begin{tabular}{ | c | c | l | }
  \hline
  Address & Event ID & MNEMONIC \\
  \hline
  0x50-0x53 & 0x14 & \lstinline|EVT_RCTRAIN_UP|   \\
  0x54-0x57 & 0x15 & \lstinline|EVT_RCTRAIN_DOWN| \\
  0x58-0x5B & 0x16 & \lstinline|EVT_RCTRAIN_STOP| \\
  0x5C-0x5F & 0x17 & \lstinline|EVT_RCTRAIN_HORN|   \\
  \hline
\end{tabular}
\medskip

\pagebreak

**Sparkfun COM-11759 Mini IR Remote**
\medskip

\renewcommand{\arraystretch}{1.5}
\begin{tabular}{ | c | c | c | l |  }
  \hline
  Address & Event ID & Ch & MNEMONIC \\
  \hline
  0x60 & 0x18 & 0 & \lstinline|EVT_SPARKFUN_POWER| \\
  0x61 & 0x18 & 1 & \lstinline|EVT_SPARKFUN_A| \\
  0x62 & 0x18 & 2 & \lstinline|EVT_SPARKFUN_B| \\
  0x63 & 0x18 & 3 & \lstinline|EVT_SPARKFUN_C| \\
  0x64 & 0x19 & 0 & \lstinline|EVT_SPARKFUN_UP| \\
  0x65 & 0x19 & 1 & \lstinline|EVT_SPARKFUN_DOWN| \\
  0x66 & 0x19 & 2 & \lstinline|EVT_SPARKFUN_LEFT| \\
  0x67 & 0x19 & 3 & \lstinline|EVT_SPARKFUN_RIGHT| \\
  \hline
\end{tabular}
\medskip

**Adafruit 389 Mini IR Remote**
\medskip

\renewcommand{\arraystretch}{1.5}
\begin{tabular}{ | c | c | c | l |  }
  \hline
  Address & Event ID & Ch & MNEMONIC \\
  \hline
  0x68 & 0x1A & 0 & \lstinline|EVT_ADAFRUIT_VOLDOWN| \\
  0x69 & 0x1A & 1 & \lstinline|EVT_ADAFRUIT_PLAY| \\
  0x6A & 0x1A & 2 & \lstinline|EVT_ADAFRUIT_VOLUP| \\
  0x6B & 0x1A & 3 & \lstinline|EVT_ADAFRUIT_SETUP| \\
  0x6C & 0x1B & 0 & \lstinline|EVT_ADAFRUIT_STOP| \\
  0x6D & 0x1B & 1 & \lstinline|EVT_ADAFRUIT_UP| \\
  0x6E & 0x1B & 2 & \lstinline|EVT_ADAFRUIT_DOWN| \\
  0x6F & 0x1B & 3 & \lstinline|EVT_ADAFRUIT_LEFT| \\
  0x70 & 0x1C & 0 & \lstinline|EVT_ADAFRUIT_RIGHT| \\
  0x71 & 0x1C & 1 & \lstinline|EVT_ADAFRUIT_ENTER| \\
  0x72 & 0x1C & 2 & \lstinline|EVT_ADAFRUIT_REPEAT| \\
  0x73 & 0x1C & 3 & \lstinline|EVT_ADAFRUIT_0| \\
  0x74 & 0x1D & 0 & \lstinline|EVT_ADAFRUIT_1| \\
  0x75 & 0x1D & 1 & \lstinline|EVT_ADAFRUIT_2| \\
  0x76 & 0x1D & 2 & \lstinline|EVT_ADAFRUIT_3| \\
  0x77 & 0x1D & 3 & \lstinline|EVT_ADAFRUIT_4| \\
  0x78 & 0x1E & 0 & \lstinline|EVT_ADAFRUIT_5| \\
  0x79 & 0x1E & 1 & \lstinline|EVT_ADAFRUIT_6| \\
  0x7A & 0x1E & 2 & \lstinline|EVT_ADAFRUIT_7| \\
  0x7B & 0x1E & 3 & \lstinline|EVT_ADAFRUIT_8| \\
  0x7C & 0x1F & 0 & \lstinline|EVT_ADAFRUIT_9| \\
  \hline
\end{tabular}




\pagebreak

## Action Encoding

The event LUT stores encoded actions in a multi-byte data structure. The actions performed by the PFx Brick are grouped into the following categories:

1. Motor Actions
2. Single Light F/X Output Actions
3. Combo Light F/X Output Actions
4. Sound F/X Actions

Note that these actions can be combined to respond to a single event, e.g. play a sound with a lighting effect, actuate multiple lights as a group, etc.

The encoded action data structure is composed of 16 bytes as follows:
\bigskip

\begin{bytefield}[bitwidth=\widthof{COMBO~},endianness=big]{9}
  \bitheader{0-7} \\
  \bitbox{1}{0} & \bitbox{8}{COMMAND} \\
  \bitbox{1}{1} & \bitbox{4}{MOTOR\_ACTION\_ID} & \bitbox{4}{MOTOR\_MASK} \\
  \bitbox{1}{2} & \bitbox{8}{MOTOR\_PARAM1} \\
  \bitbox{1}{3} & \bitbox{8}{MOTOR\_PARAM2} \\
  \bitbox{1}{4} & \bitbox{1}{COMBO} & \bitbox{7}{LIGHT\_FX\_ID} \\
  \bitbox{1}{5} & \bitbox{8}{LIGHT\_OUTPUT\_MASK} \\
  \bitbox{1}{6} & \bitbox{8}{LIGHT\_PF\_OUTPUT\_MASK} \\
  \bitbox{1}{7} & \bitbox{8}{LIGHT\_PARAM1} \\
  \bitbox{1}{8} & \bitbox{8}{LIGHT\_PARAM2} \\
  \bitbox{1}{9} & \bitbox{8}{LIGHT\_PARAM3} \\
  \bitbox{1}{10} & \bitbox{8}{LIGHT\_PARAM4} \\
  \bitbox{1}{11} & \bitbox{8}{LIGHT\_PARAM5} \\
  \bitbox{1}{12} & \bitbox{8}{SOUND\_FX\_ID} \\
  \bitbox{1}{13} & \bitbox{8}{SOUND\_FILE\_ID} \\
  \bitbox{1}{14} & \bitbox{8}{SOUND\_PARAM1} \\
  \bitbox{1}{15} & \bitbox{8}{SOUND\_PARAM2} \\
\end{bytefield}

\pagebreak

When an event is triggered (e.g. from an IR remote, or a `PFX_CMD_TEST_ACTION` message is received via USB or BLE), the PFx Brick performs the action specified by the associated action data structure.  The action is processed sequentially starting from the first byte `COMMAND`.

1. If `COMMAND` in byte 0 is non-zero, the specified command is executed and **rest of the action data structure is ignored**. One execption is when the `COMMAND` byte is specified as `COMMAND_RUN_SCRIPT`; in this case the PFx Brick will execute the script file specified in the `SOUND_FILE_ID` byte (13).
2. If `MOTOR_MASK` in byte 1 is non-zero, the motor action specified by `MOTOR_ACTION_ID` is performed using the parameters `MOTOR_PARAM1` and `MOTOR_PARAM2`.
3. If `LIGHT_FX_ID` in byte 4 is non-zero, the light effect action is performed on the light outputs specified by `LIGHT_OUTPUT_MASK` and `LIGHT_PF_OUTPUT_MASK` using the parameters in `LIGHT_PARAM1-5`.
4. If `SOUND_FX_ID` in byte 12 is non-zero, the sound effect action is performed with the sound file specified by `SOUND_FILE_ID` using parameters `SOUND_PARAM1` and `SOUND_PARAM2`.


\pagebreak

### `COMMAND`

\begin{bytefield}[bitwidth=\widthof{COMBO~},endianness=big]{9}
  \bitheader{0-7} \\
  \bitbox{1}{0} & \bitbox{8}{COMMAND} \\
\end{bytefield}

The `COMMAND` byte is used to perform special actions not related to the core actions related to motors, lights and sound.  The supported commands are listed as follows:
\bigskip

\renewcommand{\arraystretch}{1.5}
\begin{tabular}{ | c | l | p{8.2cm} | }
  \hline
  ID & MNEMONIC & Description \\
  \hline
  0x00 & \lstinline|COMMAND_NONE|                 & No action  \\
  0x01 & \lstinline|COMMAND_ALL_OFF|             & Shut off all motor channels, light output ports, and stop all audio playback \\
  0x02 & \lstinline|COMMAND_IR_LOCKOUT_ON|      & Activate IR receiver lockout, ignores IR receiver packets \\
  0x03 & \lstinline|COMMAND_IR_LOCKOUT_OFF|     & Deactivate IR receiver lockout, resumes processing of IR receiver \\
  0x04 & \lstinline|COMMAND_IR_LOCKOUT_TOGGLE|  & Toggle the state of the IR lockout mode \\
  0x05 & \lstinline|COMMAND_ALL_MOTORS_OFF|     & Turn off all motor channels \\
  0x06 & \lstinline|COMMAND_ALL_LIGHTS_OFF|     & Turn off all lighting channels \\
  0x07 & \lstinline|COMMAND_ALL_AUDIO_OFF|      & Stop all audio playback \\
  0x08 & \lstinline|COMMAND_RESTART|              & Stop all current actions, and restart with all STARTUP actions \\
  0x09 & \lstinline|COMMAND_RUN_SCRIPT|          & Execute a script file specified by the file ID in the \lstinline|SOUND_FILE_ID| byte (13) \\
  \hline
\end{tabular}

\pagebreak



### `MOTOR_ACTION_ID`

\begin{bytefield}[bitwidth=\widthof{COMBO~},endianness=big]{9}
  \bitheader{0-7} \\
  \bitbox{1}{1} & \bitbox{4}{MOTOR\_ACTION\_ID} & \bitbox{4}{MOTOR\_MASK} \\
\end{bytefield}

The `MOTOR_ACTION_ID` is a 4-bit encoded value which occupies bits [7:4] and specifies the type of action to apply to the motor channel(s) specified in the `MOTOR_MASK` bits.  The `MOTOR_ACTION_ID` bits are defined as follows:
\bigskip

\renewcommand{\arraystretch}{1.5}
\begin{tabular}{ | c | l | p{7.7cm} | }
  \hline
  ID & MNEMONIC & Description \\
  \hline
  0x00 & \lstinline|MOTOR_ESTOP|                  & Motor braked to stop immediately (emergency stop) \\
  0x01 & \lstinline|MOTOR_STOP|                   & Motor commanded to stop using the configured deceleration rate. \\
  0x02 & \lstinline|MOTOR_INC_SPEED|             & Increase motor speed one step (up to vMax) \\
  0x03 & \lstinline|MOTOR_DEC_SPEED|             & Decrease motor speed one step (clamped to zero) \\
  0x04 & \lstinline|MOTOR_INC_SPEED_BIDIR|      & Increase motor speed one step; passing zero changes direction \\
  0x05 & \lstinline|MOTOR_DEC_SPEED_BIDIR|      & Decrease motor speed one step; passing zero changes direction \\
  0x06 & \lstinline|MOTOR_CHANGE_DIR|            & Change motor direction (motor must be stopped first) \\
  0x07 & \lstinline|MOTOR_SET_SPD|               & Sets the motor speed to specific value \\
  0x08 & \lstinline|MOTOR_SET_SPD_TIMED|        & Sets the motor speed to run for a fixed time \\
  0x09 & \lstinline|MOTOR_OSCILLATE|              & Oscillate motor speed on and off \\
  0x0A & \lstinline|MOTOR_OSCILLATE_BIDIR|       & Oscillate motor speed forward/reverse \\
  0x0B & \lstinline|MOTOR_OSCILLATE_BIDIR_WAIT| & Oscillate motor speed forward/reverse with a wait interval in between \\
  0x0C & \lstinline|MOTOR_RANDOM|                 & Set random motor speed periodically within set speed \\
  0x0D & \lstinline|MOTOR_RANDOM_BIDIR|          & Set random motor speed and direction periodically within set speed \\
  0x0E & \lstinline|MOTOR_SOUND_MODULATED|       & Set motor speed within set speed modulated by sound intensity \\
  0x0F & \lstinline|MOTOR_SET_SERVO|             & Set LEGO Power Functions servo motor position \\
  \hline
\end{tabular}

\pagebreak

### `MOTOR_MASK`

\begin{bytefield}[bitwidth=\widthof{COMBO~},endianness=big]{9}
  \bitheader{0-7} \\
  \bitbox{1}{1} & \bitbox{4}{MOTOR\_ACTION\_ID} & \bitbox{4}{MOTOR\_MASK} \\
\end{bytefield}

Motor actions can be applied to any combination of motor outputs simultaneously, e.g. two or more motors controlled to the same speed.  The `MOTOR_MASK<3:0>` has 4 bits corresponding to motor outputs D,C,B,A respectively.  The initial PFx Brick design has only 2 motor outputs (A & B); however, provision for future expanded versions of the PFx Brick with 4 motor outputs is being accomodated.  A bit value of 1 in each position indicates that the corresponding motor output will be controlled, e.g. `MOTOR_MASK<3:0>=0xA` means that motor outputs D and B will be operated together.

\pagebreak

### `MOTOR_PARAMx`

\begin{bytefield}[bitwidth=\widthof{COMBO~},endianness=big]{9}
  \bitheader{0-7} \\
  \bitbox{1}{2} & \bitbox{8}{MOTOR\_PARAM1} \\
  \bitbox{1}{3} & \bitbox{8}{MOTOR\_PARAM2} \\
\end{bytefield}

The `MOTOR_PARAM1` and `MOTOR_PARAM2` bytes encode parameters which are associated with some of the `MOTOR_ACTION_ID` items.  The definition of `MOTOR_PARAM1` and `MOTOR_PARAM2` is shown in the table below:

\bigskip
\renewcommand{\arraystretch}{1.5}
\begin{tabular}{ | c | l | l | l | }
  \hline
  ID & MNEMONIC & \lstinline|MOTOR_PARAM1| & \lstinline|MOTOR_PARAM2| \\
  \hline
  0x00 & \lstinline|MOTOR_ESTOP|                  &                             &  \\
  0x01 & \lstinline|MOTOR_STOP|                   &                             &  \\
  0x02 & \lstinline|MOTOR_INC_SPEED|             & \lstinline|MOTOR_STEP|   &  \\
  0x03 & \lstinline|MOTOR_DEC_SPEED|             & \lstinline|MOTOR_STEP|   &  \\
  0x04 & \lstinline|MOTOR_INC_SPEED_BIDIR|      & \lstinline|MOTOR_STEP|   &  \\
  0x05 & \lstinline|MOTOR_DEC_SPEED_BIDIR|      & \lstinline|MOTOR_STEP|   &  \\
  0x06 & \lstinline|MOTOR_CHANGE_DIR|            &                         &  \\
  0x07 & \lstinline|MOTOR_SET_SPD|               & \lstinline|MOTOR_SPEED|  &  \\
  0x08 & \lstinline|MOTOR_SET_SPD_TIMED|        & \lstinline|MOTOR_SPEED|  & \lstinline|DURATION| \\
  0x09 & \lstinline|MOTOR_OSCILLATE|              & \lstinline|MOTOR_SPEED|  & \lstinline|MOTOR_PERIOD| \\
  0x0A & \lstinline|MOTOR_OSCILLATE_BIDIR|       & \lstinline|MOTOR_SPEED|  & \lstinline|MOTOR_PERIOD| \\
  0x0B & \lstinline|MOTOR_OSCILLATE_BIDIR_WAIT| & \lstinline|MOTOR_SPEED|  & \lstinline|MOTOR_PERIOD| \\
  0x0C & \lstinline|MOTOR_RANDOM|                 & \lstinline|MOTOR_SPEED|  & \lstinline|MOTOR_PERIOD| \\
  0x0D & \lstinline|MOTOR_RANDOM_BIDIR|          & \lstinline|MOTOR_SPEED|  & \lstinline|MOTOR_PERIOD| \\
  0x0E & \lstinline|MOTOR_SOUND_MODULATED|       & \lstinline|MOTOR_SPEED|  &  \\
  0x0F & \lstinline|MOTOR_SET_SERVO|             & \lstinline|MOTOR_POS|    &  \\
  \hline
\end{tabular}

\pagebreak

#### `MOTOR_SPEED`

The `MOTOR_SPEED` parameter specifies absolute motor speed to be directly applied without intermediate incremental steps.  This parameter is defined as follows:

\medskip
\renewcommand{\arraystretch}{1.25}
\begin{tabular}{ | c | l | l | }
  \hline
  \footnotesize MOTOR\_SPEED & \multicolumn{2}{l|}{Value} \\
  \hline
  0x0 & stopped & \\
  0x1 & 10\%    & \\
  0x2 & 25\%    & \% of maximum \\
  0x3 & 33\%    & speed in the \\
  0x4 & 50\%    & forward direction \\
  0x5 & 67\%    & \\
  0x6 & 75\%    & \\
  0x7 & 100\%   &  \\ \cline{3-3}
  0x8 & stopped & \\
  0x9 & 10\%    & \\
  0xA & 25\%    & \% of maximum \\
  0xB & 33\%    & speed in the \\
  0xC & 50\%    & reverse direction \\
  0xD & 67\%    & \\
  0xE & 75\%    & \\
  0xF & 100\%   & \\
  \hline
\end{tabular}
\medskip

The `MOTOR_SPEED` parameter can also be used to specify a higher resolution set speed.  This is achieved by setting the `MOTOR_SPEED[7]` bit to '1' and using the `MOTOR_SPEED[6]` bit as a direction flag.  `MOTOR_SPEED[5:0]` bits specify absolute speed in either direction. Therefore `MOTOR_SPEED` can be defined as follows for high resolution speed settings:

\renewcommand{\arraystretch}{1.1}
\begin{tabular}{  c  c  c  c  c  c  c  c  }
  \footnotesize 7 & \footnotesize 6 & \footnotesize 5 & \footnotesize 4 & \footnotesize 3 & \footnotesize 2 & \footnotesize 1 & \footnotesize 0 \\
  \hline
  \multicolumn{1}{|c|}{1} & Dir & \multicolumn{6}{|c|}{Speed} \\
  \multicolumn{1}{|c|}{}  & 0=fwd, 1=rev & \multicolumn{6}{|c|}{} \\
  \hline
\end{tabular}
\medskip

This allows for a range of speed settings as follows:
\medskip

\renewcommand{\arraystretch}{1.25}
\begin{tabular}{ | c | l | l | }
  \hline
  \multicolumn{2}{|c|}{\footnotesize MOTOR\_SPEED} & Speed \\
  \hline
  0xBF & 1 0 1 1 \enskip 1 1 1 1 & Maximum speed forward \\
  0xBE & 1 0 1 1 \enskip 1 1 1 0 & \\
  ...  & ...              & \\
  0x81 & 1 0 0 0 \enskip 0 0 0 1 & Minimum speed forward \\
  0x80 & 1 0 0 0 \enskip 0 0 0 0 & stopped \\
  0xC0 & 1 1 0 0 \enskip 0 0 0 0 & stopped \\
  0xC1 & 1 1 0 0 \enskip 0 0 0 1 & Minimum speed reverse \\
  ...  & ...              & \\
  0xFE & 1 1 1 1 \enskip 1 1 1 0 & \\
  0xFF & 1 1 1 1 \enskip 1 1 1 1 & Maximum speed reverse \\
  \hline
\end{tabular}

\pagebreak

#### `MOTOR_STEP`

Motor actions which increment or decrement the motor speed can specify the magnitude of the change with the `MOTOR_STEP` parameter.  It is defined as follows:
\medskip
\renewcommand{\arraystretch}{1.5}
\begin{tabular}{ | c | l | }
  \hline
  \footnotesize MOTOR\_STEP & Value  \\
  \hline
  0x0 & default +/-1 step (highest resolution) \\
  0x1 & 1\%  (100 speed steps) \\
  0x2 & 2\%  (50 speed steps) \\
  0x3 & 3\%  (33 speed steps) \\
  0x4 & 5\%  (20 speed steps) \\
  0x5 & 6\%  (16 speed steps) \\
  0x6 & 10\% (10 speed steps) \\
  0x7 & 20\% (5 speed steps) \\
  0x8 & 25\% (4 speed steps) \\
  0x9 & 33\% (3 speed steps) \\
  0xA & Lego compatible 7 step \\
  0xB & 15 deg (servo motor position increment) \\
  \hline
\end{tabular}

The percentage change in speed is specified as an increment equal to that percentage of full speed.

#### `MOTOR_PERIOD`


The `MOTOR_PERIOD` parameter specifies the time period for oscillating motor actions. This parameter is defined as follows:

\medskip

\begin{bytefield}[bitwidth=\widthof{Reserved~},endianness=big]{8}
  \bitheader{0-7} \\
  \bitbox{4}{OFF Period} & \bitbox{4}{ON Period} \\
\end{bytefield}

For motor actions which have both an on and off interval, they can be specified individually.  The definition of the motor period for both the ON and OFF period are defined as follows:

\medskip
\renewcommand{\arraystretch}{1.5}
\begin{tabular}{ | c | l | c | l |}
  \hline
  Value & Definition & Value & Definition  \\
  \hline
  0x00 & 0.25 sec & 0x08 & 3.0 sec   \\
  0x01 & 0.5 sec  & 0x09 & 4.0 sec   \\
  0x02 & 0.75 sec & 0x0A & 5.0 sec   \\
  0x03 & 1.0 sec  & 0x0B & 10 sec  \\
  0x04 & 1.25 sec & 0x0C & 15 sec  \\
  0x05 & 1.5 sec  & 0x0D & 20 sec  \\
  0x06 & 2.0 sec  & 0x0E & 30 sec  \\
  0x07 & 2.5 sec  & 0x0F & 60 sec  \\
  \hline
\end{tabular}

\pagebreak

#### `DURATION`

The `DURATION` parameter specifies a fixed time interval as follows:
\medskip

\renewcommand{\arraystretch}{1.5}
\begin{tabular}{ | c | l | c | l | }
  \hline
  Value & Definition &  Value & Definition \\
  \hline
  0x0 & 0.5 sec  & 0x8 & 15 sec \\
  0x1 & 1.0 sec  & 0x9 & 20 sec \\
  0x2 & 1.5 sec  & 0xA & 30 sec \\
  0x3 & 2.0 sec  & 0xB & 45 sec \\
  0x4 & 3.0 sec  & 0xC & 60 sec \\
  0x5 & 4.0 sec  & 0xD & 90 sec \\
  0x6 & 5.0 sec  & 0xE & 2 min  \\
  0x7 & 10 sec   & 0xF & 5 min  \\
  \hline
\end{tabular}
\normalsize

#### `MOTOR_POS`

The `MOTOR_POS` parameter specifies the angular position of a LEGO Power Functions servo motor.  This parameter offers a convenient method of specifying the servo positon rather than a corresponding voltage or speed.

\medskip

\renewcommand{\arraystretch}{1.5}
\begin{tabular}{ | c | l | c | l | }
  \hline
  Value & Definition &  Value & Definition \\
  \hline
  0x0 & -90 deg  & 0x8 & 30 deg \\
  0x1 & -75 deg  & 0x9 & 45 deg \\
  0x2 & -60 deg  & 0xA & 60 deg \\
  0x3 & -45 deg  & 0xB & 75 deg \\
  0x4 & -30 deg  & 0xC & 90 deg \\
  0x5 & -15 deg  &     &  \\
  0x6 & 0 deg   &     &  \\
  0x7 & 15 deg &     &  \\
  \hline
\end{tabular}
\normalsize

\pagebreak

### `LIGHT_FX_ID`

\begin{bytefield}[bitwidth=\widthof{COMBO~},endianness=big]{9}
  \bitheader{0-7} \\
  \bitbox{1}{4} & \bitbox{1}{COMBO} & \bitbox{7}{LIGHT\_FX\_ID} \\
\end{bytefield}

Light F/X actions are specified with an ID code which determines the action. There are two main types of light f/x:  single and combination.  Single light actions are applied to individually assigned lighting outputs (specified with the `LIGHT_OUTPUT_MASK` bytes).  Combination light f/x are coordinated to drive an entire group of light outputs in a specific pattern.  These combo light effects are applied to designated light output channels and override their current state when activated.

The `COMBO` bit <7> of the `LIGHT_FX_ID` byte specifies if the light f/x is a single or combo light action when set to 0 or 1 respectively.  Based on the state of `COMBO` bit, the `LIGHT_FX_ID` is interpreted differently.

### `LIGHT_FX_ID` Single Light Actions

When the `COMBO` bit is zero, then the `LIGHT_FX_ID` field is defined as follows:
\bigskip
\renewcommand{\arraystretch}{1.5}
\begin{tabular}{ | c | l | l | }
  \hline
  ID  & MNEMONIC                                     & Description \\
  \hline
  0x01 & \lstinline|LIGHTFX_ON_OFF_TOGGLE|      & Toggle light output on/off                 \\
  0x02 & \lstinline|LIGHTFX_INC_BRIGHTNESS|      & Increase brightness one step               \\
  0x03 & \lstinline|LIGHTFX_DEC_BRIGHTNESS|      & Decrease brightness one step               \\
  0x04 & \lstinline|LIGHTFX_SET_BRIGHTNESS|      & Set brightness to specified level          \\
  0x05 & \lstinline|LIGHTFX_FLASH_50_POS|       & 50\% duty cycle flasher (pos phase)         \\
  0x06 & \lstinline|LIGHTFX_FLASH_50_NEG|       & 50\% duty cycle flasher (neg phase)         \\
  0x07 & \lstinline|LIGHTFX_STROBE_POS|          & strobe light flasher (pos phase)           \\
  0x08 & \lstinline|LIGHTFX_STROBE_NEG|          & strobe light flasher (neg phase)           \\
  0x09 & \lstinline|LIGHTFX_GYRALITE_POS|        & fading MARS/Gyralite flasher (pos phase)   \\
  0x0A & \lstinline|LIGHTFX_GYRALITE_NEG|        & fading MARS/Gyralite flasher (neg phase)   \\
  0x0B & \lstinline|LIGHTFX_FLICKER|              & random flickering light                    \\
  0x0C & \lstinline|LIGHTFX_RANDOM_BLINK|        & random blinking light                      \\
  0x0D & \lstinline|LIGHTFX_PHOTON_TORPEDO|      & photon torpedo effect                      \\
  0x0E & \lstinline|LIGHTFX_LASER_PULSE|         & shooting laser effect                      \\
  0x0F & \lstinline|LIGHTFX_SCIFI_ENGINE_GLOW|  & glowing/pulsating engine glow effect       \\
  0x10 & \lstinline|LIGHTFX_LIGHTHOUSE|           & rotating lighthouse effect                 \\
  0x11 & \lstinline|LIGHTFX_BROKEN_LIGHT|        & flickering faulty light effect             \\
  0x12 & \lstinline|LIGHTFX_STATUS_INDICATOR|    & a status indicator of PFX events and status \\
  0x13 & \lstinline|LIGHTFX_SOUND_MODULATED|     & sound modulated light intensity \\
  0x14 & \lstinline|LIGHTFX_MOTOR_MODULATED|     & motor speed modulated light intensity \\
  \hline
\end{tabular}

\pagebreak

### `LIGHT_OUTPUT_MASK`

\begin{bytefield}[bitwidth=\widthof{COMBO~},endianness=big]{9}
  \bitheader{0-7} \\
  \bitbox{1}{5} & \bitbox{8}{LIGHT\_OUTPUT\_MASK} \\
\end{bytefield}

The selected light f/x can be applied to any combination of the dedicated light output ports.  This is configured by the `LIGHT_OUTPUT_MASK` byte where a logic 1 in each bit corresponds to selected light output port, e.g. a `LIGHT_OUTPUT_MASK<7:0>=0xC5` means that the light f/x will be applied to light output ports 8,7,3, and 1.

### `LIGHT_PF_OUTPUT_MASK`

\begin{bytefield}[bitwidth=\widthof{COMBO~},endianness=big]{9}
  \bitheader{0-7} \\
  \bitbox{1}{6} & \bitbox{8}{LIGHT\_PF\_OUTPUT\_MASK} \\
\end{bytefield}

In addition to single light actions being applicable to the 8 dedicated light output ports, they can also be applied to the Power Functions motor output connectors.  This is to support the use of the Lego brand 8870 dual LED lights with all of the sophisticated light f/x offered by the PFx Brick.  Therefore, a single light action can be performed on up to 12 light output ports simultaneously. The `LIGHT_PF_OUTPUT_MASK` byte specifies which Power Functions output connectors are used as follows:
\bigskip

\begin{bytefield}[bitwidth=\widthof{COMBO~},endianness=big]{9}
  \bitheader{0-7} \\
  \bitbox{1}{6} & \bitbox{4}{unused} &  \footnotesize \bitbox{1}{Motor Output D} &  \footnotesize \bitbox{1}{Motor Output C} &  \footnotesize \bitbox{1}{Motor Output B} &  \footnotesize \bitbox{1}{Motor Output A} \\
\end{bytefield}

Note, that if a conflicting event/action simultaneously commands a motor output and a light action on the same Power Functions motor output port, the motor action will take priority and the light f/x action will be ignored.

\pagebreak

### `LIGHT_PARAMx` Single Light Actions

\begin{bytefield}[bitwidth=\widthof{COMBO~},endianness=big]{9}
  \bitheader{0-7} \\
  \bitbox{1}{7} & \bitbox{8}{LIGHT\_PARAM1} \\
  \bitbox{1}{8} & \bitbox{8}{LIGHT\_PARAM2} \\
  \bitbox{1}{9} & \bitbox{8}{LIGHT\_PARAM3} \\
  \bitbox{1}{10} & \bitbox{8}{LIGHT\_PARAM4} \\
  \bitbox{1}{11} & \bitbox{8}{LIGHT\_PARAM5} \\
\end{bytefield}

Each of the single light actions defined by `LIGHT_FX_ID` field may have up to 5 additional parameter bytes to modify the behaviour of the light f/x.  Currently, only the first 4 bytes have corresponding parameter assignments with byte 5 reserved for future use.  The `LIGHT_PARAM1`, `LIGHT_PARAM2`, and `LIGHT_PARAM3` bytes are assigned as follows to single action light f/x:
\bigskip
\renewcommand{\arraystretch}{1.5}
\begin{tabular}{ | c | l | c | c | c | }
  \hline
  ID  & MNEMONIC                                    & \lstinline|LIGHT_PARAM1| & \lstinline|LIGHT_PARAM2| & \lstinline|LIGHT_PARAM3|  \\
  \hline
  0x01 & \lstinline|LIGHTFX_ON_OFF_TOGGLE|     & \lstinline|DIR_OPTION|   & \lstinline|FADE_TIME|   & \lstinline|FLICKER_ON| \\
  0x02 & \lstinline|LIGHTFX_INC_BRIGHTNESS|     &                          &                          &     \\
  0x03 & \lstinline|LIGHTFX_DEC_BRIGHTNESS|     &                          &                          &     \\
  0x04 & \lstinline|LIGHTFX_SET_BRIGHTNESS|     & \lstinline|BRIGHTNESS|    &                          &     \\
  0x05 & \lstinline|LIGHTFX_FLASH_50_POS|       & \lstinline|PERIOD|        & \lstinline|FADE_FACTOR|  &      \\
  0x06 & \lstinline|LIGHTFX_FLASH_50_NEG|       & \lstinline|PERIOD|        & \lstinline|FADE_FACTOR|  &      \\
  0x07 & \lstinline|LIGHTFX_STROBE_POS|         & \lstinline|PERIOD|        & \lstinline|DUTY_CYCLE|   & \lstinline|BURST_COUNT| \\
  0x08 & \lstinline|LIGHTFX_STROBE_NEG|         & \lstinline|PERIOD|        & \lstinline|DUTY_CYCLE|   & \lstinline|BURST_COUNT| \\
  0x09 & \lstinline|LIGHTFX_GYRALITE_POS|       & \lstinline|PERIOD|        & \lstinline|FADE_FACTOR|  &     \\
  0x0A & \lstinline|LIGHTFX_GYRALITE_NEG|       & \lstinline|PERIOD|        & \lstinline|FADE_FACTOR|  &     \\
  0x0B & \lstinline|LIGHTFX_FLICKER|            & \lstinline|PERIOD2|       & \lstinline|FADE_FACTOR|  &     \\
  0x0C & \lstinline|LIGHTFX_RANDOM_BLINK|       & \lstinline|PERIOD2|       & \lstinline|FADE_FACTOR|  &     \\
  0x0D & \lstinline|LIGHTFX_PHOTON_TORPEDO|     & \lstinline|PERIOD2|       &                          &     \\
  0x0E & \lstinline|LIGHTFX_LASER_PULSE|        & \lstinline|PERIOD2|       &                          &     \\
  0x0F & \lstinline|LIGHTFX_SCIFI_ENGINE_GLOW|  & \lstinline|PERIOD|        & \lstinline|FADE_FACTOR|  &     \\
  0x10 & \lstinline|LIGHTFX_LIGHTHOUSE|         & \lstinline|PERIOD|        &                          &     \\
  0x11 & \lstinline|LIGHTFX_BROKEN_LIGHT|       & \lstinline|FAULT_RATE|   & \lstinline|FADE_TIME|    & \lstinline|FAULT_INTENSITY| \\
  0x12 & \lstinline|LIGHTFX_STATUS_INDICATOR|   & \lstinline|SOURCE1|       & \lstinline|SOURCE2|       & \lstinline|INVERT| \\
  0x13 & \lstinline|LIGHTFX_SOUND_MODULATED|    & \lstinline|FADE_TIME|    &                          & \lstinline|INVERT| \\
  0x14 & \lstinline|LIGHTFX_MOTOR_MODULATED|    & \lstinline|FADE_TIME|    & \lstinline|SOURCE2|       & \lstinline|INVERT| \\
  \hline
\end{tabular}
\bigskip
\pagebreak

The `LIGHT_PARAM4` parameter is used to qualify the tranisition behaviour of the light. Normally, an individual light action results in toggling the light output on or off.  However, this can be qualified to assert the light output to either on or off rather than a toggle action.  The `LIGHT_PARAM4` byte is defined as follows:

\bigskip
\begin{bytefield}[bitwidth=\widthof{COMBO~},endianness=big]{9}
  \bitheader{0-7} \\
  \bitbox{1}{10} & \bitbox{8}{LIGHT\_PARAM4} \\
  \bitbox{1}{10} & \bitbox{4}{DURATION} & \bitbox{2}{Reserved} & \bitbox{2}{TRANSITION} \\
\end{bytefield}
\medskip

The `TRANSITION` parameter is defined as follows:
\medskip

\renewcommand{\arraystretch}{1.5}
\begin{tabular}{ | c | l | }
  \hline
  Value & Description  \\
  \hline
  0x00 & toggle light output  \\
  0x01 & turn light ON \\
  0x02 & turn light OFF \\
  0x03 & turn light ON for a specified DURATION \\
  \hline
\end{tabular}
\normalsize
\medskip

The `DURATION` parameter specifies a fixed time interval as follows:
\medskip

\renewcommand{\arraystretch}{1.5}
\begin{tabular}{ | c | l | c | l | }
  \hline
  Value & Definition &  Value & Definition \\
  \hline
  0x0 & 0.5 sec  & 0x8 & 15 sec \\
  0x1 & 1.0 sec  & 0x9 & 20 sec \\
  0x2 & 1.5 sec  & 0xA & 30 sec \\
  0x3 & 2.0 sec  & 0xB & 45 sec \\
  0x4 & 3.0 sec  & 0xD & 60 sec \\
  0x5 & 4.0 sec  & 0xD & 90 sec \\
  0x6 & 5.0 sec  & 0xE & 2 min  \\
  0x7 & 10 sec   & 0xF & 5 min  \\
  \hline
\end{tabular}
\normalsize
\pagebreak

**Suggested Default Parameter Values**

The table below shows some suggested default values for a host application for each light f/x.

\renewcommand{\arraystretch}{1.5}
\begin{tabular}{ | c | l | c | c | c | }
  \hline
  ID  & MNEMONIC                                    & \lstinline|LIGHT_PARAM1| & \lstinline|LIGHT_PARAM2| & \lstinline|LIGHT_PARAM3|  \\
  \hline
  0x01 & \lstinline|LIGHTFX_ON_OFF_TOGGLE|     &  0x00 : None     &  0x00 : No Fade & 0x00 : No flicker \\
  0x02 & \lstinline|LIGHTFX_INC_BRIGHTNESS|     &                  &               &     \\
  0x03 & \lstinline|LIGHTFX_DEC_BRIGHTNESS|     &                  &               &     \\
  0x04 & \lstinline|LIGHTFX_SET_BRIGHTNESS|     &  0x7F            &               &     \\
  0x05 & \lstinline|LIGHTFX_FLASH_50_POS|      &  0x04 : 1 sec.   & 0x03 : 10\%   &      \\
  0x06 & \lstinline|LIGHTFX_FLASH_50_NEG|      &  0x04 : 1 sec.   & 0x03 : 10\%   &      \\
  0x07 & \lstinline|LIGHTFX_STROBE_POS|         &  0x04 : 1 sec.   & 0x04 : 15\%   & 0x01 : 2 pulses \\
  0x08 & \lstinline|LIGHTFX_STROBE_NEG|         &  0x04 : 1 sec.   & 0x04 : 15\%   & 0x01 : 2 pulses \\
  0x09 & \lstinline|LIGHTFX_GYRALITE_POS|       &  0x04 : 1 sec.   & 0x09 : 50\%   &     \\
  0x0A & \lstinline|LIGHTFX_GYRALITE_NEG|       &  0x04 : 1 sec.   & 0x09 : 50\%   &     \\
  0x0B & \lstinline|LIGHTFX_FLICKER|             &  0x01 : 0.1 sec. & 0x06 : 25\%   &     \\
  0x0C & \lstinline|LIGHTFX_RANDOM_BLINK|       &  0x02 : 0.2 sec. & 0x03 : 10\%   &     \\
  0x0D & \lstinline|LIGHTFX_PHOTON_TORPEDO|     &  0x0A : 1 sec.   &               &     \\
  0x0E & \lstinline|LIGHTFX_LASER_PULSE|        &  0x01 : 0.1 sec. &               &     \\
  0x0F & \lstinline|LIGHTFX_SCIFI_ENGINE_GLOW| &  0x08 : 2 sec.   & 0x09 : 50\%   &     \\
  0x10 & \lstinline|LIGHTFX_LIGHTHOUSE|          &  0x0A : 3 sec.   &               &     \\
  0x11 & \lstinline|LIGHTFX_BROKEN_LIGHT|       &  0x02 : Often    & 0x00 : None   & 0x02 : Severe \\
  0x12 & \lstinline|LIGHTFX_STATUS_INDICATOR|   &  0x01            & 0x00          & 0x00 \\
  0x13 & \lstinline|LIGHTFX_SOUND_MODULATED|    &  0x03 : 10\%     &               &   \\
  0x14 & \lstinline|LIGHTFX_MOTOR_MODULATED|    &  0x03 : 10\%     & 0x00 : None   & 0x00 : not inverted \\
  \hline
\end{tabular}
\medskip

The suggested default value for `LIGHT_PARAM4` is 0x00, i.e. toggle light output on/off.

\pagebreak

### `LIGHT_FX_ID` Combination Light Actions

\begin{bytefield}[bitwidth=\widthof{COMBO~},endianness=big]{9}
  \bitheader{0-7} \\
  \bitbox{1}{4} & \bitbox{1}{COMBO} & \bitbox{7}{LIGHT\_FX\_ID} \\
\end{bytefield}

When the `COMBO` bit is set, then the `LIGHT_FX_ID` corresponds to a combination light action specified in the table below.  Unlike masked combinations of single light actions, these effects are coordinated to drive all 8x light outputs in a specific pattern.  These combo light effects are applied to all 8x light f/x channels and override their current state when activated.
\bigskip
\renewcommand{\arraystretch}{1.5}
\begin{tabular}{ | c | l | l | }
  \hline
  ID & MNEMONIC & Description \\
  \hline
  0x01 & \lstinline|COMBOFX_LINEAR_SWEEP|     &  Linear sweep of sequential lights                    \\
  0x02 & \lstinline|COMBOFX_BARGRAPH_SWEEP|   &  Linear bargraph sweep                                \\
  0x03 & \lstinline|COMBOFX_KNIGHT_RIDER|     &  Knight rider back-forth scanner                      \\
  0x04 & \lstinline|COMBOFX_EMCY_TWINSONIC|   &  Emergency vehicle with twinsonic lightbars           \\
  0x05 & \lstinline|COMBOFX_EMCY_WHELEN|      &  Emergency vehicle with Whelen lightbars              \\
  0x06 & \lstinline|COMBOFX_TIMES_SQUARE|     &  Constantly changing patterns of sweeping lights      \\
  0x07 & \lstinline|COMBOFX_NOISE|             &  Random patterns                                      \\
  0x08 & \lstinline|COMBOFX_TWINKLING_STARS|  &  Simulated twinkling star field effect                \\
  0x09 & \lstinline|COMBOFX_TRAFFIC_LIGHTS|   &  Traffic light sequence including pedestrian crossing \\
  0x0A & \lstinline|COMBOFX_SOUND_BAR|        &  A bargraph modulated by sound playback               \\
  0x0B & \lstinline|COMBOFX_ALTERNATE_FLASH|  &  A pair of lights which flash in opposite phases      \\
  0x0C & \lstinline|COMBOFX_LAVA_LAMP|        &  A soft fluid modulated light effect                  \\
  0x0D & \lstinline|COMBOFX_LASER_CANNON|     &  A one-shot sweeping light effect                     \\
  0x0E & \lstinline|COMBOFX_DRAGSTER|          &  Dragster starter signal lights                       \\
  0x0F & \lstinline|COMBOFX_RUNWAY|            &  Airport runway approach lights                       \\
  0x10 & \lstinline|COMBOFX_FORMULA1|          &  Formula 1 style starter lights                       \\
  \hline
\end{tabular}

\pagebreak

### Combination Light F/X Notes

#### Sound Bargraph

The sound bargraph light f/x animates a bargraph type display in response to any audio playback activity.  The bargraph deflects at a level proportional to the instantaneous audio level.  The bargraph style as well as the number of lights and peristence can be configured using parameters `BAR_STYLE`, `SIZE`, and `FADE_FACTOR`.

#### Traffic Lights

Traffic lights for a typical four way intersection can be simulated with the traffic lights combo light f/x.  The two opposing flows of traffic are designated North/South and East/West and each have a dedicated group of Red, Yellow, and Green light aspects.  Additionally, the North/South flow has two optional light outputs for a pedestrian crossing indicator with "Walk" and "Don't Walk" aspects.  The assignment of light output channels to the corresponding light aspects is as follows:

\renewcommand{\arraystretch}{1.5}
\begin{tabular}{| c | c | c | c | c | c | c | c |}
  \hline
  \multicolumn{8}{|c|}{Light Output} \\
  \hline
  1 & 2 & 3 & 4 & 5 & 6 & 7 & 8 \\
  \hline
  R & Y & G & R & Y & G & Don't Walk & Walk \\
  \hline
  \multicolumn{3}{|c|}{North/South} & \multicolumn{3}{|c|}{East/West} & \multicolumn{2}{c|}{North/South Ped Crossing} \\
  \hline
\end{tabular}


#### Emergency Flashers

The combo light f/x which are used to simulate flashers on emergency vehicles (e.g. police, fire, ambulance, etc.) enable builders to configure light outputs to match a wide variety of emergency vehicles used around the world and from different eras.  A key feature of emergency vehicle flashers is the roof mounted lighting; implemented either as discrete lights or more commonly mounted into a light bar structure on the roof.  In addition to the roof/lightbar flashers are auxilary flashing lights.  These auxilary lights vary widely in terms of quantity and location among all emergency vehicles.  Examples include side mounted flashers, radiator grille flashers, headlamp cluster flashers, etc.  Auxilary flashers are often synchronized with one or more of the lightbar flashers and may or may not have the same flashing pattern.  The PFx Brick provides a variety of functional flashing light outputs for all emergency flasher types in order to match a wide variety of prototypical emergency vehicles.  The builder does not have to use every light output and may chose any combination which best suits their model.  The emergency flashers use 6 of 8 light output ports, leaving the 7th and 8th port available for another use, e.g. headlamps.

For all emergency flasher applications, the light outputs are defined the same way.  They are as follows:

\renewcommand{\arraystretch}{1.5}
\begin{tabular}{| c | c | c | c | c | c |}
  \hline
  \multicolumn{6}{|c|}{Light Output} \\
  \hline
  1 & 2 & 3 & 4 & 5 & 6 \\
  \hline
  \multicolumn{4}{|c|}{Light bar} & \multicolumn{2}{c|}{Auxilary Flashers} \\
  \hline
  \multicolumn{2}{|c|}{Left} & \multicolumn{2}{|c|}{Right} & \multicolumn{2}{|c|}{1x flash} \\ \cline{1-6}
  outer & inner & inner & outer & left & right \\
  \hline
\end{tabular}

#### Light Bar

The lightbar or roof mounted lights consist of a group of 4 lights which flash in variety of different styles.  Often, these lights will be co-packaged into a roof mounted light bar.  Two lights are intended for the left side of the vehicle and another pair is intended for the right side.  Each left/right pair can have an inner and outer light.  This allows light flashing sequences to alternate from left to right or from inside to outside depending on the style.  For more simple applications, one of each of the left and right pairs can be used, e.g. just the outer left/right pair.

Two very common types of lightbar flashers are the so-called "Twinsonic" and "Whelen" style lightbars.  These are named after the trade-marked products of Federal Signal and Whelen Engineering respectively; manufacturers of emergency vehicle lighting products.  These style names are intended to be representative and not exact copies of any particular lighting product.  The "Twinsonic" style light bar physically consisted of rotating mirrors around a light source and were common in older or heritage emergency vehicles.  The rotating light effect is simulated with periodically variable brightness and has a "softer" flashing effect.  The "Whelen" style lightbar is designed to simulate the flashing effects of modern and contemporary LED strobe-type emergency flashers.  These light bars have many different strobe-like patterns and sequences.  The PFx Brick includes most of the typical sequences available from this style of emergency flasher.

#### Auxilary Flashers

Many emergency vehicles incorporate additional flashing lights to those mounted on the roof.  These can consist of flashers which duplicate the flashing sequence from the light bar or flash periodically synchronized with the alternating effect of the lightbar.  The PFx Brick provides auxilary flasher outputs in order to connect lights which best represent the flashing light configuration of a particular vehicle.

The left/right auxilary 1x flashers flash periodically at the specificied rate alternating from left to right.  The 1x and auxilary flashers are simple periodic flashers and do not exhibit the complicated flash sequences of the light bar.  They are however synchronized with the light bar flash rate.

\pagebreak

### `LIGHT_PARAMx` Combination Light Actions

\begin{bytefield}[bitwidth=\widthof{COMBO~},endianness=big]{9}
  \bitheader{0-7} \\
  \bitbox{1}{7} & \bitbox{8}{LIGHT\_PARAM1} \\
  \bitbox{1}{8} & \bitbox{8}{LIGHT\_PARAM2} \\
  \bitbox{1}{9} & \bitbox{8}{LIGHT\_PARAM3} \\
  \bitbox{1}{10} & \bitbox{8}{LIGHT\_PARAM4} \\
  \bitbox{1}{11} & \bitbox{8}{LIGHT\_PARAM5} \\
\end{bytefield}

Each of the combination light actions defined by `LIGHT_FX_ID` field may have up to 5 additional parameter bytes to modify the behaviour of the light f/x.  Most of the combo light f/x use 2 to 4 parameter bytes with the remaining bytes reserved for future use.  The `LIGHT_PARAM1` - `LIGHT_PARAM4` bytes are assigned as follows to combination light f/x:
\bigskip
\renewcommand{\arraystretch}{1.5}
\begin{tabular}{ | c | l | c | c | c | }
  \hline
  ID   & MNEMONIC                                 & \lstinline|LIGHT_PARAM1| & \lstinline|LIGHT_PARAM2| & \lstinline|LIGHT_PARAM3| \\
  \hline
  0x01 & \lstinline|COMBOFX_LINEAR_SWEEP|     & \lstinline|PERIOD|        & \lstinline|FADE_FACTOR|  &  \lstinline|SIZE|         \\ \cline{3-3}
       &                                     & \lstinline|LIGHT_PARAM4| & & \\ \cline{3-3}
       &                                     & \lstinline|SWEEP_STYLE| & & \\
  0x02 & \lstinline|COMBOFX_BARGRAPH_SWEEP|   & \lstinline|PERIOD|        & \lstinline|FADE_FACTOR|  &  \lstinline|SIZE|         \\ \cline{3-3}
       &                                     & \lstinline|LIGHT_PARAM4| & & \\ \cline{3-3}
       &                                     & \lstinline|SWEEP_STYLE| & & \\
  0x03 & \lstinline|COMBOFX_KNIGHT_RIDER|     & \lstinline|PERIOD|         & \lstinline|FADE_FACTOR|  &  \lstinline|SIZE|         \\
  0x04 & \lstinline|COMBOFX_EMCY_TWINSONIC|   & \lstinline|TWIN_STYLE|    & \lstinline|SEQ|          & \lstinline|FLASH_RATE| \\
  0x05 & \lstinline|COMBOFX_EMCY_WHELEN|      & \lstinline|WHELEN_STYLE|  & \lstinline|SEQ|          & \lstinline|FLASH_RATE| \\
  0x06 & \lstinline|COMBOFX_TIMES_SQUARE|     & \lstinline|PERIOD2|        & \lstinline|FADE_FACTOR| &   \\
  0x07 & \lstinline|COMBOFX_NOISE|            & \lstinline|PERIOD2|       & \lstinline|FADE_FACTOR| &   \\
  0x08 & \lstinline|COMBOFX_TWINKLING_STARS|  & \lstinline|PERIOD|         & \lstinline|FADE_FACTOR| &   \\
  0x09 & \lstinline|COMBOFX_TRAFFIC_LIGHTS|   & \lstinline|TRAFFIC_STYLE| & \lstinline|FADE_FACTOR| & \lstinline|SEQ_TIME| \\
  0x0A & \lstinline|COMBOFX_SOUND_BAR|        & \lstinline|BAR_STYLE|     & \lstinline|FADE_FACTOR|  &  \lstinline|SIZE|         \\
  0x0B & \lstinline|COMBOFX_ALTERNATE_FLASH|  & \lstinline|PERIOD|         & \lstinline|FADE_FACTOR|  & \lstinline|DUTY_CYCLE|  \\ \cline{3-4}
       &                                     & \lstinline|LIGHT_PARAM4|   & \lstinline|LIGHT_PARAM5| & \\ \cline{3-4}
       &                                     & \lstinline|OUT_MASK|      & \lstinline|TRANSITION| & \\
  0x0C & \lstinline|COMBOFX_LAVA_LAMP|        & \lstinline|PERIOD|         & \lstinline|SIZE| &         \\
  0x0D & \lstinline|COMBOFX_LASER_CANON|      & \lstinline|FLASH_RATE|    & \lstinline|FADE_FACTOR| & \lstinline|SIZE| \\ \cline{3-3}
       &                                     & \lstinline|LIGHT_PARAM4| & & \\ \cline{3-3}
       &                                     & \lstinline|SWEEP_STYLE| & & \\
  0x0E & \lstinline|COMBOFX_DRAGSTER|         & \lstinline|DRAGSTER_STYLE| & \lstinline|FADE_FACTOR| & \\
  0x0F & \lstinline|COMBOFX_RUNWAY|           & \lstinline|RUNWAY_RATE|   & \lstinline|FADE_FACTOR| & \lstinline|RUNWAY_BRIGHT| \\
  0x10 & \lstinline|COMBOFX_FORMULA1|         & \lstinline|F1_STYLE|    & \lstinline|FADE_FACTOR| &  \lstinline|FLASH_RATE| \\

  \hline
\end{tabular}
\normalsize

\pagebreak

**Suggested Default Parameter Values**

The table below shows some suggested default values for a host application for each light f/x.

\bigskip
\renewcommand{\arraystretch}{1.5}
\begin{tabular}{ | c | l | c | c | c | }
  \hline
  ID   & MNEMONIC                                 & \lstinline|LIGHT_PARAM1| & \lstinline|LIGHT_PARAM2| & \lstinline|LIGHT_PARAM3| \\
  \hline
  0x01 & \lstinline|COMBOFX_LINEAR_SWEEP|     & 0x02 : 0.5 sec.    & 0x06 : 25\%  &  0x00 : 8 lights         \\ \cline{3-3}
       &                                          & \lstinline|LIGHT_PARAM4| & & \\ \cline{3-3}
       &                                          & 0x01 : R to L & & \\
  0x02 & \lstinline|COMBOFX_BARGRAPH_SWEEP|   &  0x04 : 1.0 sec.   & 0x03 : 10\%  & 0x00 : 8 lights         \\ \cline{3-3}
       &                                          & \lstinline|LIGHT_PARAM4| & & \\ \cline{3-3}
       &                                          & 0x01 : R to L & & \\
  0x03 & \lstinline|COMBOFX_KNIGHT_RIDER|     & 0x06 : 1.5 sec. & 0x06 : 25\%  &  0x00 : 8 lights  \\
  0x04 & \lstinline|COMBOFX_EMCY_TWINSONIC|   & 0x02 : Aero   & 0x01 : L/R & 0x02 : Fast \\
  0x05 & \lstinline|COMBOFX_EMCY_WHELEN|      & 0x0A : Random &  0x02 : In/Out  & 0x02 : Fast \\
  0x06 & \lstinline|COMBOFX_TIMES_SQUARE|     & 0x01 : 0.1 sec.  & 0x0A : 75\% &   \\
  0x07 & \lstinline|COMBOFX_NOISE|             & 0x01 : 0.1 sec.  & 0x09 : 50\% &   \\
  0x08 & \lstinline|COMBOFX_TWINKLING_STARS|  & 0x08 : 2 sec. & 0x0F : 400\% &   \\
  0x09 & \lstinline|COMBOFX_TRAFFIC_LIGHTS|   & 0x04 : Std w/Xing & 0x06 : 25\% & 0x01 : Med \\
  0x0A & \lstinline|COMBOFX_SOUND_BAR|        & 0x00 : L to R  & 0x06 : 25\%  &  0x00 : 8 lights         \\
  0x0B & \lstinline|COMBOFX_ALTERNATE_FLASH|  & 0x04 : 1 sec.   & 0x09 : 50\%  & 0x06 : 25\%  \\ \cline{3-4}
       &                                          & \lstinline|LIGHT_PARAM4| & \lstinline|LIGHT_PARAM5| & \\ \cline{3-4}
       &                                          & 0x0F & 0x00 Toggle & \\
  0x0C & \lstinline|COMBOFX_LAVA_LAMP|        & 0x04 : 1 sec.  & 0x00 : 8 lights &         \\
  0x0D & \lstinline|COMBOFX_LASER_CANON|      & 0x03 : Very Fast  & 0x06 : 25\% & 0x04 : 4 lights \\ \cline{3-3}
       &                                          & \lstinline|LIGHT_PARAM4| & & \\ \cline{3-3}
       &                                          & 0x01 : R to L & & \\
  0x0E & \lstinline|COMBOFX_DRAGSTER|          & 0x00 Starter & 0x03 10\% & \\
  0x0F & \lstinline|COMBOFX_RUNWAY|            & 0x02 Med   & 0x03 10\% & 0x00 Maximum \\
  0x10 & \lstinline|COMBOFX_FORMULA1|          & 0x00 Race Start  & 0x03 10\%  & 0x01 Med \\
  \hline
\end{tabular}
\normalsize

\pagebreak

### `LIGHT_PARAMx` Definitions

This section describes all of the named parameters occupying the `LIGHT_PARAMx` event action bytes. Many of the parameters are shared among both single and combination light f/x.

#### `DIR_OPTION`

The `DIR_OPTION` parameter qualifies the illumination of individual lighting events based on motor direction. This can be used for directional head and tail lamps on a motor powered vehicle for example.
\medskip
\renewcommand{\arraystretch}{1.5}
\begin{tabular}{ | c | l | }
  \hline
  Value & Description  \\
  \hline
  0x00 & No directional behaviour  \\
  0x01 & Lights illuminate if Motor A is FWD  \\
  0x02 & Lights illuminate if Motor A is REV  \\
  0x03 & Lights illuminate if Motor B is FWD  \\
  0x04 & Lights illuminate if Motor B is REV  \\
  0x05 & Lights illuminate if Motor C is FWD  \\
  0x06 & Lights illuminate if Motor C is REV  \\
  0x07 & Lights illuminate if Motor D is FWD  \\
  0x08 & Lights illuminate if Motor D is REV  \\
  0x09 & Odd lights illuminate if Motor A is FWD, even lights if REV \\
  0x0A & Odd lights illuminate if Motor B is FWD, even lights if REV \\
  0x0B & Odd lights illuminate if Motor C is FWD, even lights if REV \\
  0x0C & Odd lights illuminate if Motor D is FWD, even lights if REV \\
  0x0D & Odd lights illuminate if Motor A is REV, even lights if FWD \\
  0x0E & Odd lights illuminate if Motor B is REV, even lights if FWD \\
  0x0F & Odd lights illuminate if Motor C is REV, even lights if FWD \\
  0x10 & Odd lights illuminate if Motor D is REV, even lights if FWD \\
  \hline
\end{tabular}
\normalsize

#### `FLICKER_ON`

The `FLICKER_ON` parameter specifies whether a light should flicker during its transition from off to on.  Any non-zero value will enable this feature.

#### `OUT_MASK`

The `OUT_MASK` parameter corresponds to an light output mask with bits 7-0 corresponding to light output ports 8-1 respectively.  A `1` in a bit position indicates that the corresponding light output port should be used/active.

\pagebreak


#### `FADE_TIME`

The `FADE_TIME` parameter specifies the absolute duration of intensity fading when the light transitions to a different intensity levels.
\medskip

\renewcommand{\arraystretch}{1.5}
\begin{tabular}{ | c | l | c | l |}
  \hline
  Value & Definition & Value & Definition  \\
  \hline
  0x00 & No Fade & 0x08 & 1.0 sec    \\
  0x01 & 50 ms   & 0x09 & 1.5 sec   \\
  0x02 & 0.1 sec & 0x0A & 2.0 sec    \\
  0x03 & 0.2 sec & 0x0B & 2.5 sec    \\
  0x04 & 0.4 sec & 0x0C & 3.0 sec    \\
  0x05 & 0.5 sec & 0x0D & 4.0 sec    \\
  0x06 & 0.6 sec & 0x0E & 5.0 sec    \\
  0x07 & 0.8 sec & 0x0F & 10.0 sec   \\
  \hline
\end{tabular}
\normalsize

#### `FADE_FACTOR`

The `FADE_FACTOR` parameter specifies the duration (relative to the period of the light f/x) of intensity fading when the light transitions to a different intensity levels.
\medskip

\renewcommand{\arraystretch}{1.5}
\begin{tabular}{ | c | l | c | l | }
  \hline
  Value & Definition & Value & Definition  \\
  \hline
  0x00 &  No Fade &  0x08 &   40 \%  \\
  0x01 &    1 \%  &  0x09 &   50 \%  \\
  0x02 &    5 \%  &  0x0A &   75 \% \\
  0x03 &   10 \%  &  0x0B &   90 \% \\
  0x04 &   15 \%  &  0x0C &  100 \% \\
  0x05 &   20 \%  &  0x0D &  150 \% \\
  0x06 &   25 \%  &  0x0E &  200 \% \\
  0x07 &   30 \%  &  0x0F &  400 \% \\
  \hline
\end{tabular}
\normalsize

\pagebreak

#### `PERIOD`

The `PERIOD` parameter specifies repeating period for many light f/x.
\medskip

\renewcommand{\arraystretch}{1.5}
\begin{tabular}{ | c | l | c | l | }
  \hline
  Value & Definition & Value & Definition  \\
  \hline
  0x00 & 0.1 sec  &  0x08 & 2.0 sec  \\
  0x01 & 0.25 sec &  0x09 & 2.5 sec  \\
  0x02 & 0.5 sec  &  0x0A & 3.0 sec  \\
  0x03 & 0.75 sec &  0x0B & 4.0 sec   \\
  0x04 & 1.0 sec  &  0x0C & 5.0 sec  \\
  0x05 & 1.25 sec &  0x0D & 8.0 sec   \\
  0x06 & 1.5 sec  &  0x0E & 10.0 sec \\
  0x07 & 1.75 sec &  0x0F & 20.0 sec  \\
  \hline
\end{tabular}
\normalsize

#### `PERIOD2`

The `PERIOD2` parameter specifies repeating period for many light f/x.
\medskip

\renewcommand{\arraystretch}{1.5}
\begin{tabular}{ | c | l | c | l | }
  \hline
  Value & Definition & Value & Definition  \\
  \hline
  0x00 &  0.05 sec & 0x08 &  0.8 sec  \\
  0x01 &  0.1 sec  & 0x09 &  0.9 sec   \\
  0x02 &  0.2 sec  & 0x0A &  1.0 sec  \\
  0x03 &  0.3 sec  & 0x0B &  1.25 sec \\
  0x04 &  0.4 sec  & 0x0C &  1.5 sec  \\
  0x05 &  0.5 sec  & 0x0D &  1.75 sec \\
  0x06 &  0.6 sec  & 0x0E &  2.0 sec  \\
  0x07 &  0.7 sec  & 0x0F &  3.0 sec  \\
  \hline
\end{tabular}
\normalsize

#### `TRANSITION`

The `TRANSITION` parameter used with the alternating flash effect defines the transition after the active (flashing) state. It is defined as follows:
\medskip

\renewcommand{\arraystretch}{1.5}
\begin{tabular}{ | c | l | }
  \hline
  Value & Description  \\
  \hline
  0x00 & toggle light output \\
  0x01 & transition to always ON \\
  0x02 & transition to OFF \\
  \hline
\end{tabular}
\normalsize
\medskip

\pagebreak

#### `DUTY_CYCLE`

The `DUTY_CYCLE` parameter specifies ratio of On/Off intervals for several periodic light f/x.
\medskip

\renewcommand{\arraystretch}{1.5}
\begin{tabular}{ | c | l | c | l | }
  \hline
  Value & Definition & Value & Definition  \\
  \hline
  0x00 &  1\%    &  0x0A & 60\%  \\
  0x01 &  2\%    &  0x0B & 70\%  \\
  0x02 &  5\%    &  0x0C & 75\%  \\
  0x03 & 10\%    &  0x0D & 80\%   \\
  0x04 & 15\%    &  0x0E & 85\%  \\
  0x05 & 20\%    &  0x0F & 90\%   \\
  0x06 & 25\%    &  0x10 & 95\%  \\
  0x07 & 30\%    &  0x11 & 98\%   \\
  0x08 & 40\%    &  0x12 & 99\%  \\
  0x09 & 50\%    &       &       \\
  \hline
\end{tabular}
\normalsize

#### `BURST_COUNT`

The `BURST_COUNT` parameter specifies how many consective strobe intervals a `LIGHTFX_STROBE_POS/NEG` light f/x has.  Generally, the strobe intervals are much shorter than the overall period of the light f/x and are specified with the `DUTY_CYCLE` parameter.
\medskip

\renewcommand{\arraystretch}{1.5}
\begin{tabular}{ | c | l | }
  \hline
  Value & Description  \\
  \hline
  0x00 & 1 strobe pulse  \\
  0x01 & 2 strobe pulses \\
  0x02 & 3 strobe pulses \\
  0x03 & 4 strobe pulses \\
  \hline
\end{tabular}
\normalsize

#### `SIZE`

The `SIZE` parameter restricts the number of light outputs used for combo light f/x.  Most combo light f/x use up to all 8 light output channels; however, some light f/x can be scaled to use less light channels.  Restricting the size of the combo action makes the remaining light channels available for other light f/x actions.
\medskip

\renewcommand{\arraystretch}{1.5}
\begin{tabular}{ | c | l | }
  \hline
  Value & Description  \\
  \hline
  0x00 & 8 lights \\
  0x01 & 7 lights \\
  0x02 & 6 lights \\
  0x03 & 5 lights \\
  0x04 & 4 lights \\
  \hline
\end{tabular}
\normalsize
\pagebreak

#### `BAR_STYLE`

The `BAR_STYLE` parameter determines the modulation pattern of combo light f/x such as the sound bar.
\medskip

\renewcommand{\arraystretch}{1.5}
\begin{tabular}{ | c | l | }
  \hline
  Value & Description  \\
  \hline
  0x01 & Left to Right bar graph \\
  0x02 & Right to Left bar graph \\
  0x03 & In to Out symmetric bar graph \\
  0x04 & Out to In symmetric bar graph \\
  \hline
\end{tabular}
\normalsize

#### `TWINSONIC_STYLE`

The `TWINSONIC_STYLE` parameter determines the modulation pattern of the Twinsonic emergency flasher combo light f/x.
\medskip

\renewcommand{\arraystretch}{1.5}
\begin{tabular}{ | c | l | }
  \hline
  Value & Description  \\
  \hline
  0x00 & Single \\
  0x01 & Dual \\
  0x02 & Aero \\
  0x03 & Combo \\
  \hline
\end{tabular}
\normalsize

#### `WHELEN_STYLE`

The `WHELEN_STYLE` parameter determines the modulation pattern of the Whelen light bar emergency flasher combo light f/x.
\medskip

\renewcommand{\arraystretch}{1.5}
\begin{tabular}{ | c | l | }
  \hline
  Value & Description  \\
  \hline
  0x0 & Signal Alert \\
  0x1 & Signal Alert Steady \\
  0x2 & Comet Flash \\
  0x3 & Action Flash 50 \\
  0x4 & Action Flash 150 \\
  0x5 & Modu Flash \\
  0x6 & Single Flash \\
  0x7 & Double Flash \\
  0x8 & Triple Flash \\
  0x9 & Warning \\
  0xA & Random \\
  \hline
\end{tabular}
\normalsize

\pagebreak

#### `SWEEP_STYLE`

The `SWEEP_STYLE` parameter determines the modulation pattern of combo light f/x such as linear sweep and bar graph.
\medskip

\renewcommand{\arraystretch}{1.5}
\begin{tabular}{ | c | l | }
  \hline
  Value & Description  \\
  \hline
  0x00 & Left to Right pattern \\
  0x01 & Right to Left pattern \\
  \hline
\end{tabular}
\normalsize

#### `TRAFFIC_STYLE`

The `TRAFFIC_STYLE` parameter determines the type of traffic light sequence to simulate.
\medskip

\renewcommand{\arraystretch}{1.5}
\begin{tabular}{ | c | l | }
  \hline
  Value & Description  \\
  \hline
  0x00 & Standard \\
  0x01 & Standard with flashing green \\
  0x02 & European \\
  0x03 & Flashing red (NS), flashing yellow (EW) \\
  0x04 & Standard with pedestrian crossing \\
  0x05 & Standard with flashing green and pedestrian crossing\\
  0x06 & European with pedestrian crossing \\
  0x07 & Flashing red (EW), flashing yellow (NS) \\
  0x08 & International \\
  0x09 & International with pedestrian crossing \\
  0x08 & International 2 \\
  0x09 & International 2 with pedestrian crossing \\
  \hline
\end{tabular}
\normalsize

#### `SEQ_TIME`

The `SEQ_TIME` parameter determines the length of traffic light sequence.
\medskip

\renewcommand{\arraystretch}{1.5}
\begin{tabular}{ | c | l | }
  \hline
  Value & Description  \\
  \hline
  0x00 & Slow (60 sec) \\
  0x01 & Medium (45 sec) \\
  0x02 & Fast (30 sec) \\
  0x03 & Very Fast (20 sec) \\
  \hline
\end{tabular}
\normalsize


#### `SEQ`

The `SEQ` parameter determines how the flashing pattern is sequenced on emergency flasher light bars, e.g. alternating left and right, alternating from inside to outside, etc.
\medskip

\renewcommand{\arraystretch}{1.5}
\begin{tabular}{ | c | l | }
  \hline
  Value & Description  \\
  \hline
  0x00 & Solid \\
  0x01 & Left/Right \\
  0x02 & In/Out \\
  \hline
\end{tabular}
\normalsize

\pagebreak

#### `FLASH_RATE`

The `FLASH_RATE` parameter determines flashing rate of emergency flashers.
\medskip

\renewcommand{\arraystretch}{1.5}
\begin{tabular}{ | c | l | }
  \hline
  Value & Description  \\
  \hline
  0x00 & Slow (60 fpm) \\
  0x01 & Medium (90 fpm) \\
  0x02 & Fast (120 fpm) \\
  0x03 & Very Fast (150 fpm) \\
  \hline
\end{tabular}
\normalsize

#### `FAULT_RATE`

The `FAULT_RATE` parameter determines the approximate probability of the broken light flickering.
\medskip

\renewcommand{\arraystretch}{1.5}
\begin{tabular}{ | c | l | }
  \hline
  Value & Description  \\
  \hline
  0x00 & Rare (~5\%) \\
  0x01 & Occasionally (~10\%)  \\
  0x02 & Often (~25\%) \\
  0x03 & Very Often (~50\%) \\
  \hline
\end{tabular}
\normalsize

#### `FAULT_INTENSITY`

The `FAULT_INTENSITY` parameter determines the approximate relative change of intensity of the broken light flickering.
\medskip

\renewcommand{\arraystretch}{1.5}
\begin{tabular}{ | c | l | }
  \hline
  Value & Description  \\
  \hline
  0x00 & Subtle \\
  0x01 & Moderate  \\
  0x02 & Severe \\
  0x03 & Maximum \\
  \hline
\end{tabular}
\normalsize

\pagebreak

#### `SOURCE1`

The `SOURCE1` parameter specifies a combination of internal PFx Brick events which can trigger a light channel.  Each of the values listed can be logically OR-ed together to indicate multiple items on one light channel.

\medskip

\renewcommand{\arraystretch}{1.5}
\begin{tabular}{ | c | l | }
  \hline
  Value & Description  \\
  \hline
  0x01 & USB connected \\
  0x02 & USB activity  \\
  0x04 & IR activity \\
  0x08 & IR lockout active \\
  0x10 & Audio playback active \\
  0x20 & BLE connected \\
  0x40 & BLE activity \\
  0x80 & Flash File System activity \\
  \hline
\end{tabular}
\normalsize

#### `SOURCE2`

The `SOURCE2` parameter specifies a combination of motor channel states which can trigger a light channel.  The indication is only active when the motor channel is operating at a speed that is not zero.  Each of the values listed can be logically OR-ed together to indicate multiple items on one light channel.

\medskip

\renewcommand{\arraystretch}{1.5}
\begin{tabular}{ | c | l | }
  \hline
  Value & Description  \\
  \hline
  0x01 & Motor channel A forward \\
  0x02 & Motor channel A reverse \\
  0x04 & Motor channel B forward \\
  0x08 & Motor channel B reverse \\
  0x10 & Motor channel C forward \\
  0x20 & Motor channel C reverse \\
  0x40 & Motor channel D forward \\
  0x80 & Motor channel D reverse \\
  \hline
\end{tabular}
\normalsize

#### `INVERT`

The `INVERT` parameter is used to specify whether the light channel output is inverted, i.e. an active state is shown with the light off.  Normally, an active state is shown with the light on. When `INVERT` is zero, the indicator is normal, i.e. active=on.  When set to a non-zero value, the indicator is inverted, i.e. active=off.

#### `BRIGHTNESS`

A numeric value specifying light intensity.  The valid range is 0 to 255 corresponding to minimum and maximum brightness respectively.

\pagebreak

#### `DRAGSTER_STYLE`

The dragster starting lights can operate in one of the 3 folloing styles:

\medskip

\renewcommand{\arraystretch}{1.5}
\begin{tabular}{ | c | l | }
  \hline
  Value & Description  \\
  \hline
  0x00 & Standard countdown to green \\
  0x01 & Pro countdown to green 0.5 sec \\
  0x02 & Pro countdown to green 0.4 sec \\
  \hline
\end{tabular}
\normalsize

#### `F1_STYLE`

The Formula 1 combo light effects can operate in a variety of styles which correspond to the different operational phases of a typical F1 race.  The F1 styles are defined as follows:

\medskip

\renewcommand{\arraystretch}{1.5}
\begin{tabular}{ | c | l | }
  \hline
  Value & Description  \\
  \hline
  0x00 & Race start countdown \\
  0x01 & Training countdown \\
  0x02 & Race break / caution \\
  0x03 & Training start \\
  0x04 & Training break \\
  0x05 & Training end \\
  \hline
\end{tabular}
\normalsize

#### `RUNWAY_RATE`

The runway approach flasher lights can operate with flashing rates defined as follows:

\medskip

\renewcommand{\arraystretch}{1.5}
\begin{tabular}{ | c | l | }
  \hline
  Value & Description  \\
  \hline
  0x00 & Steady - no flashing \\
  0x01 & Slow \\
  0x02 & Med \\
  0x03 & Fast \\
  \hline
\end{tabular}
\normalsize

#### `RUNWAY_BRIGHT`

The runway approach lights illuminate with a static brightness level under the animating flashing effect.  The static brightness level is defined by this parameter as follows:

\medskip

\renewcommand{\arraystretch}{1.5}
\begin{tabular}{ | c | l | }
  \hline
  Value & Description  \\
  \hline
  0x00 & Maximum \\
  0x01 & Med \\
  0x02 & Low \\
  0x03 & Minimum \\
  \hline
\end{tabular}
\normalsize


\pagebreak

### `SOUND_FX_ID`

\begin{bytefield}[bitwidth=\widthof{COMBO~},endianness=big]{9}
  \bitheader{0-7} \\
  \bitbox{1}{12} & \bitbox{8}{SOUND\_FX\_ID} \\
\end{bytefield}

Sound effects are actions to playback a specific sound "file" stored in flash memory.  Sounds are stored in flash memory and are pre-loaded by the host PFX Application.  Polyphonic mixing of sounds is the default behaviour so that sound f/x can be combined realistically.  The `SOUND_FX_ID` encodes the sound f/x actions as follows:
\bigskip
\renewcommand{\arraystretch}{1.5}
\begin{tabular}{ | c | l | p{8cm} | }
  \hline
  ID   & MNEMONIC                                         & Description \\
  \hline
  0x00 & \lstinline|SOUNDFX_NONE|                      & No audio effect                                             \\
  0x01 & \lstinline|SOUNDFX_INC_VOLUME|               & Increase master volume one step                        \\
  0x02 & \lstinline|SOUNDFX_DEC_VOLUME|               & Decrease master volume one step                        \\
  0x03 & \lstinline|SOUNDFX_SET_VOLUME|               & Set volume to a specific step                          \\
  0x04 & \lstinline|SOUNDFX_PLAY_ONCE|                & Play sound file one time                               \\
  0x05 & \lstinline|SOUNDFX_PLAY_CONTINUOUS|          & Play sound file continuously (effect can be toggled)   \\
  0x06 & \lstinline|SOUNDFX_PLAY_NTIMES|              & Play sound file a specified number of times            \\
  0x07 & \lstinline|SOUNDFX_PLAY_DURATION|            & Loop sound file playback for a specified duration      \\
  0x08 & \lstinline|SOUNDFX_PLAY_PITCHBEND_MOTOR|    & Play sound file continuous; modulate pitch as a function of motor speed       \\
  0x09 & \lstinline|SOUNDFX_PLAY_GATED_MOTOR|        & Play sound file; then silence at a rate proportional to motor speed (e.g. for "chuffing" sound)  \\
  0x0A & \lstinline|SOUNDFX_PLAY_AM_MOTOR|           & Play sound file continuous; modulate volume as a function of motor speed      \\
  0x0B & \lstinline|SOUNDFX_STOP|                      & Stop playback of specified sound file  \\
  0x0C & \lstinline|SOUNDFX_PLAY_IDX_MOTOR|          & Play sound files automatically indexed by motor speed. Allows for realistic simulation of engine sounds stored in audio files. \\
  0x0D & \lstinline|SOUNDFX_PLAY_RAND|                & Play sound file at randomly defined time intervals \\
  \hline
\end{tabular}

\pagebreak

### `SOUND_FILE_ID`

\begin{bytefield}[bitwidth=\widthof{COMBO~},endianness=big]{9}
  \bitheader{0-7} \\
  \bitbox{1}{13} & \bitbox{8}{SOUND\_FILE\_ID} \\
\end{bytefield}

The `SOUND_FILE_ID` is the file ID of a sound file stored in the PFx Brick file system.

### Sound F/X Notes

#### Indexed Motor/Engine Sounds (SOUNDFX_PLAY_IDX_MOTOR)

One of the more sophisticated sound playback behaviours for the PFx Brick is the automatic playback of sound files to simulate engines, motors, prime-movers, etc.  This requires specially prepared sound files which can be reliably looped and/or sequentially played without gaps and acoustically transition smoothly.

A motor sound will typically have different acoustic properties depending on the speed or load of the motor.  For example, as a motor increases or decrease speed or rpm, its pitch will increase/decrease proportionally to its speed.  In order to simulate the sound of the motor, the PFx Brick can loop up to 8 different sound file loops representing the sound of the motor at each speed or power level called "notches".  In the PFx Brick configuration, the number of power notches can be specified as well as the speed level between each notch.  Details of this configuration can be found in the `PFX_CMD_SET_CONFIG` section.

For maximum fidelity, the sound of the motor transitioning between each power notch (accelerating and/or decelerating) can be represented with a dedicated sound file for each transition.  Lastly, dedicated sound files for a motor startup and shutdown sound can also be specified.

In order to designate sound files stored on the PFx Brick for use with `SOUNDFX_PLAY_IDX_MOTOR` sound effect, the files have special attributes set in the file's directory listing.  In particular, the lower byte of the `User Attributes` field of the directory entry has special bits which tag the file as follows:

\bigskip

\begin{bytefield}[bitwidth=\widthof{SAMPLE~},endianness=big]{8}
  \bitheader{0-7} \\
  \bitbox{1}{Reseved} & \bitbox{2}{Loop Type} & \bitbox{3}{Loop Index} & \bitbox{1}{Sample Size} & \bitbox{1}{Sample Rate} \\
\end{bytefield}

Using this scheme, the sound files that can be specified for motor speed indexed playback can be summarized as follows:

\bigskip
\renewcommand{\arraystretch}{1.5}
\begin{tabular}{ | l | l | p{1cm} | p{1cm} | l | }
  \hline
  File         & User Attributes[7:0] & Loop Type & Loop Index & Description \\
  \hline
  Notch 1 Loop & X010 00XX [0x20]  & 01 & 000 & Loop for minimum speed \\
  Notch 2 Loop & X010 01XX [0x24]  & 01 & 001 & Loop for speed notch 2 \\
  Notch 3 Loop & X010 10XX [0x28]  & 01 & 010 & Loop for speed notch 3 \\
  Notch 4 Loop & X010 11XX [0x2C]  & 01 & 011 & Loop for speed notch 4 \\
  Notch 5 Loop & X011 00XX [0x30]  & 01 & 100 & Loop for speed notch 5 \\
  Notch 6 Loop & X011 01XX [0x34]  & 01 & 101 & Loop for speed notch 6 \\
  Notch 7 Loop & X011 10XX [0x38]  & 01 & 110 & Loop for speed notch 7 \\
  Notch 8 Loop & X011 11XX [0x3C]  & 01 & 111 & Loop for speed notch 8 \\
  Accel 1-2    & X100 00XX [0x40]  & 10 & 000 & Sound transition from notch 1 to 2 \\
  Accel 2-3    & X100 01XX [0x44]  & 10 & 001 & Sound transition from notch 2 to 3 \\
  Accel 3-4    & X100 10XX [0x48]  & 10 & 010 & Sound transition from notch 3 to 4 \\
  Accel 4-5    & X100 11XX [0x4C]  & 10 & 011 & Sound transition from notch 4 to 5 \\
  Accel 5-6    & X101 00XX [0x50]  & 10 & 100 & Sound transition from notch 5 to 6 \\
  Accel 6-7    & X101 01XX [0x54]  & 10 & 101 & Sound transition from notch 6 to 7 \\
  Accel 7-8    & X101 10XX [0x58]  & 10 & 110 & Sound transition from notch 7 to 8 \\
  Startup      & X101 11XX [0x5C]  & 10 & 111 & Startup sound \\
  Decel 2-1    & X110 00XX [0x60]  & 11 & 000 & Sound transition from notch 2 to 1 \\
  Decel 3-2    & X110 01XX [0x64]  & 11 & 001 & Sound transition from notch 3 to 2 \\
  Decel 4-3    & X110 10XX [0x68]  & 11 & 010 & Sound transition from notch 4 to 3 \\
  Decel 5-4    & X110 11XX [0x6C]  & 11 & 011 & Sound transition from notch 5 to 4 \\
  Decel 6-5    & X111 00XX [0x70]  & 11 & 100 & Sound transition from notch 6 to 5 \\
  Decel 7-6    & X111 01XX [0x74]  & 11 & 101 & Sound transition from notch 7 to 6 \\
  Decel 8-7    & X111 10XX [0x78]  & 11 & 110 & Sound transition from notch 8 to 7 \\
  Shutdown     & X111 11XX [0x7C]  & 11 & 111 & Shutdown sound \\
  \hline
\end{tabular}

The process of preparing the PFx Brick for this sound effect can be summarized as follows:

1. Use the `PFX_CMD_SET_CONFIG` command to set the `Notch Count` for the desired number of fixed power notches to simulate (1 to 8)
2. Use the `PFX_CMD_SET_CONFIG` command to also set the speed boundaries between the power notches.  These boundaries must be set in monotonically increasing order.
3. Load all of the desired audio files corresponding to the motor speed loops on to the PFx Brick file system.
4. Use the `PFX_CMD_FILE_DIR` command with a request type of `0x0A` (set masked attributes with ID) to set attributes of each file.  For example, to configure a file with ID 0x55 to be a loop file for notch 7, then the `PFX_CMD_FILE_DIR` command is as follows: `0x45 0x0A 0x55 0x00 0x38 0x00 0x7C`  The 0x007C is convenient mask so that only bits associated with the Loop Type and Loop Index are set, i.e. 0x0038.


\pagebreak



### `SOUND_PARAMx`

\begin{bytefield}[bitwidth=\widthof{COMBO~},endianness=big]{9}
  \bitheader{0-7} \\
  \bitbox{1}{14} & \bitbox{8}{SOUND\_PARAM1} \\
  \bitbox{1}{15} & \bitbox{8}{SOUND\_PARAM2} \\
\end{bytefield}

Some sound f/x actions have associated parameters and are encoded as follows:
\bigskip
\renewcommand{\arraystretch}{1.5}
\begin{tabular}{ | c | l | c | c | }
  \hline
  ID   & MNEMONIC                                    & \lstinline|SOUND_PARAM1| & \lstinline|SOUND_PARAM2| \\
  \hline
  0x00 & \lstinline|SOUNDFX_NONE|                      &                             &                             \\
  0x01 & \lstinline|SOUNDFX_INC_VOLUME|               &                             &                             \\
  0x02 & \lstinline|SOUNDFX_DEC_VOLUME|               &                             &                             \\
  0x03 & \lstinline|SOUNDFX_SET_VOLUME|               &                             & \lstinline|VOLUME|       \\
  0x04 & \lstinline|SOUNDFX_PLAY_ONCE|                & \lstinline|RETRIGGER|     & \lstinline|RELVOLUME|     \\
  0x05 & \lstinline|SOUNDFX_PLAY_CONTINUOUS|          &                             & \lstinline|RELVOLUME|     \\
  0x06 & \lstinline|SOUNDFX_PLAY_NTIMES|              & \lstinline|REPEAT_COUNT| & \lstinline|RELVOLUME|     \\
  0x07 & \lstinline|SOUNDFX_PLAY_DURATION|            & \lstinline|DURATION|      & \lstinline|RELVOLUME|     \\
  0x08 & \lstinline|SOUNDFX_PLAY_PITCHBEND_MOTOR|     & \lstinline|MOTOR_OUTPUT| & \lstinline|GAIN|          \\
  0x09 & \lstinline|SOUNDFX_PLAY_GATED_MOTOR|         & \lstinline|MOTOR_OUTPUT| & \lstinline|GAIN|          \\
  0x0A & \lstinline|SOUNDFX_PLAY_AM_MOTOR|            & \lstinline|MOTOR_OUTPUT| & \lstinline|GAIN|          \\
  0x0B & \lstinline|SOUNDFX_STOP|                      &                             &                             \\
  0x0C & \lstinline|SOUNDFX_PLAY_IDX_MOTOR|           & \lstinline|MOTOR_OUTPUT| & \lstinline|IDX_OPTIONS| \\
  0x0D & \lstinline|SOUNDFX_PLAY_RAND|                & \lstinline|PROBABILITY|   &  \\
  \hline
\end{tabular}

\pagebreak

### `SOUND_PARAMx` Definitions

#### `DURATION`

The `DURATION` parameter specifies a fixed time interval used by some f/x.

\renewcommand{\arraystretch}{1.5}
\begin{tabular}{ | c | l | c | l | }
  \hline
  Value & Definition &  Value & Definition \\
  \hline
  0x0 & 0.5 sec  & 0x8 & 15 sec \\
  0x1 & 1.0 sec  & 0x9 & 20 sec \\
  0x2 & 1.5 sec  & 0xA & 30 sec \\
  0x3 & 2.0 sec  & 0xB & 45 sec \\
  0x4 & 3.0 sec  & 0xD & 60 sec \\
  0x5 & 4.0 sec  & 0xD & 90 sec \\
  0x6 & 5.0 sec  & 0xE & 2 min  \\
  0x7 & 10 sec   & 0xF & 5 min  \\
  \hline
\end{tabular}
\normalsize

#### `RETRIGGER`

If an event to playback the same file occurs while the file is playing, the `RETRIGGER` parameter specifies which action should be taken as follows:

```
0 = Toggle playback on/off
1 = Restart playback from the beginning of the file
```

#### `REPEAT_COUNT`

A numeric value specifying the number of times to repeat audio playback.  The valid range is 1 to 100.

#### `VOLUME`

A numeric value specifying audio volume.  The valid range is 0 to 255 corresponding to minimum and maximum volume respectively.

#### `RELVOLUME`

2's complement 0x8 ~ 0x7 corresponding to a relative volume level expressed as a gain/attenuation factor in dB from the current playback volume.

#### `GAIN`

The `GAIN` parameter corresponds to the gain or amount of influence motor speed has on the modulation.  The valid range is -100 to 100, where negative values define modulation effect in the opposite sense to motor speed, e.g. audio volume which decreases with increasing motor speed.

#### `MOTOR_OUTPUT`

The `MOTOR_OUTPUT` parameter specifies which motor channel is used to modulate a sound f/x.  Motor channels A, B, C, and D are specified as 0x0, 0x1, 0x2, and 0x3 respectively.

If the `MOTOR_OUTPUT` parameter is used with the `SOUNDFX_PLAY_IDX_MOTOR` sound Fx, then bit 2 of `MOTOR_OUTPUT` can specify whether the desired motor channel's target or current speed is used to determine the index of the sound file to play.

If `MOTOR_OUTPUT[2] = 0` then the target speed is used, if `MOTOR_OUTPUT[2] = 1` then the current speed is used.

#### `IDX_OPTIONS`

The `IDX_OPTIONS` parameter customizes the behaviour of the `SOUNDFX_PLAY_IDX_MOTOR` sound Fx.  The `IDX_OPTIONS` parameter is defined as follows:

\medskip
\begin{bytefield}[bitwidth=\widthof{PLAYSHUTDOWN~},endianness=big]{4}
  \bitheader{0-3} \\
  \bitbox{1}{Startup Sound Override} & \bitbox{1}{Play Startup Shutdown} & \bitbox{2}{Volume Modulation} \\
\end{bytefield}

`Startup Sound Override` allows any changes in motor speed to interrupt the playback of startup sounds.  This is a useful option to avoid waiting for a lengthy startup sound to finish.  If set to 1, motor speed changes will halt playback of the startup sound, and immediately start operational motor sounds.  If not set (0), the startup sound file will playback to completion before responding to any motor speed changes for sound playback.

`Play Startup Shutdown` specifies whether or not sound files representing engine startup and shutdown sounds should be played when the `SOUNDFX_PLAY_IDX_MOTOR` sound Fx is toggled on or off.  If set to 1, sound files representing the startup and shutdown sounds should be pre-loaded into the file system with the correct corresponding reserved file IDs.

`Volume Modulation` specifies if any volume modulation should also be applied to motor indexed sound playback.  This will allow for a variable amount of loudness to be simulated corresponding to engines which sound louder at higher speeds.


```
0x0 = no volume modulation
0x1 = light modulation
0x2 = medium modulation
0x3 = heavy modulation
```

#### `PROBABILITY`

The `PROBABILITY` parameter specifies the approximate probability of playing a specified sound file when used with the `SOUNDFX_PLAY_RAND` sound Fx.  The `PROBABILITY` parameter is specified as follows:

```
0x0 = rare
0x1 = occasional
0x2 = often
0x3 = very often
```

\pagebreak

# Notifications

The PFx Brick implements an optional notification mechanism to asynchronously send messages to a connected host.  These notification messages operate on a subscription model whereby the host indicates which combination of notifications it wants to receive.  After a command has been issued to subscribe to notifications, the PFx Brick will then send messages corresponding to the desired notification events.  The notifications can be enabled or disabled at any time by the host.

The specify which notifications are desired to be sent, a logical-OR combination of bit flags is used.  This allows for any desired combination of notifications to be sent to the host as required.  The flags to specify notifications are defined as follows:

\renewcommand{\arraystretch}{1.5}
\begin{tabular}{ | l | l | p{6.5cm} | }
  \hline
  ID   & MNEMONIC                             & Description \\
  \hline
  0x01 & \lstinline|PFX_NOTIFICATION_AUDIO_PLAY_DONE| \normalsize & When any audio channel reaches the end of its playback interval, a notification is sent with a parameter indicating which audio file ID ended playback. \\
  0x02 & \lstinline|PFX_NOTIFICATION_AUDIO_PLAY|       \normalsize & When an audio channel begins playback, a notification is sent indicating which audio file ID is starting playback. \\
  0x04 & \lstinline|PFX_NOTIFICATION_MOTORA_CURR_SPD|  \normalsize & Periodic notifcations are sent indicating the current speed of motor channel A \\
  0x08 & \lstinline|PFX_NOTIFICATION_MOTORA_STOP|      \normalsize & A notification is sent when motor channel A stops \\
  0x10 & \lstinline|PFX_NOTIFICATION_MOTORB_CURR_SPD|  \normalsize & Periodic notifcations are sent indicating the current speed of motor channel B \\
  0x20 & \lstinline|PFX_NOTIFICATION_MOTORB_STOP|      \normalsize & A notification is sent when motor channel B stops \\
  0x40 & \lstinline|PFX_NOTIFICATION_TO_BLE|           \normalsize & Instructs the PFx Brick to send notifications to the Bluetooth LE interface \\
  0x80 & \lstinline|PFX_NOTIFICATION_TO_USB|           \normalsize & Instructs the PFx Brick to send notifications to the USB interface \\
  \hline
\end{tabular}

\medskip
For example, if a BLE connected host wants to receive notifications for audio stop events and motor channel A and B speed changes, then the command message would be as follows:

\medskip
\begin{bytefield}[bitwidth=\widthof{0xAA~},endianness=little]{2}
  \bitheader{0-1} \\
  \bitbox{1}{0x60} & \bitbox{1}{0x55} \\
\end{bytefield}

to disable notifications completely, the following command message is used:

\medskip
\begin{bytefield}[bitwidth=\widthof{0xAA~},endianness=little]{2}
  \bitheader{0-1} \\
  \bitbox{1}{0x60} & \bitbox{1}{0x00} \\
\end{bytefield}

\pagebreak

# Memory Map

The PFx Brick has non-volatile flash memory storage used to store its configuration and audio files.  Typically, the PFx Brick can come configured with 4, 8, or 16 MBytes of flash storage.  This is partitioned into the following regions:

\renewcommand{\arraystretch}{1.5}
\begin{tabular}{ | l | l | l | l | l | l | }
  \hline
  \multicolumn{2}{|c }{4 MB}      & \multicolumn{2}{|c }{8 MB}      & \multicolumn{2}{|c|}{16 MB}      \\
  \hline
  Address   & Memory Space        & Address   & Memory Space        &Address   & Memory Space         \\
  \hline
  0x000 000 & File system         & 0x000 000 & File system         & 0x000 000 & File system    \\
            &                     &           &                     &          &                      \\
  \multicolumn{2}{ | c }{...}     & \multicolumn{2}{ | c }{...}     & \multicolumn{2}{ |c| }{...}       \\
            &                     &           &                     &          &                      \\
  0x3FB FFF &                     & 0x7FB FFF &                     & 0xFFB FFF &                      \\
  \hline
  0x3FC 000 & FAT Sector Map      & 0x7FC 000 & FAT Sector Map      & 0xFFC 000 & FAT Sector Map  \\
  0x3FD FFF &                     & 0x7FD FFF &                     & 0xFFD FFF &               \\
  \hline
  0x3FE 000 & FAT Directory       & 0x7FE 000 & FAT Directory       & 0xFFF 000 & FAT Directory  \\
  0x3FE FFF &                     & 0x7FE FFF &                     & 0xFFE FFF &               \\
  \hline
  0x3FF 000 & Config space        & 0x7FF 000 & Config space        & 0xFFF 000 & Config space  \\
  0x3FF 1FF &                     & 0x7FF 1FF &                     & 0xFFF 1FF &               \\
  \hline
  0x3FF 200 & Event LUT           & 0x7FF 200 & Event LUT           & 0xFFF 200 & Event LUT       \\
            &                     &           &                     &          &                      \\
            &                     &           &                     &          &                      \\
  0x3FF 9FF &                     & 0x7FF 9FF &                     & 0xFFF 9FF &                      \\
  \hline
  0x3FF A00 & Reserved            & 0x7FF A00 & Reserved            & 0xFFF A00 & Reserved      \\
            &                     &           &                     &          &                      \\
  0x3FF FFF &                     & 0x7FF FFF &                     &0xFFF FFF &                      \\
  \hline
\end{tabular}

\pagebreak

# Flash Memory File System

The majority of the capacity of PFx Brick flash memory is dedicated to storing a simple block-oriented file system.  This file system allows files of any content to be transfered to and from the connected USB host. The primary function of this file system is to store audio files; however, it is general purpose enough to be used for storage of any file type for future applications.

Access to the file system is provided by a set of conventional file I/O methods such as open, close, read, write, etc.  Before any file can be accessed, it must be opened.  This will ensure that pointers to the file data content for read and write operations are initialized to a known state.  Open files must also be closed when the host has completed any read or write tasks.  This ensures any buffered data is safely committed back to the file system and the state of file handles and directories remain consistent.

The details of allocating files across the flash memory is completely abstracted and managed by the file system.  The file system automatically allocates space for new files, performs garbage collection on freed/deleted files, pre-erases blocks of flash memory for instant allocation, and arbitrates access to the flash memory from all sources.

## Flash Directory Structure

A file system directory contains a list of the files stored as well as several fields of meta data associated with each file.  The format of individual flash directory entries is as follows:

\bigskip

\begin{bytefield}[bitwidth=\widthof{SECTIM1~},endianness=little]{10}
  \bitheader{0-9} \\
  \bitbox{2}{File ID[15:0]} & \bitbox{2}{Flags} & \bitbox{2}{First Sector[15:0]} & \bitbox{4}{File size[31:0]} \\
\end{bytefield}

\begin{bytefield}[bitwidth=\widthof{SECTIM1~},endianness=little]{10}
  \bitheader[lsb=10]{10-19} \\
  \bitbox{2}{User Attributes[15:0]} & \bitbox{4}{User Data1[31:0]} & \bitbox{4}{User Data2[31:0]} \\
\end{bytefield}

\begin{bytefield}[bitwidth=\widthof{SECTIM1~},endianness=little]{4}
  \bitheader[lsb=20]{20-23} \\
  \bitbox{4}{CRC32[31:0]} \\
\end{bytefield}

\begin{bytefield}[bitwidth=\widthof{MIA1~},endianness=little]{16}
  \bitheader[lsb=24]{24-39} \\
  \bitbox{16}{Left justified 32 character filename UTF-8 encoded} \\
\end{bytefield}

\begin{bytefield}[bitwidth=\widthof{MIA1~},endianness=little]{16}
  \bitheader[lsb=40]{40-55} \\
  \bitbox{16}{Left justified 32 character filename UTF-8 encoded} \\
\end{bytefield}

### File ID

The `File ID` is a unique identifier which is used to identify and distiguish files.  It can have any value in the range 0x0000 to 0x7FFE.  An identifier value of 0xFFFF signifies an empty directory entry.  **Note:** that all file access commands described in this ICD use the **lower 8-bits of the `File ID` only.**  The `File ID` is stored as a 16-bit value; however, access requests are made using the lower 8-bits.  Therefore, `File ID` values should be specified as values between 0x00 and 0xFE.  The use of the full 16-bits of `File ID` may be exploited in future applications.

### Flags

The `Flags` field is used internally within the file system during file operations and is not normally useful to connected host applications.

### First Sector

The `First Sector` field points to the location in flash memory of the first sector of the associated file's payload data.  This sector location is also used by the file system as a pointer to the beginning of File Allocation Table (FAT) sector chain belonging to the file.  Sectors are nominally 4096 byte containers and file data is stored in an integral number of these 4k sectors.

### File Size

The `File Size` reports the total number of bytes contained in the file.

### User Attributes

The `User Attributes` field stores file specific meta data as follows:

\bigskip

\begin{bytefield}[bitwidth=\widthof{MIM~},endianness=big]{16}
  \bitheader{0-15} \\
  \bitbox{8}{File Format[15:8]} & \bitbox{8}{User defined[7:0]} \\
\end{bytefield}

The upper byte stores the `File Format` identifier.  Rather than using a typical dotted string extension to the filename, the file format can be optionally stored in the `User Attributes[15:8]` field using a code which maps the file format.  The current list of defined file format extensions are as follows:

\medskip

\renewcommand{\arraystretch}{1.5}
\begin{tabular}{ | c | l | c | l | }
  \hline
  Value & Definition & Value & Definition  \\
  \hline
  0x00 & WAV  &  0x10 & TXT  \\
  0x01 & FLAC &  0x11 & HEX  \\
  0x02 & MP3  &  0x20 & ZIP \\
  0x03 & OGG  &  0x21 & GZ \\
  0x04 & AU   &  0x50 & IMG \\
  0x05 & GSM  &       &  \\
  \hline
\end{tabular}
\normalsize

\pagebreak

The user defined bits of `User Attributes` can be used by the host application and firmware in any agreed upon way.  Currently, the `User Attributes` field has definitions when associated with WAV files and with text files used for scripting.

\medskip

**WAV File User Attributes**

 Currently, for the storage of audio WAV files the `User Attributes[7:0]` bits have the following definitions:

\bigskip

\begin{bytefield}[bitwidth=\widthof{RESERVED~},endianness=big]{8}
  \bitheader{0-7} \\
  \bitbox{1}{Reserved} & \bitbox{2}{Loop Type} & \bitbox{3}{Loop Index} & \bitbox{1}{Sample Size} & \bitbox{1}{Sample Rate} \\
\end{bytefield}

where:

\renewcommand{\arraystretch}{1.5}
\begin{tabular}{ | c | l | }
  \hline
  Bit & Definition   \\
  \hline
  0 & Sample rate : 0=22.050 kHz, 1=11.025 kHz   \\
  1 & Sample size : Quantization 0=16 bits per sample, 1=8 bits per sample \\
  4:2 & Loop Index when Loop Type[1:0] is not zero \\
  6:5 & Loop Type where \\
      & 01 = Fixed motor/engine loop sound at power notch \\
      & 10 = Accelerating motor sound between power notches \\
      & 11 = Decelerating motor sound between power notches \\
  \hline
\end{tabular}
\normalsize

A more detailed description of setting these file attributes for use with motor speed indexed sound effects can be found in Sound F/X Notes in the Action Encoding section.

\medskip

**Script File User Attributes**

When a text file is specifically intended to be used for scripting, then an optional value of **0x80** can be assigned to the `User Attributes` field.  This is not strictly required for execution of script files; however it can be a useful marker for host applications to easily distinguish ordinary text files from script files.


### User Data1/2

The `User Data1` and `User Data2` fields are user defined 32-bit containers for any meta data that either the host or firmware application needs to store conveniently with the file directory entry.  These fields are currently defined when used to store audio WAV files as follows:

\medskip

\renewcommand{\arraystretch}{1.5}
\begin{tabular}{ | c | l | }
  \hline
  Field & Definition   \\
  \hline
  \lstinline|User Data1| & Number of sample bytes in audio WAV file starting at data chunk offset   \\
  \lstinline|User Data2| & Offset in bytes from the start of the file to sample byte data \\
  \hline
\end{tabular}
\normalsize

\medskip

Note that the PFx Brick firmware automatically fills the contents of `User Attributes`, `User Data1`, and `User Data2` automatically when a WAV audio file is written to the file system.

### CRC32

The `CRC32` field is a 32 bit hash code automatically generated by the PFx Brick after a file has been written to the file system.  This hash code is automatically computed along the entire stream of data bytes of the file.  This code can be a useful integrity check of the data that is actually written to the file system.  It can also be used loosely as a unique hashing code to verify the identity of a file; however, CRC32 codes are prone to "code collision" for hashing purposes when a large number of files need to be compared.

### Filename

The filename field can be used to store a filename containing up to 32 UTF-8 characters.  The filename is not used for file directory lookup as with other traditional file systems; rather the `File ID` field is used for lookup.

## File System Access Commands

The file system is accessed by the host with a group of commands supporting many of the conventional file access tasks.  Files are accessed by first opening a handle to a file specified by its unique `File ID`.  When a handle has been obtained, read and write operations may be performed on the file.  Finally, after file I/O has been completed, the file handle can be closed.  Note that the file handle is not a physical token which is passed to the host, it is effectively a virtual state.  When a handle is opened, the PFx file system initializes read and write pointers to a file and applies any subsequent read or write requests to the requested file.  It will continue in this state until the handle is closed.  The handle is logically associated with the USB interface instance that the host uses to connect to the PFx Brick.  There can be up to 4 USB HID interface sessions available and one virtual file handle is associated with each USB HID interface.  Connecting with multiple interface sessions allows for a potential increase in transfer bandwidth between the PFx Brick and the host.

The `PFX_CMD_FILE_OPEN` command opens a virtual file handle to a file for host file I/O.  If the specified file does not exist, then it is created by reserving a directory entry for the file and empty storage sectors are allocated for the file.  Unlike other file systems, the creation of a new file requires that the file size be known in advance for pre-allocation of sectors in the FAT.

Another consideration when using the file system is that files are currently "Write Once Only".  That is, when a file is written, it must not be changed.  If changes are required, then the file should be deleted and a new file created to replace it.  This differs from other file systems that support arbitrary write access modes to a file.  The reason for this restriction relates to the requirement of flash memory to be erased before it can be written.  The file system performs routine garbage collection by pre-erasing all memory sectors that have been marked as "free".  This lets the file system easily pre-allocate new files immediately for writing.  It is possible that the file system may evolve with additional buffering capabilities to support more arbitrary file write schemes; however, this will come at the cost of additional complexity and performance.  Nonetheless, despite this restriction, files can be written in any arbitrary sequence of full sectors as long as they are written one time and as one complete sector.  Furthermore, write operations should be performed monotonically in increasing byte order.  These considerations will likely not be restrictive since files are typically written sequentially from the beginning.  Lastly, read operations have absolutely no restrictions in terms of size and sequence.  Any number of bytes can be read in random access fashion.

The USB host commands to access the file system are summarized as follows (details for each command can be found in the Host Command Messages reference section):

\medskip

\renewcommand{\arraystretch}{1.5}
\begin{tabular}{ | l | p{8cm} | }
  \hline
  Command & Definition   \\
  \hline
  \lstinline|PFX_CMD_FILE_OPEN|      & Open virtual file handle                                                             \\
  \lstinline|PFX_CMD_FILE_CLOSE|     & Close file handle                                                                    \\
  \lstinline|PFX_CMD_FILE_READ|      & Read data from file to host                                                          \\
  \lstinline|PFX_CMD_FILE_WRITE|     & Write host data to file                                                              \\
  \lstinline|PFX_CMD_FILE_SEEK|      & Move file pointer to a specified byte offset with respect to the beginning of a file \\
  \lstinline|PFX_CMD_FILE_DIR|       & Query the file system for directory information or make changes to directory data   \\
  \lstinline|PFX_CMD_FILE_REMOVE|    & Remove a file from the file system  \\
  \lstinline|PFX_CMD_FILE_FORMAT_FS| & Erase all files and reinitialize the file system directory and file allocation table \\
  \lstinline|PFX_CMD_FILE_GET_FS_STATE| & Reports low-level status information on the file system \\
  \hline
\end{tabular}
\normalsize

\pagebreak

# Product ID Codes & Descriptors

\renewcommand{\arraystretch}{1.5}
\begin{tabular}{ | p{1.3cm} | l | p{8.8cm} | }
  \hline
  Part Number   & Product Descriptor       & Description \\
  \hline
  0x1201        & PFx Brick alpha           & First pre-production prototype PFx Brick with 2x motor channels (using the DRV8839), 8x light channel with discrete pico light connectors, and sound. \\
  0x1202        & PFx Brick beta            & Second pre-production prototype PFx Brick with 2x motor channels (using the DRV8835), 8x light channels on the standard 10-pin lighting dock connector, and sound. \\
  0x1203        & PFx Brick gamma          & Third pre-production prototype with 2x motor channels (using the DRV8833), 8x light channels on the standard 10-pin lighting dock connector, and sound. \\
  0x1204        & PFx Brick delta IR       & Fourth pre-production prototype with 2x motor channels (using the DRV8833), 8x light channels on the standard 10-pin lighting dock connector, and sound. \\
  0x9204        & PFx Brick delta          & Fourth pre-production prototype with 2x motor channels (using the DRV8833), Bluetooth interface, 8x light channels on the standard 10-pin lighting dock connector, and sound. \\
  0x2204        & \textbf{PFx Brick IR 4 MB}  & Production version of the 4 MB PFx Brick IR with 2x motor channels, 8x light channels, and sound. \\
  0x2208        & \textbf{PFx Brick IR 8 MB}  & 8 MB PFx Brick IR \\
  0x2216        & \textbf{PFx Brick IR 16 MB}  & 16 MB PFx Brick IR \\
  0xA204        & \textbf{PFx Brick 4 MB}  & Production version of the 4 MB PFx Brick with Bluetooth interface, 2x motor channels, 8x light channels, and sound. \\
  0xA208        & \textbf{PFx Brick 8 MB}  & 8 MB PFx Brick \\
  0xA216        & \textbf{PFx Brick 16 MB}  & 16 MB PFx Brick \\
  \hline
  0x1701        & PFXLite alpha      & Pre-production economy PFx Brick with light f/x only (8x channels with 10-pin dock connector). It has no plastic enclosure, but has stud mounting holes for integration into a model. \\
  0x2702        & \textbf{PFXLite}   & Production economy PFx Brick with light f/x only. \\
  \hline
  0x1401        & PFx Brick Pro alpha       & Pre-production PFx Brick with 4x motor channels, 8x light channels, and sound. \\
  0x2404        & \textbf{PFx Brick Pro 4 MB}    & Production 4 MB PFx Brick with 4x motor channels, 8x light channels, and sound. \\
  0x2408        & \textbf{PFx Brick Pro 8 MB}   & 8 MB PFx Brick Pro \\
  0x2416        & \textbf{PFx Brick Pro 16 MB}  & 16 MB PFx Brick Pro \\
  \hline
\end{tabular}

\pagebreak

# Status Codes

\renewcommand{\arraystretch}{1.5}
\begin{tabular}{ | c | l | }
  \hline
  Code & MNEMONIC  \\
  \hline
  0x00 & \lstinline|PFX_STATUS_NORMAL|           \\
  0x33 & \lstinline|PFX_STATUS_NORMAL_PENDING|  \\
  0x55 & \lstinline|PFX_STATUS_SERVICE|          \\
  0x53 & \lstinline|PFX_STATUS_SERVICE_PENDING| \\
  0x5B & \lstinline|PFX_STATUS_SERVICE_BUSY|    \\
  \hline
\end{tabular}

\pagebreak

# Error Codes

Several USB command messages include status feedback bytes which may report error or status conditions.  Note that there are some error codes which can refer to more than one condition; however, these codes are used in different contexts and therefore will not conflict.  For example, some codes reported by the PFX_CMD_GET_STATUS message will be different than the PFX_CMD_FILE_OPEN message.  The error codes are summarized as follows:

\renewcommand{\arraystretch}{1.5}
\begin{tabular}{ | c | l | }
  \hline
  Code & MNEMONIC  \\
  \hline
  0x00 & \lstinline|PFX_ERR_NONE|                       \\
  0x00 & \lstinline|PFX_ERR_VERIFY_PASS|               \\
  0x01 & \lstinline|PFX_ERR_VERIFY_FAIL|               \\
  0x00 & \lstinline|PFX_ERR_TRANSFER_REQUEST_OK|      \\
  0x02 & \lstinline|PFX_ERR_TRANSFER_FILE_EXISTS|     \\
  0x03 & \lstinline|PFX_ERR_TRANSFER_TOO_BIG|         \\
  0x04 & \lstinline|PFX_ERR_TRANSFER_INVALID|          \\
  0x04 & \lstinline|PFX_ERR_SPKR_SHORTCIR_FAULT|      \\
  0x06 & \lstinline|PFX_ERR_TRANSFER_CRC_MISMATCH|    \\
  0x08 & \lstinline|PFX_ERR_DAC_OVERTEMP_FAULT|       \\
  0x0B & \lstinline|PFX_ERR_BLE_FAULT|                 \\
  0x05 & \lstinline|PFX_ERR_TRANSFER_FILE_NOT_FOUND| \\
  0x06 & \lstinline|PFX_ERR_TRANSFER_CRC_MISMATCH|    \\
  0x07 & \lstinline|PFX_ERR_TRANSFER_BUSY_WAIT|       \\
  0x08 & \lstinline|PFX_ERR_TRANSFER_LUT_FULL|        \\
  0xFF & \lstinline|PFX_ERR_TRANSFER_ERROR|            \\
  0x80 & \lstinline|PFX_ERR_UPGRADE_FAIL|              \\
  0x0A & \lstinline|PFX_ERR_TRAP_BROWNOUT_RST|        \\
  0x10 & \lstinline|PFX_ERR_TRAP_CONFLICT|             \\
  0x20 & \lstinline|PFX_ERR_TRAP_ILLEGAL_OPCODE|      \\
  0x40 & \lstinline|PFX_ERR_TRAP_CONFIG_MISMATCH|     \\
  \hline
\end{tabular}

\pagebreak

File system access commands have a several error response codes usually passed back as a status byte in a response packet.  These error codes are summarized as follows:

\bigskip
\renewcommand{\arraystretch}{1.5}
\begin{tabular}{ | c | l | p{7.5cm} | }
  \hline
  Status & Code & Description \\
  \hline
  0x00 & \lstinline|PFX_ERR_NONE|                  & file system operation ok \\
  0xF0 & \lstinline|PFX_ERR_FILE_SYSTEM_ERR|      & overall file system error \\
  0xF1 & \lstinline|PFX_ERR_FILE_INVALID|          & file request was invalid or file is invalid  \\
  0xF2 & \lstinline|PFX_ERR_FILE_OUT_OF_RANGE|   & file access request is outside of file size  \\
  0xF3 & \lstinline|PFX_ERR_FILE_READ_ONLY|       & file creation or write access denied \\
  0xF4 & \lstinline|PFX_ERR_FILE_TOO_BIG|         & requested file creation is too big  \\
  0xF5 & \lstinline|PFX_ERR_FILE_NOT_FOUND|       & requested file ID is not found \\
  0xF6 & \lstinline|PFX_ERR_FILE_NOT_UNIQUE|      & requested file creation ID is already used  \\
  0xF7 & \lstinline|PFX_ERR_FILE_LOCKED_BUSY|     & file system is locked or busy  \\
  0xF8 & \lstinline|PFX_ERR_FILE_SYSTEM_FULL|     & file system full \\
  0xF9 & \lstinline|PFX_ERR_FILE_SYSTEM_TIMEOUT|  & file access operation time out \\
  0xFA & \lstinline|PFX_ERR_FILE_INVALID_ADDRESS| & file system request resulted in an invalid memory address \\
  0xFB & \lstinline|PFX_ERR_FILE_NEXT_SECTOR|     & file system FAT points to an invalid sector \\
  0xFC & \lstinline|PFX_ERR_FILE_ACCESS_DENIED|   & file system operation denied or prohibited \\
  0xFF & \lstinline|PFX_ERR_FILE_EOF|              & file access has reached the end of the file \\
  \hline
\end{tabular}


\pagebreak
