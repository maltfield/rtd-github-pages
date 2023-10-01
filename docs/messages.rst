.. _autodoc:

###############
System Messages
###############
 
Overview
========
This page describes the system messages for the Hercules S/370, ESA/390, and z/Architecture emulator.


Message Format
==============
All Hercules-issued messages are of the form ``HHC*mmnnns* *text*`` where:

- ``HHC`` is the message prefix for Hercules. All Hercules messages will have this prefix.
- ``mm``  specifies the function that issued the message, from the below list
- ``nnn`` Specific message number, assigned more or less sequentially.
- ``s``  Message severity
   - S  Severe error. Causes immediate termination of Hercules.
   - E  Error. The function being requested did not execute correctly, but Hercules should continue running.
   - W  Warning. Not necessarily an error, but something to take note of and possibly correct.
   - I  Information. General messages that do not require any further action.
   - A  Action. You need to do something.
- text  Message text.

CA Communication Adapter emulation
CF Configuration file processing
CP CPU emulation
CT Channel-to-channel adapter emulation
CU CCKD utility
DA DASD emulation (both CKD and FBA)
DC dasdcopy
DG dyngui.dll
DI dasdinit
DL dasdload
DS dasdisup
DT dasdcat
DU DASD utilities common functions
HD Hercules Dynamic Loader
HE hetinit
HG hetget
HM hetmap
HT HTTP server
HU hetupd
IF hercifc (Network interface configuration handler)
IN Hercules initialization
LC LCS emulation
LG System Log functions
PN Hercules control panel command messages
PR Printer emulation
PU Card punch emulation
RD Card reader emulation
SD Socket devices common functions
TA Tape device emulation
TC tapecopy
TE 1052 and 3270 terminal emulation
TM tapemap
TS tapesplt
TT TOD Clock and Timer Services
TU TUN/TAP driver support
VM VM/CP emulation facility


CA Communication Adapter emulation
----------------------------------

HHCCA001I
+++++++++
HHCCA001I CCUU:Connect out to ipaddr:port failed during initial status : System Cause Text
Explanation
HERCULES attempted to make an outgoing TCP connection to ipaddr:port, but the system indicated that there was an error while processing the request.
System Action
The DIAL or ENABLE CCW that caused the connection attempt ends with Unit Check and Intervention Required. The reason for the failure is indicated in the System Cause Text field
Operator Action
None
Programmer Action
Correct the RHOST/RPORT configuration statements in the configuration file. If this message occured during a program initiated DIAL, correct the dial data.
Module
commadpt.c
Function
commadpt_connout


HHCCA002I
+++++++++
HHCCA002I CCUU:Line Communication thread thread id started
Explanation
The thread responsible for asynchronous operations for the BSC emulated line CCUU has been started.
System Action
The system continues
Operator Action
None. This is an informational message
Programmer Action
None. This is an informational message
Module
commadpt.c
Function
commadpt_thread


HHCCA003E
+++++++++
HHCCA003E CCUU:Cannot obtain socket for incoming calls : System Cause Text
Explanation
A system error occured while attempting to create a socket to listen for incoming calls.
System Action
The device creation is aborted.
Operator Action
None.
Programmer Action
Check the System Cause Text for any information relating to the host system. Notify support.
Module
commadpt.c
Function
commadpt_thread


HHCCA004W
+++++++++
HHCCA004W CCUU:Waiting 5 seconds for port port to become available
Explanation
While attempting to reserve port port to listen to it, the system indicated the port was already being used.
System Action
The system waits 5 seconds and then retries the operation
Operator Action
Terminate the device if the port is in error
Programmer Action
Determine the program holding the specified port. If the port cannot be made available, use a different port.


HHCCA005I
+++++++++
HHCCA005I CCUU:Listening on port port for incoming TCP connections
Explanation
The system is now listening on port port for incoming a tcp connection.
System Action
The system continues
Operator Action
None. This is an informational message
Programmer Action
None. This is an informational message


