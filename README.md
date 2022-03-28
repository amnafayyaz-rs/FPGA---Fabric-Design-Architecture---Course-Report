# FPGA-Fabric,Design and Architecture -Course-Report

**Course Instructors**
- Kunal Ghosh
- Nandita Rao

This is the first draft of the report. It is work in progress.

**FPGA Introduction**
--------------------------------------------------------------------------
The field-programmable gate array (FPGA) is an integrated circuit that consists of internal hardware blocks with user-programmable interconnects to customize operation for a specific application. The interconnects can readily be reprogrammed.

![image](https://user-images.githubusercontent.com/86342952/160444516-987dfe8d-151c-4429-b01c-1a9e6f96cd48.png)



Configurable logic blocks (CLBs) are FPGAs fundamental elements that are surrounded by a system of programmable interconnects, called a fabric, that routes signals between CLBs. Input/output (I/O) blocks interface between the FPGA and external devices.

**FPGA Logic Blocks**

![image](https://user-images.githubusercontent.com/86342952/160444091-a5a28b94-374f-40c0-94b2-f52e59bd8025.png)


**ASIC versus FPGA**

![image](https://user-images.githubusercontent.com/86342952/160445097-73827d14-ec1c-4ddf-a121-aa88c045f019.png)

Day 1
---------------------------------------
**Lab 1 – Counter**

**Tool used - Vivado**

**FPGA Borard - Basys 3** 


![image](https://user-images.githubusercontent.com/86342952/160443807-d9e9db62-99e8-4e4f-ad52-0afaf0a7c1b3.png)


**Simulation**

 ![image](https://user-images.githubusercontent.com/86342952/160274339-5c6e189d-8c89-4898-8c9d-0dd789d651f2.png)


**RTL Analysis**

**Open Elaborated Design**

![image](https://user-images.githubusercontent.com/86342952/160274348-83ecb811-dd34-4708-a78a-b2f23308ea75.png)

 
 

**I/O Planning**

![image](https://user-images.githubusercontent.com/86342952/160274358-6c8b66ce-d935-4770-bd34-b9cda74cd03b.png)

 

**Synthesis**

**Timing summary**

 
![image](https://user-images.githubusercontent.com/86342952/160274367-be5b82f3-8483-4817-bf98-e6cdbaa53b3f.png)

**setting user constraints**

![image](https://user-images.githubusercontent.com/86342952/160276226-778a7468-32b9-4532-b91d-9b7591bc2c36.png)

**Schematic**

![image](https://user-images.githubusercontent.com/86342952/160276275-67ca0e32-d2e9-4698-a167-dc565c9dde87.png)

**Utilization report**

![image](https://user-images.githubusercontent.com/86342952/160276390-6ba6b1bb-0a6b-4af4-afc8-09398f827bf6.png)

Bitstream Generation and Loading hardware (Couldn't load the bitstream as I was using Vivado on server and it was restricted for external device connection)


![image](https://user-images.githubusercontent.com/86342952/160277048-49f9fd0d-0e02-475f-a210-b4ac39b3c66a.png)

**Detailed Path Report**

![image](https://user-images.githubusercontent.com/86342952/160277246-69e9f8e7-72dd-4f0f-b6af-3904e6eff00f.png)

Modified the counter, added VIO template and then simulated the design again.

**Elaborated design:**

![image](https://user-images.githubusercontent.com/86342952/160279132-e77e86ed-b060-4e97-87db-19502a9685ec.png)

**Floor Planning window view:**

![image](https://user-images.githubusercontent.com/86342952/160279169-72faf58c-69ca-46fd-9240-dc6be59146f6.png)

**Clock pin view:**

![image](https://user-images.githubusercontent.com/86342952/160279261-d80baf37-05ef-45ee-a310-df6202d14e47.png)




![image](https://user-images.githubusercontent.com/86342952/160279096-e9558bd9-74cc-481c-bbb8-3bc77b9fcc71.png)


Program counter on FPGA, observed output through LEDs on FPGA

Day 2
---------------------------------------------------------------------
**OpenFPGA Introduction**

OpenFPGA is an Opensource Framework Enabling Rapid Prototyping of Customizable FPGAs.

![image](https://user-images.githubusercontent.com/86342952/160452354-c5133c95-f471-4bed-9eb1-212e0b23131c.png)


**VTR**

![image](https://user-images.githubusercontent.com/86342952/160455326-1d23428a-e16b-445c-98bb-570f21315a03.png)



**VTR Quick Start Guide**

[VTR Quick Start Guide](https://docs.verilogtorouting.org/en/latest/quickstart/)

FPGA Architecture description can be founde here :

[FPGA Architecture](https://docs.verilogtorouting.org/en/latest/arch/reference/)



Day 3
------------------------------------------

 

![image](https://user-images.githubusercontent.com/86342952/160456701-8a1d23e4-8a7b-4b2d-b903-6d550361e4c5.png)



Day 4 
----------------------------------------

**Circuit Statistics:**

  Blocks: 17
    .input :       3
    .latch :       4
    .output:       4
    4-LUT  :       6
  Nets  : 13
    Avg Fanout:     2.5
    Max Fanout:     5.0
    Min Fanout:     1.0
  Netlist Clocks: 1
  
 
**SOFA**

Skywater Opensource FpgA (SOFA) is a fully open-source embedded FPGA IP library, from the architecture description to production ready layouts. 

![image](https://user-images.githubusercontent.com/86342952/160457771-77fd48da-b1e8-4418-8561-6057e83f2c23.png)

[SOFA](https://skywater-openfpga.readthedocs.io/en/latest/device/introduction/)
  
**Counter Design on SOFA**

```
Pb types usage
inpad        : 3
outpad       : 4
lut4         : 2
ble4         : 2
ff           : 4
fle          : 6
clb          : 1
lut3inter    : 4
ble3         : 4
io           : 7
lut3         : 4
lut          : 6
```

**hold timing met**

```
clock clk (rise edge)                                            0.000     0.000
clock source latency                                             0.000     0.000
clk.inpad[0] (.input)                                            0.000     0.000
out[0].clk[0] (.latch)                                           0.000     0.000
clock uncertainty                                                0.000     0.000
cell hold time                                                   0.390     0.390
data required time                                                         0.390
--------------------------------------------------------------------------------
data required time                                                        -0.390
data arrival time                                                          4.170
--------------------------------------------------------------------------------
slack (MET)                                                                3.780
```

**setup timing met**

```
clock clk (rise edge)                                           35.000    35.000
clock source latency                                             0.000    35.000
clk.inpad[0] (.input)                                            0.000    35.000
out[3].clk[0] (.latch)                                           0.110    35.110
clock uncertainty                                                0.000    35.110
cell setup time                                                 -0.390    34.720
data required time                                                        34.720
--------------------------------------------------------------------------------
data required time                                                        34.720
data arrival time                                                        -16.420
--------------------------------------------------------------------------------
slack (MET)                                                               18.300
```

Day 5
----------------------------

**RVMyth process utilization**

```
Pb types usage...
  inpad        : 2
  outpad       : 8
  shift_reg    : 3
  lut4         : 3031
  ble4         : 3031
  ff           : 1807
  fle          : 3477
  clb          : 447
  lut3inter    : 443
  ble3         : 663
  io           : 10
  lut3         : 648
  lut          : 3679
 ```

```
Logic Element (fle) detailed count:
  Total number of Logic Elements used : 3477
  LEs used for logic and registers    : 1741
  LEs used for logic only             : 1732
  LEs used for registers only         : 4
  ```
  
**Hold timing:**
  
```
clock clk (rise edge)                                            0.000     0.000
clock source latency                                             0.000     0.000
clk.inpad[0] (.input)                                            0.000     0.000
CPU_is_bltu_a3.clk[0] (.latch)                                   0.000     0.000
clock uncertainty                                                0.000     0.000
cell hold time                                                   0.390     0.390
data required time                                                         0.390
--------------------------------------------------------------------------------
data required time                                                        -0.390
data arrival time                                                          1.350
--------------------------------------------------------------------------------
slack (MET)                                                                0.960
```

**Setup timing:**

```
clock clk (rise edge)                                          200.000   200.000
clock source latency                                             0.000   200.000
clk.inpad[0] (.input)                                            0.000   200.000
CPU_Xreg_value_a4[22][31].clk[0] (.latch)                        0.110   200.110
clock uncertainty                                                0.000   200.110
cell setup time                                                 -0.390   199.720
data required time                                                       199.720
--------------------------------------------------------------------------------
data required time                                                       199.720
data arrival time                                                       -192.180
--------------------------------------------------------------------------------
slack (MET)                                                                7.540
```

**RVMyth simulation of post synthesis netlist on Vivado**

![image](https://user-images.githubusercontent.com/86342952/160461998-6a32a396-86bf-4c60-9233-a844ac6f6799.png)



