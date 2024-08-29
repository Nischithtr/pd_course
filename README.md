# pd_course
Design inputs:
  1. Verilog file: Contains RTL data
     ![image](https://github.com/user-attachments/assets/e3b171b9-02a3-41c9-846e-823901518bad)
  2. SDC: Defines clock
     ![image](https://github.com/user-attachments/assets/cc421b41-4929-48c7-959f-73c47cc13b16)

Config file:
  1. Config.tcl in design directory:
     ![image](https://github.com/user-attachments/assets/e0359a86-9f5b-4a0e-a4f1-19282bd5bccf)
     1. Sets the design name
     2. Provides pointers to verilog and SDC files
     3. Overrides the clock perion (In this case both SDC and config file periods are ns)
     4. Provides pointer to sky130A_sky130_fd_sc_hd.tcl file
   2. sky130A_sky130_fd_sc_hd.tcl : Sets additional knobs. The data in this file has the highest priority
      ![image](https://github.com/user-attachments/assets/5693faa4-4857-4f0b-a5ff-7883f335b7da)
  3. Config.tcl in run directory: List of all the parameters used:
     ![image](https://github.com/user-attachments/assets/a947b4b3-d074-4d91-b289-1ffb2021715e)


Design preparation:
![image](https://github.com/user-attachments/assets/f26804f2-386b-4b5f-a3ac-45f205b6c1f5)

Tasks:
Merge design lef and techlef to create merged.lef:
  1. Tech lef data:
     ![image](https://github.com/user-attachments/assets/7652a8ee-d458-4e63-bb6b-7811b666b04f)
  2. Design data:
     ![image](https://github.com/user-attachments/assets/82b13a33-1da2-4a57-89c1-e6225f922f73)

cmds.log snapshot:
![image](https://github.com/user-attachments/assets/a2617ebb-ac8e-4e86-abd7-b47d1b8b8993)

Synthesis:
![image](https://github.com/user-attachments/assets/8a49020d-6919-422e-a518-fac4f8b4aaf7)

Observation:
  1. Chip area: 147712.92u
     ![image](https://github.com/user-attachments/assets/04c16645-4af3-4a08-90c3-77ce7e7c020b)
