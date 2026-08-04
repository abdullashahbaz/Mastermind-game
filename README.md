# Mastermind – Embedded Systems Game

A hardware-based implementation of the classic **Mastermind** game, developed using **C** and **ARM Assembly** for the Raspberry Pi.

The project combines high-level game logic written in C with low-level ARM Assembly routines for sequence matching and hardware interaction. It was compiled and tested successfully on a **Raspberry Pi 3 Model B**, where it passed the provided unit tests.

## Project Overview

The player attempts to guess a hidden sequence of numbers. After each attempt, the system provides feedback using:

* **Exact matches** – correct value in the correct position
* **Approximate matches** – correct value in the wrong position
* **Green and red LEDs**
* **Push button input**
* **LCD display output**

The project demonstrates:

* C and ARM Assembly integration
* Embedded systems programming
* GPIO input and output
* LCD control
* Low-level hardware interaction
* Automated unit testing
* GitLab CI integration

## Technologies Used

* C
* ARM Assembly
* GCC
* GNU Make
* Bash
* Raspberry Pi GPIO
* GitLab CI/CD

## Hardware Requirements

The project was tested using a **Raspberry Pi 3 Model B**.

The following components are required:

* Raspberry Pi
* 16×2 LCD display
* Green LED
* Red LED
* Push button
* Potentiometer
* Current-limiting resistors
* Breadboard
* Jumper wires

## GPIO Connections

| Component   | GPIO Pin |
| ----------- | -------: |
| Green LED   |  GPIO 13 |
| Red LED     |   GPIO 5 |
| Push button |  GPIO 19 |

The LCD should be connected to the Raspberry Pi according to the wiring diagram supplied with the project specification.

> Resistors should be used with the LEDs and push button. A potentiometer is also required to control the LCD contrast.

## Project Structure

```text
.
├── master-mind.c
├── mm-matches.s
├── lcdBinary.c
├── testm.c
├── test.sh
└── Makefile
```

### `master-mind.c`

Contains the main Mastermind game logic, command-line processing and supporting functions.

### `mm-matches.s`

Contains the ARM Assembly implementation of the matching algorithm used to calculate exact and approximate matches.

### `lcdBinary.c`

Contains the low-level functions used to control the LEDs, push button and LCD display. Hardware-control operations are implemented using inline ARM Assembly.

### `testm.c`

Contains testing functions used to compare the C and ARM Assembly implementations of the matching algorithm.

### `test.sh`

A shell script used to perform automated unit testing of the matching function.


## Building the Project

Ensure that GCC and Make are installed.

To compile the application and testing components, run:

```bash
make all
```

## Running the Game

To run the Mastermind application in debug mode:

```bash
make run
```

The general command-line format is:

```bash
./cw2 [-v] [-d] [-s] <secret-sequence> [-u <sequence1> <sequence2>]
```

### Available Options

| Option | Description                                  |
| ------ | -------------------------------------------- |
| `-v`   | Enables verbose output                       |
| `-d`   | Enables debug mode                           |
| `-s`   | Uses a manually supplied secret sequence     |
| `-u`   | Runs the matching function in unit-test mode |

## Unit Testing

To run the automated unit tests:

```bash
make unit
```

Alternatively, run the test script directly:

```bash
sh ./test.sh
```

To verify whether every test completed successfully:

```bash
echo $?
```

A return value of `0` indicates that all tests passed.

## Comparing C and Assembly Implementations

To compare the output of the C and ARM Assembly matching functions:

```bash
make test
```

This verifies that both implementations produce the same number of exact and approximate matches.

## Unit-Test Example

The following command compares the sequences `121` and `313`:

```bash
./cw2 -u 121 313
```

Expected output:

```text
0 exact matches
1 approximate matches
```

## Implementation Details

The matching algorithm was initially implemented in C and then recreated in ARM Assembly.

The final application integrates both languages by calling the Assembly matching function from the main C program.

The hardware-control functions for the following components are implemented using inline Assembly:

* Green LED
* Red LED
* Push button
* LCD display

The project components were first tested independently before being integrated into the complete embedded application.

## Testing and Compatibility

The project has been:

* Compiled successfully using GCC
* Tested on a Raspberry Pi 3 Model B
* Verified using the provided shell-based unit tests
* Tested by comparing the C and Assembly implementations
* Configured for automatic testing through GitLab CI

## Coursework Specification

The original coursework specification can be found here:

[Coursework Specification](https://www.macs.hw.ac.uk/~hwloidl/Courses/F28HS/Coursework_F28HS_CW2_2024.pdf)

```
