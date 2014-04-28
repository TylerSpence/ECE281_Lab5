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

By analyzing the piece of PRISM code provided to us, I determined that the code functions by initially loading the value 8 into the accumulator then continually adding 1 and outputting the result to output port 3. This process continues until it adds 1 to F, resulting in a 0. It then goes past the jump because it is a jn and 0 is a positive number and enters an infinite loop at the end of the program.

#Discussion of first program instruction cycles.

Below is the first 70 ns of the waveform
![alt tag] (https://raw.githubusercontent.com/TylerSpence/ECE281_Lab5/master/initial%20screenshot.png)

The value on the op sel is loaded from the ir on a rising edge every three clock cycles as to be expected from the instuction cycle. On the third clock cycle, the opsel is 7 and the data is 8, resulting in the accumulator becoming 8. On the sixth clock cycle, the opsel is 6 and the operand is 1, resulting in 1 being added to 8. 

below is 70 ns through the jump of the waveform
![alt tag] (https://raw.githubusercontent.com/TylerSpence/ECE281_Lab5/master/jump%20screenshot.png)

At approx 97 ns (the last instruction took two clock cycles instead of one), the opsel becomes 4 and the address 3, outputting the accumulator to port 3. 

Though it cannot be seen on this picture, jumpsel becomes 1 at approx 125 ns, resulting in the program going back to the beggining and opsel being 6 at 167ns, starting the program over again.

#Discussion of second part prism program.

The second program works according to the following logic chart.
![alt tag] (https://raw.githubusercontent.com/TylerSpence/ECE281_Lab5/master/logic.jpg)

As seen in the comments for the actual code, it checks for the transition between the 9's and 10's by adding 6 and then having a 0 jump. This works because the output should be a 10 when the hex value is A. A plus 6 is 0, thus, when an A comes up, the value jumps to a different logic set to output a 0 instead of A. The same logic works for counting down, but by adding 1 because 0 minus 1 is F.

#Answer to Prism Questions

#debugging

When designing my prism program for part two it took me a little bit of time and a few different tactics to figure out how to prevent the number from counting up to f instead of 9. 

#functionality checks

First functionality-
Dr. Neebel checked my funtionality for part A in class on Friday, April 18th. 

Part two funtionality-
Captain Silva checked it at the end of class on 24 April.

Part two fpga functionality-
Captain Silva checked it in his office on 25 April. At this time I also told captain Silva that my commit hisotry isn't good for the second PRISM because I finished making it in one sitting and he said that was ok. 
