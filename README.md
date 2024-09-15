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

Standard Cell Charactrerization:

Inverter layout: ![image](https://github.com/user-attachments/assets/7859e8f7-62a9-41ec-803f-efe050cb25aa)
Nmos: ndiff intersection with poly: ![image](https://github.com/user-attachments/assets/90ba446b-b6a5-4753-bd55-8c5d91f6f07f)
Pmos: pdiff intersection with poly: ![image](https://github.com/user-attachments/assets/cd8aa44a-4584-4055-a55c-1a8d146e7bca)
Drain connectivity to Y: ![image](https://github.com/user-attachments/assets/ded1511a-7fe4-4363-9eb3-a8c6d410c826)
Pmos source connectivity to VDD: ![image](https://github.com/user-attachments/assets/3e47acf0-659e-422a-8cf6-5e2abdf59077)
Nmos source connectivity to VSS: ![image](https://github.com/user-attachments/assets/dceb4e02-3fc0-4bb5-8e11-914c54113a90)
DRC violation when we delete layers: ![image](https://github.com/user-attachments/assets/26441748-9419-4578-aa58-9aae71a2316b)
DRC error: ![image](https://github.com/user-attachments/assets/17b9f4f8-713b-4f5a-b7b4-022fadf7641c)
extract all --> .ext file:
  ![image](https://github.com/user-attachments/assets/4a475ba7-b5b0-4fec-ab87-a21e28e5bdf5)
ext2spice --> .spice file:
  ![image](https://github.com/user-attachments/assets/9f888b3d-226a-4a89-8ed1-1010ebc0b9d4)
Spice model: ![image](https://github.com/user-attachments/assets/48c1e836-881a-4302-9fd8-05620159d490)
Input spice to ngspice: ![image](https://github.com/user-attachments/assets/8f92400c-739b-41c2-a667-cdc6ec9ef870)
ngspice run: ![image](https://github.com/user-attachments/assets/b64f9827-9736-4c7d-aa3a-7e076551f3cd)
Input vs output: ![image](https://github.com/user-attachments/assets/3933e4a2-ce65-4879-8327-df55404bc625)
  1. Rise transition time:
     ![image](https://github.com/user-attachments/assets/688795c5-f6b8-43f7-83c2-857357e6dbfa)
     2.19042e-9 - 2.13018e-9 = 60.24 ps
  2. Fall transition time:
     4.09173e-9 - 4.04881e-9 = 42.92 ps
  3. Rise delay:
     2.15209e-9 - 2.105e-9 =  47.09 ps
  4. Fall delay:
     4.07293e-9 - 4.05016e-9 = 22.77 ps    

DRC tests:

met3 design violations: ![image](https://github.com/user-attachments/assets/0f80c942-a544-4895-b119-0baa1441f786)
3.6 design error definition: ![image](https://github.com/user-attachments/assets/c7b95593-8868-4c87-8177-bc06fa6643e8)
DRC reason using drc why: ![image](https://github.com/user-attachments/assets/0ee5dab4-746d-46c2-b6ad-5b325ed79a06)
Poly spacing issue: ![image](https://github.com/user-attachments/assets/d674cce7-0720-4a54-b606-85f7946f9493)



Timing modeling using delay tables:

Tracks info: ![image](https://github.com/user-attachments/assets/2db1084a-2c29-46f9-9e1b-7e92e23ec6d0)
![image](https://github.com/user-attachments/assets/3f477a30-80fd-489e-8748-3796ceca2f80)
Width: 3 units
Height: 8 units
Defining ports in magic: ![image](https://github.com/user-attachments/assets/6cf26d2b-34ff-49fa-ba45-14aa90924545)
Creating lef: ![image](https://github.com/user-attachments/assets/c3c447e2-be47-42df-8631-2cdd2127f494)
Lef file: ![image](https://github.com/user-attachments/assets/bbfce380-48f6-4e50-8135-b1127dcf69f2)

The characterized cell is included by the tool: ![image](https://github.com/user-attachments/assets/8d3870aa-3854-4eca-aa32-dc349753b893)
Negative slack: ![image](https://github.com/user-attachments/assets/ec475fde-3cc4-45fa-bb8b-1c78a48d7e97)
Synth strategy: ![image](https://github.com/user-attachments/assets/4744b078-1b11-4427-a382-329828491c0f)
Fixing slack with DELAY 0 strategy: ![image](https://github.com/user-attachments/assets/2e890617-04c2-47ce-b85b-d53c598cfde2)
Macro vsdinv included after floorplan: ![image](https://github.com/user-attachments/assets/85033f62-6b4b-4fc0-91e8-dba8fdd486e2)
vsdinv included in def post placement: ![image](https://github.com/user-attachments/assets/ac343176-9e58-4f6f-bd5a-d5026605237e)


STA:

STA conf: ![image](https://github.com/user-attachments/assets/31e31876-58be-4ed1-9b32-4a4310504c3e)
SDC: ![image](https://github.com/user-attachments/assets/52fa8cbc-d356-42d7-8454-8874d551d369)
Zero slew: ![image](https://github.com/user-attachments/assets/678b7476-1a80-4c5e-9484-1365c8a3b03d)

CTS:

CTS inputs: ![image](https://github.com/user-attachments/assets/9d47c1ae-477f-4478-bb64-e23176887fee)
CTS run: ![image](https://github.com/user-attachments/assets/84c3ba94-ce71-44b4-831e-fa9bd7d673ff)
Post CTS def: ![image](https://github.com/user-attachments/assets/6039e1eb-88e3-4d57-b9d7-0a411873a495)
Post CTS STA hold: ![image](https://github.com/user-attachments/assets/504c809c-b161-4095-b235-cf8cc7d99c48)
Post CTS STA setup: ![image](https://github.com/user-attachments/assets/c1dc8b56-a210-43c4-8212-7e225e64cfd1)

CTS without drive strength 1 buffer: ![image](https://github.com/user-attachments/assets/0d3e8a5a-32d9-4e25-84e3-a1114dcedec3)
Post CTS STA hold: ![image](https://github.com/user-attachments/assets/36a4be61-ae26-4ada-8b05-a6d23559c428)
Post CTS STA setup: ![image](https://github.com/user-attachments/assets/5b5738a2-f772-43f4-a565-e09630b53720)
Clock skew: ![image](https://github.com/user-attachments/assets/f08dd4d0-61e6-42a4-9a50-b67d391da0f1)

























  
  





  
