# PIC18F4620-Based Multi-Function System with LCD Display and Serial Communication
## Introduction

This project involves the development of a multi-function system using the PIC18F4620 microcontroller. The system includes features such as real-time clock management, analog input reading, and digital I/O control, all interfaced with an LCD display and serial communication for monitoring and control.

## Features

1. Real-Time Clock: Keeps track of the current time and allows setting and incrementing/decrementing time.
2. Analog Input Reading: Reads voltages from three analog channels (AN0, AN1, AN2) and displays the values.
3. Digital I/O Control: Reads and sets the states of various digital inputs and outputs.
4. LCD Display: Provides a user interface to display the time, analog values, and system status.
5. Serial Communication: Allows interaction with the system via serial commands to read or set various parameters.

## Hardware Requirements

1. Microcontroller: PIC18F4620
2. Crystal Oscillator: 4 MHz
3. LCD Display: Compatible with lcd_x8.h
4. Push Buttons: Connected to PORTB
5. Analog Sensors: Connected to AN0, AN1, AN2
6. Digital I/O Devices: Connected to PORTC and PORTD
7. Power Supply: Appropriate for the microcontroller and peripherals

## Software Configuration
### Configuration Bits
The configuration bits are set to ensure proper operation of the microcontroller:

• OSC = XT (XT Oscillator)

• FCMEN = OFF (Fail-Safe Clock Monitor disabled)

• IESO = OFF (Oscillator Switchover mode disabled)

• PWRT = OFF (Power-up Timer disabled)

• BOREN = SBORDIS (Brown-out Reset enabled in hardware only)

• BORV = 3 (Minimum Brown-out Reset Voltage setting)

• WDT = ON (Watchdog Timer enabled)

• WDTPS = 32768 (Watchdog Timer Postscale Select bits)

• CCP2MX = PORTC (CCP2 input/output is multiplexed with RC1)

• PBADEN = ON (PORTB<4:0> pins configured as analog input channels on Reset)

• LPT1OSC = OFF (Timer1 configured for higher power operation)

• MCLRE = ON (MCLR pin enabled)

• STVREN = ON (Stack Full/Underflow will cause Reset)

• LVP = ON (Single-Supply ICSP enabled)

• XINST = OFF (Instruction set extension disabled)

• CP0-CP3 = OFF (Code Protection bits disabled)

• CPB = OFF (Boot Block Code Protection disabled)

• CPD = OFF (Data EEPROM Code Protection disabled)

• WRT0-WRT3 = OFF (Write Protection bits disabled)

• WRTC = OFF (Configuration Register Write Protection disabled)

• WRTB = OFF (Boot Block Write Protection disabled)

• WRTD = OFF (Data EEPROM Write Protection disabled)

• EBTR0-EBTR3 = OFF (Table Read Protection bits disabled)

• EBTRB = OFF (Boot Block Table Read Protection disabled)

## Project Files
• main.c: The main C file containing the project logic.

• my_s.h: Header file for serial communication.

• my_adc.h: Header file for ADC operations.

• lcd_x8.h: Header file for LCD operations.

## Functions and Interrupts
• setupPorts(): Configures the I/O ports.

• initTimers01(): Initializes Timer0.

• RX_ISR(): Handles the serial receive interrupt.

• int1_isr(): Handles INT1 external interrupt.

• int0_isr(): Handles INT0 external interrupt.

• int2_isr(): Handles INT2 external interrupt.

• timer_isr(): Handles Timer0 overflow interrupt.

• highIsr(): High priority interrupt service routine.

## Main Loop
1. Initialize: Ports, serial communication, LCD, ADC, and timers.
2. Monitor Serial Communication: Read commands from the serial interface and respond accordingly.
3. Update Display: Show current time, analog input values, and system status on the LCD.
4. Handle Inputs: Read push button states and update the system state.
## Serial Commands
• R<t>: Request current time.

• R<A><n>: Request analog value from channel n (0, 1, or 2).

• R<H>: Request Heater status.

• R<C>: Request Cooler status.

• R<D>: Request status of digital outputs.

• W<H><V>: Write value to Heater (0 or 1).

• W<C><V>: Write value to Cooler (0 or 1).

• W<d><V>: Write value to digital output d (0-7).

## Usage
1. Set up hardware according to the schematic.
2. Compile and upload the code to the PIC18F4620 using an appropriate programmer.
3. Monitor and control the system via the LCD display and serial interface.
## Notes
• Ensure that the crystal oscillator and all connections are correctly set up for the real hardware environment.

• The system was tested and works on PICSimLab, a virtual simulation tool for PIC microcontrollers.
