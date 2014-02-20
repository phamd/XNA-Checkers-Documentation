
APP Decomposition
 . Hardware Hiding
	.
 . Software Decision
	. 
 . Behaviour Hiding
	. 

A. Top Level Decomposition
The software system consists of the three modules described
below.
A.1 Hardware-Hiding Module
The hardware-hiding module includes the programs that
need to be changed if any part of the hardware is replaced by a
new unit with a different hardware-software interface but with
the same general capabilities. This module implements virtual
hardware that is used by the rest of the software. The primary
secrets of this module are the hardware-software interfaces de-
scribed in chapters 1 and 2 of the requirements document [9] .
The secrets of this module are the data structures and algo-
rithms used to implement the virtual hardware.

A.2 Behavior-Hiding Module
The behavior-hiding module includes programs that need to
be changed if there are changes in the sections of the require-
ments document that describe the required behavior [9, ch. 3,
4] . The content of those sections is the primary secret of this
module.
These programs determine the values to be sent to
the virtual output devices provided by the hardware-hiding
module.

A.3 Software Decision Module
The software decision module hides software design decisions
that are based upon mathematical theorems, physical facts,
and programming considerations such as algorithmic efficiency
and accuracy. The secrets of this module are not described in
the requirements document.
This module differs from the
other modules in that both the secrets and the interfaces are
determined by software designers. Changes in these modules
are more likely to the motivated by a desire to improve per-
formance than by externally imposed changes.