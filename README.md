# Joey Chang | Embedded systems and robotics

I’m a computer engineering graduate from UC Irvine looking for embedded software, robotics integration, and firmware validation roles in Southern California. I wrote receiver-side firmware for a wireless charging station and worked on two drone projects with Prof. Peter Burke.

[UCI project poster](https://escholarship.org/uc/item/7zb42857) · [Dean’s Choice Award](https://engineering.uci.edu/news/2026/march/eleven-senior-projects-win-deans-choice-awards-at-2026-annual-design-review.php) · [LinkedIn](https://www.linkedin.com/in/joey-chang120101)

## Wireless drone charging station

On a five-person senior design team, I wrote the receiver-side STM32 firmware. I configured multiple ADC channels, read voltages on the board, and implemented protection logic for overvoltage, undervoltage, and overcurrent. I also helped select the LDO and buck converter ICs and reviewed the receiver schematic.

| Test | Method | Result |
| --- | --- | --- |
| ADC acquisition | I applied an input to the receiver and inspected the ADC channels in the STM32 development environment. | I verified that the board produced ADC readings. |
| Protection logic | I set ADC values in the development environment to represent the fault conditions. | The test exercised the firmware response to simulated faults. Physical fault shutdown remains unverified. |
| Receiver bench test | Our team connected a waveform generator directly to the receiver when transmitter power was insufficient. | We could characterize the receiver separately. The team poster reports an 8.4 V battery rail. Charging did not start with the battery connected. |

Figure 6 of the poster shows the regulated rail. The system diagram shows where the team measured it. This repository documents the prototype and the scope of its tests.

## Drone integration and testing

In EECS 195, our three-person team assembled a drone from individual components. We integrated the flight controller, ESCs, GPS, radio receiver, and camera, configured ArduPilot, and debugged the hardware connections.

In a subsequent three-person independent study, we worked with a Raspberry Pi and the ArduPilot flight controller. We tested two separate functions.

| Function | What we observed |
| --- | --- |
| Claude commands through a Model Context Protocol (MCP) server | A physical drone took off and hovered in response to commands. We kept the flight demonstration to those maneuvers because we lacked a suitable flight cage. |
| YOLO-triggered Return-to-Launch (RTL) | In ground or simulation tests, detections of people or selected objects triggered an RTL command. We tested this separately from the Claude interface. |

## Chess engine in C

The engine represents pieces with bitboards and searches moves using negamax with alpha-beta pruning. A move-generation test counted **197,281 legal continuations** four plies from the standard starting position. Depths one through three returned 20, 400, and 8,902. These counts exercise move generation and the make/undo path.
