Morse Code Decoder using FPGA and 16x2 LCD
Nexys-4 DDR (Artix-7 XC7A100T) Based Digital Design Project
________________________________________
📌 Project Overview
This project implements a real-time Morse Code Decoder on the Digilent Nexys-4 DDR FPGA board using Verilog HDL.
The system accepts Morse code input through a push button, decodes the timing of button presses into dots and dashes, converts them into ASCII characters, and displays the decoded letters on a 16x2 LCD display.
The project demonstrates:
•	FPGA-based digital design
•	Finite State Machine (FSM) implementation
•	Timing analysis using counters
•	Human input debouncing
•	Morse code decoding logic
•	LCD interfacing in 4-bit mode
________________________________________
🧠 Working Principle
1.	User presses a push button to input Morse code.
o	Short press → Dot (.)
o	Long press → Dash (-)
2.	FPGA measures the button press duration using counters.
3.	The Morse sequence is stored as a binary pattern.
4.	After detecting a pause between symbols:
o	The pattern is sent to a lookup ROM.
o	Corresponding ASCII character is generated.
5.	The decoded character is displayed on the LCD.
________________________________________
⚙️ Hardware Used
Component	Description
FPGA Board	Digilent Nexys-4 DDR
FPGA Device	Xilinx Artix-7 XC7A100T-CSG324
Display	16x2 LCD (HD44780 compatible)
Push Buttons	On-board buttons
LEDs	On-board debug LEDs
Clock	External/On-board FPGA clock
Software	Xilinx Vivado
________________________________________
📂 Project Files
File Name	Purpose
morse_top.v	Top-level module
debouncer.v	Removes switch bouncing
pulse_timer.v	Measures button press duration
morse_fsm.v	Detects dots/dashes and gaps
morse_rom.v	Morse → ASCII lookup table
lcd_driver.v	Drives 16x2 LCD in 4-bit mode
.xdc file	FPGA pin constraints
________________________________________
🏗️ Module Description
________________________________________
1️⃣ Debouncer Module (debouncer.v)
Mechanical push buttons generate noisy transitions when pressed or released.
This module filters out unstable transitions and generates a clean signal for reliable operation.
Function:
•	Removes switch bounce
•	Produces stable button output
________________________________________
2️⃣ Pulse Timer (pulse_timer.v)
Measures how long the push button remains pressed.
Function:
•	Counts clock cycles during button press
•	Determines pulse width
•	Sends timing information to FSM
Output:
•	Short duration → Dot
•	Long duration → Dash
________________________________________
3️⃣ Morse FSM (morse_fsm.v)
Main control logic of the project.
Function:
•	Detects dots and dashes
•	Stores Morse pattern
•	Detects letter gaps and word gaps
•	Generates control signals for decoding
Morse Timing Rules:
Action	Timing
Dot	1 unit
Dash	3 units
Letter Gap	3 units
Word Gap	7 units
________________________________________
4️⃣ Morse ROM (morse_rom.v)
Lookup table for Morse-to-ASCII conversion.
Function:
•	Receives Morse pattern
•	Maps pattern to corresponding character
•	Outputs ASCII code
Example:
Morse	Character
.-	A
-...	B
...	S
---	O
________________________________________
5️⃣ LCD Driver (lcd_driver.v)
Interfaces the FPGA with the 16x2 LCD module.
Features:
•	4-bit communication mode
•	Sends ASCII data
•	Generates LCD enable pulses
•	Displays decoded letters
________________________________________
🔌 LCD Connections
LCD Pin	FPGA Signal
RS	lcd_rs
EN	lcd_en
D4	lcd_d[0]
D5	lcd_d[1]
D6	lcd_d[2]
D7	lcd_d[3]
RW	GND
VSS	GND
VDD	+5V
________________________________________
🟢 LEDs Used
LED	Purpose
LED0	Dot detected
LED1	Dash detected
LED2	Letter complete
LED3	Word gap detected
________________________________________
🧪 Simulation and Testing
The design was verified using:
•	Vivado Synthesis
•	Behavioral Simulation
•	Hardware Testing on Nexys-4 DDR FPGA
Test Cases:
•	Single-letter decoding
•	Multiple-letter decoding
•	Short/long press detection
•	LCD output verification
________________________________________
🚀 Steps to Run the Project
1️⃣ Open Vivado
Create a new RTL project.
________________________________________
2️⃣ Select FPGA Device
Choose:
xc7a100t-1csg324
________________________________________
3️⃣ Add Source Files
Add all Verilog modules:
•	morse_top.v
•	debouncer.v
•	pulse_timer.v
•	morse_fsm.v
•	morse_rom.v
•	lcd_driver.v
________________________________________
4️⃣ Add Constraints File
Add the .xdc file containing:
•	Clock pin mappings
•	Button mappings
•	LED mappings
•	LCD mappings
________________________________________
5️⃣ Set Top Module
Set:
morse_top
as Top Module.
________________________________________
6️⃣ Run Synthesis
Flow → Run Synthesis
________________________________________
7️⃣ Run Implementation
Flow → Run Implementation
________________________________________
8️⃣ Generate Bitstream
Flow → Generate Bitstream
________________________________________
9️⃣ Program FPGA
Open Hardware Manager:
Open Target → Auto Connect → Program Device
________________________________________
📈 Applications
•	Morse code communication systems
•	Embedded system education
•	FPGA timing-based digital systems
•	Human-machine interfaces
•	Digital communication experiments
________________________________________
🎯 Learning Outcomes
Through this project, the following concepts were explored:
•	FPGA Design Flow
•	Verilog HDL Programming
•	FSM Design
•	Timing Analysis
•	LCD Interfacing
•	Debouncing Techniques
•	Digital Communication Encoding
•	Hardware Debugging using LEDs
________________________________________
📚 Future Improvements
Possible future enhancements include:
•	UART serial output
•	PS/2 keyboard input
•	OLED/TFT display support
•	Audio buzzer for Morse feedback
•	Morse encoder mode
•	Full sentence buffering
________________________________________
👨‍💻 Developed Using
•	Xilinx Vivado
•	Verilog HDL
•	Digilent Nexys-4 DDR FPGA Board
________________________________________
✅ Conclusion
This project successfully demonstrates a hardware implementation of a Morse Code Decoder using FPGA technology.
By combining timing analysis, FSM-based control, and LCD interfacing, the system provides a real-time Morse decoding platform suitable for educational and embedded applications.

**This Read me was made with the help honorable ChatGPT**
