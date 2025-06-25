---
title: "Apostrophe 3x"
author: "Allen"
description: "Display that reflects off the windshield to display speed and runs openpilot"
created_at: "2025-05-28"
---
# May 30 - Mostly Planning
I mostly just planned out what exactly my goals were and started looking at components. While a RockChip SOM board would be more fun to design around, they are hard to source, mostly being from AliBaba with expensive but slow shipping. However, I found the Radxa Rock 4D, which seems super powerful but is only $45, which is a very good deal for these kinds of AI SBCs. It also has a bunch of peripheral ports such as MIPI for cameras and displays, and CAN support. I think I will use a MCP2551 CAN transciever for the OBD2 connection, as it has silent mode to lower the risk of interfering with the car's operation. I also found the CH224K USB-PD driver, which should be able to convert the 12V of a car to the correct voltage to power the processor. However, I want to find a way to power it through the GPIO header because it is a lot cleaner that way, with less external wires and everything being on the same PCB.

![image](https://github.com/user-attachments/assets/1db299be-dbe5-41ad-bae1-005005b36d4f)

I also started working on the schematic: 

![image](https://github.com/user-attachments/assets/51b84483-6c85-45c2-9a79-458685378a80)

Time Spent: 1.5h

# June 25 - Schematic Work
I realized that I can take a lot of inspiration from the Comma which is also why I have renamed it to the apostrophe which is like an upside down comma. I plan on porting openpilot over somehow and ideally I want to use the NPU, although this is probably going to be way too hard to do right now.

I figured out what the form factor of the ADAS connector on the Nissan Leaf is (Molex iGrid I believe) which is helpful.

This is the AMS1117 voltage regulator that will connect to the OBD2 power. It has a fuse which also acts as a switch in case I don't want to power it like that or something goes terribly wrong.

![image](https://github.com/user-attachments/assets/886f6616-d91f-450e-8c56-5909b957e518)

I finished wiring up the GPIOs and the CAN transceiver. 

![image](https://github.com/user-attachments/assets/58337f16-dffa-41f7-bd8f-219028436919)

Here is the OBD2 port schematic, however, I need to update it to be the same as the Leaf's

![image](https://github.com/user-attachments/assets/f97ad5e1-6431-4dad-9a8c-2a7ba9807d40)

I plan on adding relays to add full passthrough just like how the Comma does it, and maybe a UART to CAN converter because the ROCK 4D only has 1 CAN bus, but there are 3 channels on the car and I don't know which ones I need.

Time Spent: 2h

**Total time spent: 1.5h**
