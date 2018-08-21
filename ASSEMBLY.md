# Assembly

Since there are three different voltage domains is important to check that the different voltages are provided correctly. Keep this list while assembling the board. Go ahead only if the previous step ended successfully.

Step|Aim|Components|Expected Result
--|--|--|--
1|The USB provide 5V|J1|Around 5V between TP25 (+) and TP28(-).
2|The battery polarity is correct|J2| 3.4 < V < 4.2 between  TP23(+) and TP28(-).
3|The charger works|IC7, C11, C12, C13, R19, R22, R24, R26, R27, R28|LED7 lights up. TP31 is low. Between TP30 and TP28 we have a voltage between 3.4V and 5.5V. **Note 1**.
4|The power button latch works|S1, IC11|After pressing S1, TP33 goes high. Pressing S1 again and TP33 return to ground.
5|The 3V3 switching circuit works|IC12, R36, C23, C25, C27, C29, L4|TP34 is in HiZ. After pressing S1 between TP34 and TP28 there are 3V3. Repeat with USB + Battery and Battery only.
6|The 5V switching circuit works|IC13, R37, C24, C26, C28, C30|TP35 is in HiZ. After pressing S1 between TP35 and TP28 there are 5V. Repeat with USB + Battery and Battery only.

If all the 6 steps are passed it's possible to mount the other components and proceed with the communication tests. See **TODO** for more information.

As recap, with USB and/or battery connected we should have the following voltages (the ground  reference is **TP28**):

Test Point|Voltage|Source
--|--|--
TP25|~5V|USB port (J1)
TP23|3.4 < V < 4.2|Battery (J2)
TP31|TP23 < V < TP25|BQ74025 (IC7)
TP34|3V3|TPS63001 (IC12)
TP35|5V|TPS63002 (IC13)

Be sure to power on the board by pressing **S1**.

# Notes
1. The battery charger gots 2 input pins to select the max current used to charge the battery. Since them are driven by the CPU, short **TP26** and **TP27** to **TP28** to set the charging current to **100mA**. Keep the jumpers until we solder the CPU.
