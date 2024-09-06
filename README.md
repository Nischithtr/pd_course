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
  2. Flop Ratio:
     ![image](https://github.com/user-attachments/assets/6651220e-61b4-46c4-86b1-fa269f4572f5)
     Flop ratio = 1613/14876*100 = 10.84%

Output: 
  1. Gate level netlist
     ![image](https://github.com/user-attachments/assets/dc4f47a6-2d97-4650-8f06-1662a7b2a3af)
  2. Pre-placement timing report:
     ![image](https://github.com/user-attachments/assets/9ee3caf4-24bd-4762-b888-df08bbce4002)

Floorplan:

Inputs:
  1. Config.tcl:
     ![image](https://github.com/user-attachments/assets/bfbfffcb-d7d0-496e-88c2-9a0d9f740ba8)
     1. Equidistant IO placement
     2. IO vertical layer is metal2, IO horizontal layer is metal3
   2. sky130A_sky130_fd_sc_hd_config.tcl:
      ![image](https://github.com/user-attachments/assets/406ab7d6-917b-4e1e-97f9-e309d2c8591d)
      1. Core utilization: 35%

Results:
  1. Die area:
     ![image](https://github.com/user-attachments/assets/f50d64e0-5597-4274-a301-ca5247d30660)
     Area = (660685-0)/1000 * (671405-0)/1000 = 443587u
  2. Equidistant IO pins:
     ![image](https://github.com/user-attachments/assets/3a04e4ae-3397-47cb-932b-f7831a2f546c)
  3. Horizontal pins on metal3, vertical pins on metal2
     ![image](https://github.com/user-attachments/assets/abb15dcd-c5fd-4b79-b927-04159c8ff65e)
  4. Standard cells on lower left:
     ![image](https://github.com/user-attachments/assets/5fc51582-7e51-4d2b-900a-ba26f2599811)
  5. Tapcell spacing is 13u:
     ![image](https://github.com/user-attachments/assets/ae87663e-4bc1-4829-aebe-6ff8316b092a)
  6. IO placement with FP_IO_MODE is set to zero:
     ![image](https://github.com/user-attachments/assets/9480e908-ae43-427e-b1de-2673ed862b67)

Placement:

Results:
  1. Def after placement:
  2.   ![image](https://github.com/user-attachments/assets/25026d16-29fc-429a-891b-2094a2d10196)


  
  





  
