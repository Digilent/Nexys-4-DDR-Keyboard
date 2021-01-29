Nexys 4 DDR Keyboard Demo
==============

Description
--------------

This project is a Vivado demo using the Nexys 4 DDR's USB HID Host port and seven segment display, written in Verilog.
When programmed onto the board, whenever the user presses a key on a keyboard connected to the USB HID port (J5, labeled "USB HOST"), a scan code is sent to the Nexys 4 DDR's  Artix-7 chip through a PS/2 interface.

This scan code is then displayed on the seven segment display.
Whenever a new code is read, the last code displayed is shifted left by 2 digits on the display.
In order to avoid repeatedly shifting in the same code when a key is held down, if the new code is the same as the last one read, it is discarded instead of being displayed.

Two digits on the display are used in order to support both key press and key release sequences. When a key is pressed, its scan code "XX" is transmitted. When the key is released, a scan code of 0xF0XX is transmitted, indicating that the key with PS/2 code "XX" has been released. Not all PS/2 scan code sequences are handled.

For example: If the user presses the space bar on a keyboard connected to the Nexys 4 DDR, the scan code "29" will be displayed.  When the space bar is released, "F0 29" will be displayed, and the original "29" will be moved to the left half of the seven segment display.

Requirements
--------------
* **Nexys 4 DDR**: To purchase a Nexys 4 DDR, see the [Digilent Store](https://store.digilentinc.com/nexys-4-artix-7-fpga-trainer-board-limited-time-see-nexys4-ddr/)
* **Vivado 2018.2 Installation**: To set up Vivado, see the [Installing Vivado and Digilent Board Files Tutorial](https://reference.digilentinc.com/vivado/installing-vivado/start).
* **Serial Terminal Emulator**: For more information, see the [Installating and Using a Terminal Emulator Tutorial](https://reference.digilentinc.com/learn/programmable-logic/tutorials/tera-term).
* **MicroUSB Cable**
* **USB Keyboard**

Demo Setup
--------------
1. Download and extract the most recent release ZIP archive from this repository's [Releases Page](https://github.com/Digilent/Nexys-4-DDR-GPIO/releases).
2. Open the project in Vivado 2018.2 by double clicking on the included XPR file found at "\<archive extracted location\>/vivado_proj/Nexys-4-DDR-Keyboard.xpr".
3. In the Flow Navigator panel on the left side of the Vivado window, click **Open Hardware Manager**.
4. Plug a Basys 3 into the computer running Vivado using a MicroUSB cable.
5. Open a serial terminal emulator (such as TeraTerm) and connect it to the Nexys 4 DDR's serial port, using a baud rate of 9600.
6. In the green bar at the top of the window, click **Open target**. Select **Auto connect** from the drop down menu.
7. In the green bar at the top of the window, click **Program device**.
8. In the "Program Device" Wizard, enter "\<archive extracted location\>vivado_proj/Nexys-4-DDR-Keyboard.runs/impl_1/top.bit" into the "Bitstream file" field. Then click **Program**.
9. The demo will now be programmed onto the Nexys 4 DDR. See the Introduction section of this README for a description of how this demo works.

Next Steps
--------------
This demo can be used as a basis for other projects, either by adding sources included in the demo's release to those projects, or by modifying the sources in the release project.

Check out the Nexys 4 DDR's [Resource Center](https://reference.digilentinc.com/reference/programmable-logic/nexys-4-ddr/start) to find more documentation, demos, and tutorials.

For technical support or questions, please post on the [Digilent Forum](https://forum.digilentinc.com).

Additional Notes
--------------
For more information on how this project is version controlled, refer to the [Digilent Vivado Scripts Repository](https://github.com/digilent/digilent-vivado-scripts)


