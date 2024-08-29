# pd_course
Design inputs:
  1. Verilog file: Contains RTL data
     ![image](https://github.com/user-attachments/assets/e3b171b9-02a3-41c9-846e-823901518bad)
  2. SDC: Defines clock
     ![image](https://github.com/user-attachments/assets/cc421b41-4929-48c7-959f-73c47cc13b16)

Config file:
  1. Config.tcl:
     ![image](https://github.com/user-attachments/assets/e0359a86-9f5b-4a0e-a4f1-19282bd5bccf)
     1. Sets the design name
     2. Provides pointers to verilog and SDC files
     3. Overrides the clock perion (In this case both SDC and config file periods are ns)
     4. Provides pointer to sky130A_sky130_fd_sc_hd.tcl file
   2. sky130A_sky130_fd_sc_hd.tcl : Sets additional knobs. The data in this file has the highest priority
      ![image](https://github.com/user-attachments/assets/5693faa4-4857-4f0b-a5ff-7883f335b7da)

