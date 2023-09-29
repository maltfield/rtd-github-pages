.. _autodoc:
 
Hercules Version 4: Configuration File
======================================
 
.. automodule:: helloWorld
  :members:
  :undoc-members:
 
Example configuration file
--------------------------

Comment lines
-------------
Blank lines, and lines beginning with a # sign or an asterisk, are treated as comments.

System parameters
-----------------
Except for the ARCHLVL and LPARNUM statements, system parameter statements may appear in any order but must precede any device statements. Each system parameter must be on a separate line.
The following system parameters may be specified:

ARCHLVL
+++++++
``ARCHLVL S/370 | ESA/390 | ESAME | z/Arch``
Specifies the initial architecture mode.
- use ``S/370`` for OS/360, VM/370, and MVS 3.8.
- use ``ESA/390`` for MVS/XA, MVS/ESA, OS/390, VM/ESA, VSE/ESA, Linux/390, and ZZSA.
- use ``z/Arch`` or `ESAME` for z/OS and zLinux. This is the default.

When ``z/Arch`` or ``ESAME`` is specified, the machine will always IPL in ESA/390 mode, but is capable of being switched into z/Architecture mode after IPL. This is handled automatically by all z/Architecture operating systems.

When `ARCHLVL S/370` is set, the current LPARNUM and CPUIDFMT settings will be automatically changed to `BASIC`. When `ARCHLVL z/Arch` is set, `LPARNUM` and `CPUIDFMT` will be reset back to `1` and `0` respectively (if needed). Refer to the *"Limited automatic LPARNUM updating when setting certain architecture modes"* section of the Release Notes document for more information.

The `ARCHLVL` statement used to be called `ARCHMODE` in previous versions of Hercules but the use of `ARCHMODE` has been deprecated in favor of the new `ARCHLVL` statement. Existing `ARCHMODE` statements should be changed to `ARCHLVL` instead. For the time being however, `ARCHMODE` is still accepted and is treated as simply a synonym for the `ARCHLVL` statement.

ASN_AND_LX_REUSE
++++++++++++++++
ASN_AND_LX_REUSE   ENABLE | DISABLE       (deprecated; use FACILITY)

AUTOINIT
++++++++
AUTOINIT   ON | OFF
The `AUTOINIT` option controls whether device files for emulated tape volumes should be automatically created or not.

When `AUTOINIT` is `ON`, a `devinit` command specifying a file that does not yet exist causes the tape driver to automatically create an empty unlabeled tape volume consisting of just two tapemarks when it discovers the specified file does not exist yet. When `AUTOINIT` is `OFF` a `devinit` command instead fails with an expected "file not found" error. For convenience the default setting is `ON`.

Even more text
