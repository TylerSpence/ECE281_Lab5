ECE281_Lab5
===========
#List of functionality achieved

1st Program Demo on FPGA (25 pts)	

2nd Program Demo in PRISM Simulator  (25 pts)

2nd Program Demo on FPGA	(5 pts)


#Discussion of first program operation.

The first program is implemented on the fpga using the following instantiation code
```vhdl
Inst_PRISM: PRISM PORT MAP(
		Clock => ClockBus_sig(21),
		Reset_L => not btn(3),
	--	Control_Bus => ,
		Input_0 => switch(3 downto 0),
		Input_1 => switch(7 downto 4),
		Input_2 =>"0000" ,
		Input_3 => "0000",
		Output_0 => nibble3,
		Output_1 => nibble2,
		Output_2 => nibble1,
		Output_3 => nibble0
	);
```

In addition, the use of the nibbles higher up in the program was commented out as seen below.
```vhdl
--nibble0 <= 
--nibble1 <= 
```


#Discussion of first program instruction cycles.

#Answer to Prism Questions

#
#Yeh

First functionality-
Dr. Neebel checked my funtionality for part A in class on Friday, April 18th. 

Part two funtionality-
Captain Silva checked it at the end of class on 24 April.

Part two fpga functionality-
Captain Silva checked it in his office on 25 April.
