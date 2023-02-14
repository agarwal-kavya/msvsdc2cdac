# Mixed Signal 10-Bit C2C Digital to Analog Converter Based on SCL180nm Process Node.

This project focusses on designing a low power and efficient DAC design in Cadence. For DAC topology C2C architecture of 10bit resolution is chosen over binary-weighted architecture because of its remarkable speed and higher bandwidth, at a cost of distortions caused by parasitic capacitances. 

## Reference Circuit Diagram

#### The schematic of C2C DAC
![Screenshot 2023-02-14 105028](https://user-images.githubusercontent.com/110079729/218646473-ea1c1010-3188-44c3-b67d-438eaecffb9f.png)

DAC switches take the digital bits as inputs and switch the output voltage in between Vref and GND.
If the digital bit is ‘1’ then M1 and M2 transistors will be ON, transistors M3 
and M4 will be OFF. This makes the switch output raise to Vdd. If the digital bit is ‘0’ then
M3 and M4 transistors will be ON, transistors M1 and M2 will be OFF. This makes the 
switch output fall to ground voltage.

#### Schematic of DAC_switch
![Screenshot 2023-02-14 105051](https://user-images.githubusercontent.com/110079729/218646703-548dc433-2227-44a1-a17e-fa51806133f8.png)

## Simulation Results

### Schematic for DAC Switch

![Screenshot from 2023-02-13 23-01-27](https://user-images.githubusercontent.com/110079729/218647760-878ff4ea-4f8d-4cc3-b434-34f35081c38d.png)

### Output Waveforms for DAC Switch
![Screenshot from 2023-02-13 23-09-36](https://user-images.githubusercontent.com/110079729/218647785-ae8fbfcf-ccd1-488a-ad65-3a92a3ed8946.png)


### Schematic for 1-bit DAC
![Screenshot from 2023-02-14 11-16-12](https://user-images.githubusercontent.com/110079729/218650488-805fe3be-b989-4868-8383-a344af4e6205.png)


### Output Waveform for 1-bit DAC
![Screenshot from 2023-02-14 01-36-12](https://user-images.githubusercontent.com/110079729/218647813-f60c41b8-46b8-4721-bf7a-bbcaada4a462.png)

