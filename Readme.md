# Smart Drink Vending Machine (VM) Simulation

## Table of Contents
1. [Project Description](#project-description)
2. [Main Menu](#main-menu)
3. [Onsite Purchase](#onsite-purchase)
4. [Online Purchase](#online-purchase)
5. [Authentication](#authentication)
6. [Burglar Alarm](#burglar-alarm)
7. [Non-functional Inactive Mode](#non-functional-inactive-mode)
8. [Non-functional Active Mode](#non-functional-active-mode)
9. [Docker](#docker)
10. [Functional Requirements](#functional-requirements)
    1. [Function 1 – Start Up and Main Menu](#function-1--start-up-and-main-menu)
    2. [Function 2 – Onsite Purchase](#function-2--onsite-purchase)
    3. [Function 3 – Online Purchase](#function-3--online-purchase)
    4. [Function 4 – Authentication Services](#function-4--authentication-services)
    5. [Function 5 – Burglar Alarm](#function-5--burglar-alarm)
11. [Non-Functional Requirements](#non-functional-requirements)
    1. [Activation Management](#activation-management)
12. [Software Architecture](#software-architecture)

## Project Description
Describe your project here.

## Main Menu
1. When the VM is active, user can choose to start or off it.
2. If "start" was chosen, user can select purchasing if they're buying drinks, or others for technicians or refilling supply purposes.
3. If "off" was chosen, VM will simulate powering off by being in the inactive state.

## Onsite Purchase
1. Detail 1
2. Detail 2

## Online Purchase
1. Detail 1
2. Detail 2

## Authentication
1. Detail 1
2. Detail 2

## Burglar Alarm
1. Detail 1
2. Detail 2

## Non-functional Inactive Mode
1. Detail 1
2. Detail 2

## Non-functional Active Mode
1. Detail 1
2. Detail 2

## Docker
1. Main file: 
2. Image pushed to:

## Functional Requirements

### Function 1 – Start Up and Main Menu
The Smart Drink VM will prompt users on their needs when they use the VM.

**REQ_ID** | **Requirement**
--- | ---
REQ-01 | When the VM is active, the main menu with the text below should be displayed on the LCD screen: Line 1: “1. Start” Line 2: “2. Off”
REQ-02 | In the main menu defined in REQ-01, if the option “1. Start” is selected on the keypad, then the following menu shall be displayed on the LCD Screen: Line 1: “1. Purchasing” Line 2: “2. Others”
REQ-03 | In the main menu defined in REQ-01, if the option “2. Off” is selected on the keypad, the LCD should display the following text for 2 seconds and then turn off the LCD display and back light and enter the Inactive state defined in the State Machine in REQ-23: Line 1: “Thank You” Line 2: “Powering Off”

### Function 2 – Onsite Purchase
The Smart Drink VM allows users to purchase their drink physically from the VM.

**REQ_ID** | **Requirement**
--- | ---
REQ-04 | From the main menu, if the user selects “1. Start” → “1. Purchasing”, then the following menu shall be displayed on the LCD Screen: Line 1: “1. Key Selection” Line 2: “2. Online Payment”
REQ-05 | Each drink in the VM is given a corresponding number based on our CSV file for drinks. From REQ-04, if the user selects “1. Key Selection”, the VM will read the CSV file (drink.csv) containing a list of drinks and their corresponding price.
REQ-06 | The VM will prompt the user to select a drink afterwards. The user is allowed to enter any number between 0 to 99. When a number is keyed in, the following text shall be displayed on the LCD Screen: Line 1: “Enter Number:” Line 2: [Display number entered]: “X” or “XX”, where X represent a digit from 0 to 9
REQ-07 | If the user is unsatisfied with his selection, he can choose ‘*’ to re-enter his drink number as and when he wants. If the user is satisfied with his selection, he can choose ‘#’ to confirm his number. Afterwards, the flowchart defined in Figure 1 shall be implemented.

### Function 3 – Online Purchase
The Smart Drink VM supports “Online Purchase” remotely via smartphones or an external website.

**REQ_ID** | **Requirement**
--- | ---
REQ-12 | The user shall be able to access and view the website to purchase drinks from the VM without being physically there.
REQ-13 | The user should make payment via the app or website, and a QR code or barcode will then be generated for the user to scan at the VM, to collect their drink.
REQ-14 | From REQ-04, if the user selects “2. Online Payment”, then the flowchart defined in Figure 2 shall be implemented.

### Function 4 – Authentication Services
For service technicians and drink suppliers, they will need to enter a valid user code on the keypad to open the VM door without triggering the burglar alarm.

**REQ_ID** | **Requirement**
--- | ---
REQ-19 | The valid user code is made up of 6 characters, including numbers, “*” and “#”. (Valid code: *73524) From the main menu defined in REQ-02, if the user selects “2. Others”, then the LCD shall display the following text: Line 1: “Key user code:” Line 2: The LCD shall display “X” for each key pressed
REQ-20 | Service technicians and/or drink suppliers have only 3 attempts to key in the valid code before the buzzer rings. For each invalid attempt, the following text shall be displayed on the LCD screen: Line 1: “Invalid code” Line 2: [Display attempts left]: “(integer) attempts left”
REQ-21 | If the 6 character code corresponds to the valid user code, then the flowchart defined in Figure 3 shall be implemented.

### Function 5 – Burglar Alarm
To avoid any theft of the drinks, a buzzer will be activated if the VM door has been forcefully pried open.

**REQ_ID** | **Requirement**
--- | ---
REQ-25 | From REQ-20, if an invalid code has been keyed in wrongly for the 3rd time, the buzzer shall be activated based on the timing diagram in Figure 4
REQ-26 | An IR sensor will be used to detect the status of the door (close/open) by returning a value, 0 or 1, as defined below. If the IR sensor detects that the door has been forced open (i.e., opened before the VM prompts for a valid code or opened before a valid code was entered), the buzzer shall be activated based on the timing diagram in Figure 4: 0: Close, 1: Open

## Non-Functional Requirements

### Activation Management
The Smart Drink VM has 2 modes as defined in the State Machine Diagram in Figure 4 below. The transitions between the Inactive Mode and Active Mode are triggered by the events labeled “evEnterIM” and “evEnterAM”.

Conditions for trigger events are defined in the requirements below.

**REQ_ID** | **Requirement**
--- | ---
REQ-27 | “evEnterIM” Trigger Condition 1: When the option “2. Power Off” is selected in the main menu.
REQ-28 | “evEnterIM” Trigger Condition 2: When the keypad has not been pressed for at least 1 minute.
REQ-29 | “evEnterIM” Trigger Condition 3: When the RFID or Camera has not detected any payment for at least 1 minute.
REQ-30 | “evEnterAM” Trigger Condition 1: When the user presses any button on the keypad.
REQ-31 | “evEnterAM” Trigger Condition 2: When the Ultrasonic Distance Sensor detects an object is within 10 cm of the Smart Drink VM.

## Software Architecture

### Static Software Architecture
The Software Architecture defines the various Software Components that are developed to realize the implementation of the system requirements.
