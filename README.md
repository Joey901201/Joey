# Joey Chang | Embedded systems and robotics

I studied computer engineering at UC Irvine. These projects cover two parts of my work: writing firmware for a physical board and integrating a companion computer with a flight controller.

## Wireless drone charging station

**My role:** Receiver-side STM32 firmware on a five-person senior design team. Our project received a Dean’s Choice Award at UCI’s 2026 Annual Design Review.

I configured multiple ADC channels to read voltages along the receiver power path and implemented secondary protection logic for overvoltage, undervoltage, and overcurrent. I also helped select the LDO and buck converter ICs and reviewed the receiver schematic.

### How we tested it

| Test | Method | What it established |
| --- | --- | --- |
| Board measurements | I connected the STM32 to a physical input and inspected ADC readings in the development environment. | The firmware acquired readings on the board. |
| Firmware fault cases | I set ADC values in the STM32 development environment to exercise the protection logic. | I could test the software response without applying damaging electrical conditions. Physical shutdown under a real fault remained unverified. |
| Receiver isolation | Our team fed the receiver directly from a waveform generator. | This let us test the receiver separately when the transmitter could not supply enough power. |

### Reviewing the results

Open the [UCI project poster](https://escholarship.org/uc/item/7zb42857). Start with the system block diagram to trace power from the transmitter through the receiver rectifier and regulator. Then compare the waveforms with the result reported in the abstract. The team reported an 8.4 V battery rail. Charging did not start when the battery was connected. The available measurements leave the cause under load unresolved.

The poster documents the team prototype. This repository is a project write-up. The original firmware, board configuration, and bench data are not included, so there is no firmware build to reproduce here.

[UCI Annual Design Review award announcement](https://engineering.uci.edu/news/2026/3/eleven-senior-projects-win-deans-choice-awards-2026-annual-design-review)

## Drone companion computer and ground telemetry

In an independent study, I integrated a Raspberry Pi Zero 2 W with an ArduPilot flight controller for onboard scripting and camera streaming. I used MAVLink to connect the flight controller to a natural-language command interface. In my drone-building course, I assembled a drone, integrated its flight controller, GPS, and radio receiver, and configured DroneBridge Wi-Fi telemetry to a ground station.

The independent study and course build are separate project descriptions. The command interface supported takeoff, waypoint, and landing commands. Flight logs and verification results for individual commands are not included here.
