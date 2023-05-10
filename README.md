# Mixed Signal 10-Bit C2C Digital to Analog Converter Based on SCL180nm Process Node.

This project focusses on designing a low power and efficient DAC design in Cadence. For DAC topology C2C architecture of 10bit resolution is chosen over binary-weighted architecture because of its remarkable speed and higher bandwidth, at a cost of distortions caused by parasitic capacitances. 



## Table of Contents
- [1. Introduction to C2C DAC](#1-Introduction-to-C2C-DAC)
- [2. C2C DAC architecture with DAC switches](#2-C2C-DAC-architecture-with-DAC-switches)
- [3. Schematic of DAC_switch](#3-Schematic-of-DAC_switch)
- [4. IP Design Specifications](#4-IP-Design-Specification)
- [5. Simulation Results](#5-Simulation-Results)
  * [ DAC Switch](#DAC-switch)
  * [ 1-Bit DAC subcircuit](#1-bit-dac-subcircuit)
  * [ 2-Bit DAC subcircuit](#2-bit-dac-subcircuit)
  * [ 3-Bit DAC subcircuit](#3-bit-dac-subcircuit)
  * [ 4-Bit DAC subcircuit](#4-bit-dac-subcircuit)
  * [ 5-Bit DAC subcircuit](#5-bit-dac-subcircuit)
  * [ 6-Bit DAC subcircuit](#6-bit-dac-subcircuit)
  * [ 7-Bit DAC subcircuit](#7-bit-dac-subcircuit)
  * [ 8-Bit DAC subcircuit](#8bit-dac-subcircuit)
  * [ 9-Bit DAC subcircuit](#9bit-dac-subcircuit)
  * [ 10-Bit-DAC](#10-bit-dac)
- [6. Schematic for Layout ](#6-Schematic-for-Layout)
- [7. Layout ](#7-LAYOUT)

## 1. Introduction to C2C DAC

DACs convert discrete digital signals into continuous analog signals. Among all the DAC
architectures Capacitive DACs are preferred because of their reduced design complexity,
optimized power and improved matching. Exclusively for medium to high resolution
applications capacitive DACs are chosen over resistive and current steering DACs. Even
though the Capacitive DAC based solution provides many benefits, it still faces a
bottleneck in sizing the capacitors, capacitor mismatch and parasitic capacitance degrading
the DAC performance. With technology scaling, digital solutions will also provide better
portability between IC fabrication technologies and flexibility, and ultimately result in
lower power and cost.



## 2. C2C DAC architecture with DAC switches

![Screenshot 2023-02-14 105028](https://user-images.githubusercontent.com/110079729/218646473-ea1c1010-3188-44c3-b67d-438eaecffb9f.png)

DAC switches take the digital bits as inputs and switch the output voltage in between Vref and GND.
If the digital bit is ‘1’ then M1 and M2 transistors will be ON, transistors M3 
and M4 will be OFF. This makes the switch output raise to Vdd. If the digital bit is ‘0’ then
M3 and M4 transistors will be ON, transistors M1 and M2 will be OFF. This makes the 
switch output fall to ground voltage.

## 3. Schematic of DAC_switch

Switches are used to switch the output voltage in between Vdd and GND based on the 
digital bits.

![Screenshot 2023-02-14 105051](https://user-images.githubusercontent.com/110079729/218646703-548dc433-2227-44a1-a17e-fa51806133f8.png)


## 4. IP Design Specifications

| Parameter| Description| Min | Type | Max | Unit | Condition |
| :---:  | :-: | :-: | :-: | :---:  | :-: | :-: |
|VDD|Digital supply voltage||1.8||V|T=-40 to 85C|
|VREFH|Reference voltage high|||1.8|V|T=-40 to 85C|
|VREFL|Reference voltage low|0.0|||V|T=-40 to 85C|
|RES|Resolution| |10||bit|T=27C|
|VFS|Full Scale Voltage|0| |1.7982| V |T=27C|



## 5. Simulation Results

## 5.1 PRE-LAYOUT SIMULATION

## DAC Switch
### Schematic for DAC Switch

As seen in Schematic, digital inputs are the control terminals to the switches of a DAC. 
Switches are used to switch the output voltage in between Vdd and GND based on the 
digital bits.

![Screenshot from 2023-02-13 23-01-27](https://user-images.githubusercontent.com/110079729/218647760-878ff4ea-4f8d-4cc3-b434-34f35081c38d.png)

The logic of this switch is implemented using a 2 to 1 MUX.

### Output Waveforms for DAC Switch

![Screenshot from 2023-02-13 23-09-36](https://user-images.githubusercontent.com/110079729/218647785-ae8fbfcf-ccd1-488a-ad65-3a92a3ed8946.png)

## 1-Bit DAC subcircuit
### Schematic for 1-bit DAC

DAC switches take the digital bits as inputs and switch the output voltage in between Vref 
and GND.

![Screenshot from 2023-02-14 11-16-12](https://user-images.githubusercontent.com/110079729/218650488-805fe3be-b989-4868-8383-a344af4e6205.png)

Based on the 
digital bits output of DAC is calculated as: ` 𝑉𝑜𝑢𝑡𝐶𝑡𝑜𝑡𝑎l = 𝐶𝑒𝑓𝑓𝑒𝑐𝑡𝑖𝑣𝑒 ∗ 𝑉𝑟𝑒𝑓 ∗ (∑𝑏𝑖2^(−(𝑁−𝑖)))  ` ,
where bi is the digital input bits from Pulse input.
 Ctotal is the effective output 
capacitance of the entire C2C ladder network which is equal to 2Cu where Cu is the unit 
capacitance.


### Output Waveform for 1-bit DAC

![Screenshot (501)](https://github.com/agarwal-kavya/msvsdc2cdac/assets/110079729/071c4a81-757a-4850-a96c-51510b7fb4f6)

The output here reaches to 900mV based on the calculations.

## 2-Bit DAC subcircuit
### Schematic for 2-bit DAC

![Screenshot from 2023-02-17 00-34-10](https://user-images.githubusercontent.com/110079729/219584193-b936b182-4a58-4123-b880-d8ee1fbdc514.png)


### Output Waveform for 2-bit DAC

![Screenshot (499)](https://github.com/agarwal-kavya/msvsdc2cdac/assets/110079729/c436a013-2e00-4e32-9b48-5a60fc26b6a4)


## 3-Bit DAC subcircuit
### Schematic for 3-bit DAC

![Screenshot from 2023-02-17 00-36-58](https://user-images.githubusercontent.com/110079729/219584232-26b95530-5dce-492b-86bf-c5746d475cdc.png)

### Output Waveform for 3-bit DAC

![Screenshot (498)](https://github.com/agarwal-kavya/msvsdc2cdac/assets/110079729/c5e77d84-ae9f-4822-9f7f-67fa5383bac0)


## 4-Bit DAC subcircuit
### Schematic for 4-bit DAC

![Screenshot from 2023-02-17 12-43-24](https://user-images.githubusercontent.com/110079729/219584382-2c6dc919-9546-42c3-a35f-a6c9ec31073d.png)

### Output Waveform for 4-bit DAC

![Screenshot (497)](https://github.com/agarwal-kavya/msvsdc2cdac/assets/110079729/33d845e9-7d95-4d1a-9241-6d146a7b44cd)


## 5-Bit DAC subcircuit
### Schematic for 5-bit DAC

![Screenshot from 2023-02-17 00-45-28](https://user-images.githubusercontent.com/110079729/219584512-70ca5011-5118-4148-88d2-d344842aa380.png)

### Output Waveform for 5-bit DAC

![Screenshot (496)](https://github.com/agarwal-kavya/msvsdc2cdac/assets/110079729/6e614e4d-f928-4062-83ba-62d542b53ab4)


## 6-Bit DAC subcircuit
### Schematic for 6-bit DAC

![Screenshot from 2023-02-17 12-41-14](https://user-images.githubusercontent.com/110079729/219585125-c9c0e331-3e90-4c13-9aac-7b39e4902091.png)

### Output Waveform for 6-bit DAC

![Screenshot (495)](https://github.com/agarwal-kavya/msvsdc2cdac/assets/110079729/a9120fc3-a65e-499a-bbf1-fd6e42866ca7)


## 7-Bit DAC subcircuit
### Schematic for 7-bit DAC

![Screenshot from 2023-02-17 12-34-30](https://user-images.githubusercontent.com/110079729/219585070-63cc06e2-803d-4240-83b6-6423cc511eae.png)

### Output Waveform for 7-bit DAC

![Screenshot (494)](https://github.com/agarwal-kavya/msvsdc2cdac/assets/110079729/bf165669-94d7-40de-ac09-153aa83e452a)


## 8-Bit DAC subcircuit
### Schematic for 8-bit DAC

![Screenshot from 2023-02-17 01-03-24](https://user-images.githubusercontent.com/110079729/219584793-6cdad740-6a26-408b-81ca-41429763af2e.png)

### Output Waveform for 8-bit DAC

![Screenshot (493)](https://github.com/agarwal-kavya/msvsdc2cdac/assets/110079729/ad7dc420-01b9-4e48-b412-fa053fbbe6e2)


## 9-Bit DAC subcircuit
### Schematic for 9-bit DAC

![Screenshot from 2023-02-17 01-09-26](https://user-images.githubusercontent.com/110079729/219584871-60b1ec44-df90-422c-aede-f492b474078e.png)

### Output Waveform for 9-bit DAC

![Screenshot (492)](https://github.com/agarwal-kavya/msvsdc2cdac/assets/110079729/2c44088d-6ce7-4027-b005-b385091d1327)


## 10-Bit DAC 
### Schematic for 10-bit DAC

![Screenshot from 2023-02-17 01-13-00](https://user-images.githubusercontent.com/110079729/219584990-a1872177-7fb9-4969-9e72-c19f526fa61b.png)

Total capacitance spread of the C2C 10-bit DAC is 29Cu which is drastically 
low compared to binary weighted capacitor array DAC which will have a total of 1024Cu
capacitance.

### Output Waveforms for 10-bit DAC

Here v0 is the LSB bit and v9 acts as MSB. The inputs are provided using a pulse Signal. 
The Output waveform showing the Output reaching 1.8V with smaller steps.

![Screenshot from 2023-03-01 08-09-08](https://user-images.githubusercontent.com/110079729/222167689-ad728c03-34ea-49cc-8fb4-6e9784518cd1.png)


 For DAC topology C2C architecture of 10bit resolution is 
chosen over binary-weighted architecture because of its remarkable speed and higher 
bandwidth, at a cost of distortions caused by parasitic capacitances.


## 6. PRE LAYOUT CHARACTERIZATION

Waveforms showing Actual and Ideal Outputs: 

![Screenshot from 2023-03-01 08-13-42](https://user-images.githubusercontent.com/110079729/222167242-6daa7ff2-a753-4533-bddb-bfb02f396009.png)

DNL and INL Characteristics:

![Screenshot from 2023-03-01 08-21-01](https://user-images.githubusercontent.com/110079729/222167358-27d0fe0a-504b-4654-a307-e8837c362cf8.png)

Characteristics Table:

| Parameter| Pre-layout | 
| :---:  | :-: | 
|DNL| -0.44 LSB to 0.26 LSB | 
|INL| -0.487 LSB to 0.057 LSB| 
|Gain Error| 0 | 
|Offset Error| -0.001757 | 

## 7. Schematic for Layout

The schematic obtained by replacing all the voltage sources is as:

![sch](https://github.com/agarwal-kavya/msvsdc2cdac/assets/110079729/72ba7eff-8aa9-4326-8518-308d3216322b)


## 8. LAYOUT of 10 bit C2C DAC created in Cadence Virtuoso using SCL180 pdk:

The obtained layout is as:

![Screenshot from 2023-05-10 12-23-29](https://github.com/agarwal-kavya/msvsdc2cdac/assets/110079729/fbb7a291-121e-4ff4-a481-b08068304993)


### Magnified images of layout:

![Screenshot from 2023-05-10 12-24-05](https://github.com/agarwal-kavya/msvsdc2cdac/assets/110079729/11c74022-ab3d-41f1-8560-4f6cdf9d10f0)

![Screenshot from 2023-05-10 12-24-43](https://github.com/agarwal-kavya/msvsdc2cdac/assets/110079729/4464919a-ad5d-41ae-88da-dc22419926e5)

![Screenshot from 2023-05-10 12-24-54](https://github.com/agarwal-kavya/msvsdc2cdac/assets/110079729/1049f52f-51cd-4e1e-a844-52009dd9566a)



## 9. Contributors 

- **Kavya Agarwal** 
- **Kunal Ghosh** 

## 10. Acknowledgments

- Kunal Ghosh, Director, VSD Corp. Pvt. Ltd.
- Steven Bos


## 11. Contact Information

- Kavya Agarwal, Postgraduate Student, International Institute of Information Technology, Bangalore  kavya11.ag@gmail.com
- Kunal Ghosh, Director, VSD Corp. Pvt. Ltd. kunalghosh@gmail.com


## 12. Future Work

- The post layout simulation has to be carried out for the design.

## 13. References
- [kunalg123/avsddac_workshop](https://github.com/kunalg123/avsddac_workshop#readme)
- [Wright State University - 10 bit DAC Design](https://corescholar.libraries.wright.edu/cgi/viewcontent.cgi?article=3253&context=etd_all)
