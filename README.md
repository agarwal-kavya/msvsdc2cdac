# Mixed Signal 10-Bit C2C Digital to Analog Converter Based on SCL180nm Process Node.

This project focusses on designing a low power and efficient DAC design in Cadence. For DAC topology C2C architecture of 10bit resolution is chosen over binary-weighted architecture because of its remarkable speed and higher bandwidth, at a cost of distortions caused by parasitic capacitances. 

## Reference Circuit Diagram

### C2C DAC architecture with DAC switches

![Screenshot 2023-02-14 105028](https://user-images.githubusercontent.com/110079729/218646473-ea1c1010-3188-44c3-b67d-438eaecffb9f.png)

DAC switches take the digital bits as inputs and switch the output voltage in between Vref and GND.
If the digital bit is ‘1’ then M1 and M2 transistors will be ON, transistors M3 
and M4 will be OFF. This makes the switch output raise to Vdd. If the digital bit is ‘0’ then
M3 and M4 transistors will be ON, transistors M1 and M2 will be OFF. This makes the 
switch output fall to ground voltage.

### Schematic of DAC_switch
![Screenshot 2023-02-14 105051](https://user-images.githubusercontent.com/110079729/218646703-548dc433-2227-44a1-a17e-fa51806133f8.png)


## IP Design Specifications

| Parameter| Description| Min | Type | Max | Unit | Condition |
| :---:  | :-: | :-: | :-: | :---:  | :-: | :-: |
|VDD|Digital supply voltage||1.0||V|T=-40 to 85C|
|VREF|Reference voltage|||1.0|V|T=-40 to 85C|
|RES|Resolution| |10||bit|T=27C|
|VFS|Full Scale Voltage|0| |0.999| V |T=27C|



## Simulation Results

## PRE-LAYOUT SIMULATION
### Schematic for DAC Switch

As seen in Schematic, digital inputs are the control terminals to the switches of a DAC. 
Switches are used to switch the output voltage in between Vdd and GND based on the 
digital bits.

![Screenshot from 2023-02-13 23-01-27](https://user-images.githubusercontent.com/110079729/218647760-878ff4ea-4f8d-4cc3-b434-34f35081c38d.png)

The logic of this switch is implemented using a 2 to 1 MUX.

### Output Waveforms for DAC Switch

![Screenshot from 2023-02-13 23-09-36](https://user-images.githubusercontent.com/110079729/218647785-ae8fbfcf-ccd1-488a-ad65-3a92a3ed8946.png)


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

![Screenshot from 2023-02-14 01-36-12](https://user-images.githubusercontent.com/110079729/218647813-f60c41b8-46b8-4721-bf7a-bbcaada4a462.png)

The output here reaches to 500mV based on the calculations.


### Schematic for 2-bit DAC

![Screenshot from 2023-02-17 00-34-10](https://user-images.githubusercontent.com/110079729/219584193-b936b182-4a58-4123-b880-d8ee1fbdc514.png)


### Output Waveform for 2-bit DAC

![Screenshot from 2023-02-17 00-35-22](https://user-images.githubusercontent.com/110079729/219584210-7786821a-40f8-4807-92e2-7248da812bdd.png)



### Schematic for 3-bit DAC

![Screenshot from 2023-02-17 00-36-58](https://user-images.githubusercontent.com/110079729/219584232-26b95530-5dce-492b-86bf-c5746d475cdc.png)

### Output Waveform for 3-bit DAC

![Screenshot from 2023-02-17 00-39-38](https://user-images.githubusercontent.com/110079729/219584267-edfe66c2-535d-4847-bbc9-2dccf70b5b42.png)



### Schematic for 4-bit DAC

![Screenshot from 2023-02-17 12-43-24](https://user-images.githubusercontent.com/110079729/219584382-2c6dc919-9546-42c3-a35f-a6c9ec31073d.png)

### Output Waveform for 4-bit DAC

![Screenshot from 2023-02-17 00-43-24](https://user-images.githubusercontent.com/110079729/219584283-d60d0bbc-2e27-47a2-9c91-dad711caeebe.png)



### Schematic for 5-bit DAC

![Screenshot from 2023-02-17 00-45-28](https://user-images.githubusercontent.com/110079729/219584512-70ca5011-5118-4148-88d2-d344842aa380.png)

### Output Waveform for 5-bit DAC

![Screenshot from 2023-02-17 00-48-59](https://user-images.githubusercontent.com/110079729/219584531-9a0ec31f-e2a4-473d-9a05-20303781d354.png)



### Schematic for 6-bit DAC

![Screenshot from 2023-02-17 12-41-14](https://user-images.githubusercontent.com/110079729/219585125-c9c0e331-3e90-4c13-9aac-7b39e4902091.png)

### Output Waveform for 6-bit DAC

![Screenshot from 2023-02-17 12-42-32](https://user-images.githubusercontent.com/110079729/219585146-b562afa5-c255-4fb9-bb20-9de33c5bac3e.png)



### Schematic for 7-bit DAC

![Screenshot from 2023-02-17 12-34-30](https://user-images.githubusercontent.com/110079729/219585070-63cc06e2-803d-4240-83b6-6423cc511eae.png)

### Output Waveform for 7-bit DAC

![Screenshot from 2023-02-17 12-37-05](https://user-images.githubusercontent.com/110079729/219585086-8871a68d-7488-4ea0-96d4-eb5d3ceb19fb.png)



### Schematic for 8-bit DAC

![Screenshot from 2023-02-17 01-03-24](https://user-images.githubusercontent.com/110079729/219584793-6cdad740-6a26-408b-81ca-41429763af2e.png)

### Output Waveform for 8-bit DAC

![Screenshot from 2023-02-17 01-06-07](https://user-images.githubusercontent.com/110079729/219584821-5e03df81-0f7f-4768-a623-45a90844b845.png)



### Schematic for 9-bit DAC

![Screenshot from 2023-02-17 01-09-26](https://user-images.githubusercontent.com/110079729/219584871-60b1ec44-df90-422c-aede-f492b474078e.png)

### Output Waveform for 9-bit DAC

![Screenshot from 2023-02-17 01-11-35](https://user-images.githubusercontent.com/110079729/219584954-9c7726b9-8762-4202-b8bd-46d1af9899b3.png)



### Schematic for 10-bit DAC

![Screenshot from 2023-02-17 01-13-00](https://user-images.githubusercontent.com/110079729/219584990-a1872177-7fb9-4969-9e72-c19f526fa61b.png)

Total capacitance spread of the C2C 10-bit DAC is 29Cu which is drastically 
low compared to binary weighted capacitor array DAC which will have a total of 1024Cu
capacitance.

### Output Waveforms for 10-bit DAC

Here v0 is the LSB bit and v9 acts as MSB. The inputs are provided using a pulse Signal. 

![Screenshot from 2023-02-17 01-16-42](https://user-images.githubusercontent.com/110079729/219585011-aff8da1c-95de-4dc7-9457-a00faf8e2145.png)

The Output waveform showing the Output reaching 1V with smaller steps.

![Screenshot from 2023-02-17 12-30-14](https://user-images.githubusercontent.com/110079729/219585021-ff71b11d-3b8d-466e-a02a-0dba062c3947.png)


 For DAC topology C2C architecture of 10bit resolution is 
chosen over binary-weighted architecture because of its remarkable speed and higher 
bandwidth, at a cost of distortions caused by parasitic capacitances.


## PRE-LAYOUT CHARACTERIZATION

Waveforms showing Actual and Ideal Outputs: 

![Screenshot from 2023-02-20 23-15-04](https://user-images.githubusercontent.com/110079729/220181456-54c71e75-2d0f-407a-a73a-4093ede3cb60.png)


DNL and INL Characteristics:

![Screenshot from 2023-02-20 23-51-39](https://user-images.githubusercontent.com/110079729/220181569-c28ea6c0-fe0c-44de-b9ad-9832e83c4749.png)


Characteristics Table:

| Parameter| Pre-layout | 
| :---:  | :-: | 
|DNL| -0.44 LSB to 0.26 LSB | 
|INL| -0.487 LSB to 0.057 LSB| 
|Gain Error| 0 | 
|Offset Error| -0.00099 | 
