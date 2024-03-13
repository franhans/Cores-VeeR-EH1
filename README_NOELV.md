### Useful commands and NOEL-V modifications

Some modifications have been done to the original repo, namely:
* Makefile compilation flags have been modified
* Inside the CoreMark C code some functions have been added to configure, reset and print performance monitor counters.
* Some defines have been added to perform simulation in QuestaSim for NOEL-V core: NOELV, SIMULATION, CHECK and PERF. NOELV and SIMULATION have to be set to 1 when simulating in the NOEL-V core. The UART is not implemented for NOEL-V simulations, if CHECK is set, the test will make use of the ahbrep component to print some information. PERF controls which set of PERF counters is used during NOEL-V simulation.

To obtain a decent score in CoreMark in the SweRV-VeeR-EH1 we have to compile and execute cmark_dccm test to make use of the data tightly-coupled memory.
To generate a srec file that can be executed in the NOEL-V the test cmark has to be compiled. 


To execute CoreMark in SweRV-VeeR-EH1 in QuestaSim:
`make -f $RV_ROOT/tools/Makefile vlog TEST=cmark_dccm`

To generate srec file for NOEL-V simulation:
`make -f $RV_ROOT/tools/Makefile ram.srec TEST=cmark_dccm`

**RV_ROOT** should point to the root directory.