HHCCA006T
+++++++++
HHCCA006T CCUU:Select failed : System Cause Text
Explanation
An error occured during a 'select' system call.
System Action
The BSC thread is terminated
Operator Action
None.
Programmer Action
Check the System Cause Text for any indication of where the error might come from. Notify Support.
HHCCA007W CCUU:Outgoing call failed during ENABLE|DIAL command : System Cause Text
Explanation
The system reported that a previously initiated TCP connection could not be completed
System Action
The I/O operation responsible for the TCP outgoing connection is ended with Unit Check and Intervention Required.
Operator Action
If the error indicates that the error is temporary, retry the operation.
Programmer Action
Check that the destination for this line is correctly configured. If the operation was a DIAL attempt, check in the application configuration or operation data.
HHCCA008I CCUU:cthread - Incoming Call
Explanation
The BSC thread has received an incoming call.
System Action
Depending on configuration and operational status, the call is either accepted or rejected. Eventually, an ongoign I/O operation may complete.
Operator Action
None. This is an informational message
Programmer Action
None. This is an informational message
HHCCA009I CCUU:BSC utility thread terminated
Explanation
The BSC thread has ended
System Action
the system continue.
Operator Action
Refer to any previous error message if this message was not unexpected
Programmer Action
Refer to any previous error message if this message was not unexpected
HHCCA010I CCUU:initialisation not performed
Explanation
The Device initialisation process has failed.
System Action
the system terminates or continues, depending on the reason for which the device was initialisation was initiated.
Operator Action
Refer to any previous error message
Programmer Action
Refer to any previous error message
HHCCA011E CCUU:Error parsing Keyword
Explanation
The device keyword parser found an error while parsing a known keyword.
System Action
The system continues. The device initialisation routine turns on a NOGO flag.
Operator Action
for a runtime initialisation, correct the device initialisation parameters, otherwise notify the programmer.
Programmer Action
For an engine initialisation, correct the device configuration parameters in the configuration file.
HHCCA012E CCUU:Unrecognized parameter Keyword
Explanation
The device keyword parser found an unknown keyword in the device parameter list.
System Action
The system continues. The device initialisation routine turns on a NOGO flag.
Operator Action
for a runtime initialisation, correct the device initialisation parameters, otherwise notify the programmer.
Programmer Action
For an engine initialisation, correct the device configuration parameters in the configuration file.
HHCCA013E CCUU:Incorrect local port|remote port|local host|remote host specification value
Explanation
The device initialisation routine could not correctly parse a parameter value.
System Action
The system continues. The device initialisation routine turns on a NOGO flag.
Operator Action
for a runtime initialisation, correct the device initialisation parameters, otherwise notify the programmer.
Programmer Action
For an engine initialisation, correct the device configuration parameters in the configuration file.
HHCCA014E CCUU:Incorrect switched/dial specification value; defaulting to DIAL=OUT
Explanation
The device initialisation routine found an incorrect DIAL value.
System Action
The system continues. The device initialisation routine turns on a NOGO flag.
Operator Action
for a runtime initialisation, correct the device initialisation parameters, otherwise notify the programmer.
Programmer Action
For an engine initialisation, correct the device configuration parameters in the configuration file.
HHCCA015E CCUU:Missing parameter : DIAL=NO|IN|OUT|INOUT and LPORT|RPORT|LHOST|RHOST not specified
Explanation
The device initialisation routine found that a mandatory parameter was not provided for a specific DIAL Value.
System Action
The system continues. The device initialisation routine turns on a NOGO flag.
Operator Action
for a runtime initialisation, correct the device initialisation parameters, otherwise notify the programmer.
Programmer Action
For an engine initialisation, correct the device configuration parameters in the configuration file.
Note
For DIAL=NO , LPORT, RPORT and RHOST are needed
For DIAL=IN , LPORT is required
For DIAL=OUT None of LPORT,LHOST,RPORT,RHOST are required
For DIAL=INOUT, LPORT is required
HHCCA016W CCUU:Conflicting parameter : DIAL=NO|IN|OUT|INOUT and LPORT|RPORT|LHOST|RHOST=value specified
Explanation
The device initialisation routine found that a parameter was provided for a parameter that is not relevant for a specific DIAL Value.
System Action
The parameter is ignored. The system continues
Operator Action
for a runtime initialisation, correct the device initialisation parameters, otherwise notify the programmer.
Programmer Action
For an engine initialisation, correct the device configuration parameters in the configuration file.
Note
For DIAL=IN , RPORT and RHOST are ignored
For DIAL=OUT , LPORT, LHOST, RPORT and RHOST are ignored
For DIAL=INOUT, RPORT and RHOST are ignored
HHCCA017I CCUU:LPORT|RPORT|LHOST|RHOST parameter ignored
Explanation
The system indicates that the parameter specified is ignored. This message is preceeded by message HHCCA016W
System Action
The system continues
Operator Action
None
Programmer Action
None
HHCCA018E CCUU:Bind failed : System Cause Text
Explanation
While attempting to bind a socket to a specific host/port, the host system returned an uncorrectable error.
System Action
BSC Thread terminates
Operator Action
None
Programmer Action
Check that the LHOST parameter for this device is indeed a local IP address. Otherwise, notify support.
HHCCA019E CCUU:BSC comm thread did not initialise
Explanation
The BSC communication thread reported that it terminated while the device was initialising.
System Action
The device is not initialised.
Operator Action
Check for any previously issued error message.
Programmer Action
Check for any previously issued error message.
HHCCA020E CCUU:Memory allocation failure for main control block
Explanation
A memory allocation failure occured while attempting to reserve memory for the Communication Adapter control block
System Action
The device is not initialised.
Operator Action
None
Programmer Action
Contact support
HHCCA021I CCUU:Initialization failed due to previous errors
Explanation
The initialisation process for device CCUU did not complete succesfully
System Action
The device is not initialised
Operator Action
None
Programmer Action
Refer to any previous error message
HHCCA300D Debug Message
Explanation
This is a debug message. CCW Tracing has been turned on for this device and the Line Handler issues debug messages to help diagnose interface, conformance and protocol issues.
System Action
The system continues
Operator Action
If the debug messages are no longer necessary, turn off CCW tracing (panel command : 't-CCUU').
Programmer Action
None


