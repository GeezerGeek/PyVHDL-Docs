

Write a Python testbench
------------------------

This part of the documentation needs more work! For now, look at the Python files in the **plasma** project. Briefly:

* Setup for the simulation is in the file: ``PyVHDL-0.0.1\workspace\plasma\peripheral.py``

* The plasma registers are implemented in the file: ``PyVHDL-0.0.1\workspace\plasma\reg_block.py``. Note the print statements which print register activity messages to the zamiaCAD console.

* 8K of memory for the plasma CPU, and a UART data register are implemented in the file: ``PyVHDL-0.0.1\workspace\plasma\plasma_ram.py``. Note how the ``initialize(self)`` method is used to set up the contents of the memory from a file. 

The **Process** class implements a **concurrent** process. The class has 2 important methods:

* **initialize(self)** is called before the simulation starts to do any setup that is needed.

* **run(self, P, S)** is called to start the process running. The ``while true:`` loop causes the process to continuously run through its code, yielding to other processes when a wait is encountered. The **P** argument is a class whose attributes are the ports defined in the VHDL entity declaration. Signals are accessed as **P.signal_name**. The **signal_name** must be in **UPPER CASE**. the **S** argument is a list containing references to all the signals in the design (`avoid using this for now`).

Each Python file that implements a VHDL architecture has a **setup(tb, P)** function that adds the processes defined in the file to the simulation execution environment. The **tb** argument is a reference to the simulation execution environment. The **P** argument is a string identifying the process.    
