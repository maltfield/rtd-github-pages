.. _autodoc:

###############
System Messages
###############
 
Overview
========
This page describes the system messages for the Hercules S/370, ESA/390, and z/Architecture emulator.


Message Format
==============
All Hercules-issued messages are of the form ``HHC*mmnnns`` text where:

- `HHC` is the message prefix for Hercules. All Hercules messages will have this prefix.
- ``mm``  specifies the function that issued the message, from the below list
- nnn Specific message number, assigned more or less sequentially.
- s  Message severity:
   - S  Severe error. Causes immediate termination of Hercules.
   - E  Error. The function being requested did not execute correctly, but Hercules should continue running.
   - W  Warning. Not necessarily an error, but something to take note of and possibly correct.
   - I  Information. General messages that do not require any further action.
   - A  Action. You need to do something.
- text  Message text.