CF Configuration file processing
----------------------------------


CP CPU emulation
----------------------------------


CT Channel-to-channel adapter emulation
----------------------------------


CU CCKD utility
----------------------------------


DA DASD emulation (both CKD and FBA)
----------------------------------


DC dasdcopy
----------------------------------


DG dyngui.dll
----------------------------------


DI dasdinit
----------------------------------


DL dasdload
----------------------------------


DS dasdisup
----------------------------------


DT dasdcat
----------------------------------


DU DASD utilities common functions
----------------------------------


HD Hercules Dynamic Loader
----------------------------------


HE hetinit
----------------------------------


HG hetget
----------------------------------


HM hetmap
----------------------------------


HT HTTP server
----------------------------------


HU hetupd
----------------------------------


IF hercifc (Network interface configuration handler)
----------------------------------


IN Hercules initialization
----------------------------------


LC LCS emulation
----------------------------------


LG System Log functions
----------------------------------


PN Hercules control panel command messages
----------------------------------


PR Printer emulation
----------------------------------


PU Card punch emulation
----------------------------------


RD Card reader emulation
----------------------------------


SD Socket devices common functions
----------------------------------


TA Tape device emulation
----------------------------------


TC tapecopy
----------------------------------


TE 1052 and 3270 terminal emulation
----------------------------------


TM tapemap
----------------------------------


TS tapesplt
----------------------------------


TT TOD Clock and Timer Services
----------------------------------


TU TUN/TAP driver support
----------------------------------


VM VM/CP emulation facility
----------------------------------


