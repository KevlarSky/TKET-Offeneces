# Overview
- a way to detect if the door is open and or not completely closed
- attempts to close the door after a period of time
	- Hardware override to keep door open when that's wanted
- if the door fails to close after multiple attempts it notifies someone
- time between attempts should be such that if saftey beam or motor force trips that it can be assumed that the problem is cleared. example 30 minutes
- LED indicators for basic diagnostics (what is sensed, and when command is being sent)
- Sensors should not interfere with existing garage door controller (e.g. optocouplers if reusing existing limit switches)

# Implementation
## Brainstorm Process
1. checks Closed switch indication
TRUE - Do Nothing
FALSE - Wait a period, Record, send Closing to Controller
Controller - Sends command for Opening State
2. Controller sends Opening State for Many periods but Open State is not reached
Controller - sends notification to people. "Door not closed, No longer trying"
Controller - stops sending Opening State

Hardware Override - Interrupts Commands from Controller

# Parts
## Hardware

## Software

# States
1. Door Closed
- Closed Switch TRUE
- Safety Beam, Don't Care
2. Door Open
- Open Switch TRUE
- Safety Beam, Don't Care
3. Door Undermined
4. Closing
- listening for Close Switch
- listening for Safety Beam, goes to Opening
- listening for Motor Force, goes to Opening
5. Opening
- Listens for Open Switch
- unknown if listening for Motor Force
