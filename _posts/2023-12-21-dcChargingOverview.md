---
layout: post
title: DC Charging Overview
subtitle: The Communication Behind The DC Charging Process
tags: [dc charging, charging]
author: Sam White
---

# DC Charging Session Steps


## Charge Plug Connected
When the charge plug is connected, the EVSE will provide a 5% duty cycle to the EVCC. This duty cycle is reserved for this type of charge session. 

## SLAC
After the charge plug is connected, the EVCC will initiate the first Signal Level Attenuation Characterization (SLAC) request. This ensures that the vehicle and charger are physically connected to each other. 

## SECC Discovery Protocol
Then, the IP address and port are communicated in order to be used in the following communication messages. If TLS encryption is going to be used in the charging process, it will be communicated here. 

Encryption is part of the ISO 15118-20 standard, but it isn't really used in industry yet.

Supply Equipment Communication Controller (SECC)

## Supported App Protocol
The vehicle and charger communicate the communication standards that they support as well as their preferred communication method.
These are the options:
- DIN 70121
- ISO 15118-2
- ISO 15118-20

## Service Discovery
EVCC will request the available payment options and value added services (VAS). For ISO 15118-2 and DIN 70121, the only available payment option is "External Payment" and there are no VAS options. The ISO 15118-20 has more options.

## Authorization/Authentication
This stage will loop until the EVSE has authorized the session. If the EVSE has not completed the authorization, it will periodically send a message to the EVCC to indicate that it is still processing the information. The EVCC will send an empty message back when it receives this message. 
The user may have to scan their RFID card at this stage. 

## Charge Parameter Discovery (CPD)
In this stage, the EVSE and the EVCC will exchange charge parameters, limits, and a charge schedule, if applicable.

## Cable Check
The EVSE applies a voltage to the charge cable to check the isolation. This is important for safely completing a DC charging session. 
#todo explain isolation and why it is important

## Precharge
The EVCC will specify a target voltage for the EVSE to reach. Once the EVSE is at this level, the EV will close the contactors to connect the charger to the vehicle. 
#todo reference spec with allowable voltage level.

## Power Delivery Start
This is the message used to start, stop, or renegotiate charge parameters.

## Current Demand
A successful charging session will spend most of its time in this state. In this state, the EVCC communicates the following parameters:
- EV Status
- Target Current
- Charging Complete
- Target Voltage

It can optionally provide:
- Maximum Voltage Limit
- Maximum Current Limit
- Remaining Time to a Full SOC

The EVSE will communicate the following:
- Status
- Present Voltage
- Present Current
- Current Limit Achieved
- Voltage Limit Achieved
- Power Limit Achieved

It can optionally provide
- Maximum Voltage Limit
- Maximum Current Limit
- Maximum Power Limit

## Power Delivery Stop
Message used to stop a charge session. 

## Welding Detection
This is used to check and communicate if the EVSE contactors have welded closed. 

## Session Stop
TCP communication will end here.


