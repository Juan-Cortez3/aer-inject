## aer-inject
This tool allows users to inject PCI-E AER errors on the software level into
a running Linux kernel. This is intended for validation of the PCI-E
driver error recovery handler and PCI-E AER core handler.

### Usage
```
aer-inject aer-file
```
See **SPEC** for the input language description

Some simple tests are in **example** folder.

This tool depends on the Linux kernel to provide AER inject functionality.
Enable these items in the kernel configuration file:
```
CONFIG_PCIEPORTBUS=y
CONFIG_PCIEAER=y
CONFIG_PCIEAER_INJECT=y
```
Apart from that, you also need to add to your `pcie_ports=native` kernel command-line parameters. 
This statement will enable the native PCI-E services(including AER) associated with PCI-E ports
unconditionally.

if you enabled the aer inject kernel config, a **aer_inject** file shall exist in folder **/dev** with
which you could use to inject AER errors in software layer.

**aer-inject** only works on PCI devices which support AER. You can always check it by looking for 
**Advanced Error Reporting** in the **capabilities** section in the output of command `lspci -vvv`.

### Authors

Huang Ying <ying.huang@intel.com>

Basic design, some code and document are based on Andi Kleen's
mce-inject.

*Copyright 2009 by Intel Corporation*
> aer-inject is free software; you can redistribute it and/or modify
> it under the terms of the GNU General Public License as published
> by the Free Software Foundation; version 2.
> aer-inject is distributed in the hope that it will be useful, but
> WITHOUT ANY WARRANTY; without even the implied warranty of
> MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the GNU
> General Public License for more details.
> You should find a copy of v2 of the GNU General Public License
> somewhere on your Linux system; if not, write to the Free Software
> Foundation, Inc., 59 Temple Place, Suite 330, Boston, MA 02111-1307
> USA

