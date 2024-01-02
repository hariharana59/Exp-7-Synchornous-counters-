## Name: Hariharan.A
## Register number: 23012392

# Exp-6-Synchornous-counters - up counter and down counter 

## AIM: 
To implement 3 bit up and down counters and validate  functionality.

## HARDWARE REQUIRED:  
– PC, Cyclone II , USB flasher

## SOFTWARE REQUIRED:   
Quartus prime

## THEORY 

### UP COUNTER 
The counter is a digital sequential circuit and here it is a 3 bit counter, which simply means it can count from 0 to 15 and vice versa based upon the direction of counting (up/down). 

The counter (“count“) value will be evaluated at every positive (rising) edge of the clock (“clk“) cycle.
The Counter will be set to Zero when “reset” input is at logic high.
The counter will be loaded with “data” input when the “load” signal is at logic high. Otherwise, it will count up or down.
The counter will count up when the “up_down” signal is logic high, otherwise count down

Since we know that binary count sequences follow a pattern of octave (factor of 2) frequency division, and that J-K flip-flop multivibrators set up for the “toggle” mode are capable of performing this type of frequency division, we can envision a circuit made up of several J-K flip-flops, cascaded to produce four bits of output.
The main problem facing us is to determine how to connect these flip-flops together so that they toggle at the right times to produce the proper binary sequence.
Examine the following binary count sequence, paying attention to patterns preceding the “toggling” of a bit between 0 and 1:
Binary count sequence, paying attention to patterns preceding the “toggling” of a bit between 0 and 1.

Note that each bit in this four-bit sequence toggles when the bit before it (the bit having a lesser significance, or place-weight), toggles in a particular direction: from 1 to 0.

Starting with four J-K flip-flops connected in such a way to always be in the “toggle” mode, we need to determine how to connect the clock inputs in such a way so that each succeeding bit toggles when the bit before it transitions from 1 to 0.

The Q outputs of each flip-flop will serve as the respective binary bits of the final, three-bit count:


![image](https://github.com/Raji1009/Exp-7-Synchornous-counters-/assets/89059861/e8c6b2b5-7ae2-4a96-8e1b-f5577cc431ec)




### DOWN COUNTER 

As well as counting “up” from zero and increasing or incrementing to some preset value, it is sometimes necessary to count “down” from a predetermined value to zero allowing us to produce an output that activates when the zero count or some other pre-set value is reached.

This type of counter is normally referred to as a Down Counter, (CTD). In a binary or BCD down counter, the count decreases by one for each external clock pulse from some preset value. Special dual purpose IC’s such as the TTL 74LS193 or CMOS CD4510 are 3-bit binary Up or Down counters which have an additional input pin to select either the up or down count mode.

![image](https://github.com/Raji1009/Exp-7-Synchornous-counters-/assets/89059861/b550d483-2152-4ee8-87bc-cf6cdb31f565)



3-bit Count Down Counter

### Procedure
1.Create a new project in Quartus II software.

2.Name the project as uc for upcounter and dc for downcounter.

3.Create a new Verilog HDL file in the project file.

4.Name the module as dc and uc for downcounter and upcounter.

5.Within the module declare input and output variables.

6.Complete the program.

7.End the module.


## PROGRAM :

### UP COUNTER :
```
module uc(clk, A);
input clk;
output reg [2:0]A;
always @(posedge clk)
begin
A[2]=(((A[0])&(A[1]))^A[2]);
A[1]=(A[0])^A[1];
A[0]=A[0]^1;
end
endmodule
```

### DOWN COUNTER :
```
module dc(clk,A);
input clk;
output reg [2:0]A;
always @(posedge clk)
begin
A[2]=(((~A[0])&(~A[1]))^A[2]);
A[1]=(~A[0])^A[1];
A[0]=1^A[0];
end
endmodule
```

# RTL Realisation:

### UP COUNTER:

![image](https://github.com/hariharana59/Exp-7-Synchornous-counters-/assets/144980130/9a0b6183-3576-4167-94aa-4877b9a4298d)


### DOWN COUNTER:
![image](https://github.com/hariharana59/Exp-7-Synchornous-counters-/assets/144980130/f04dc05a-f686-4eae-a723-bb9a6003b37f)


### TIMING DIGRAMS FOR COUNTER :

### UP COUNTER :
![image](https://github.com/hariharana59/Exp-7-Synchornous-counters-/assets/144980130/fa278c03-ca14-4689-8419-1e1ac41513c0)

### DOWN COUNTER :
![image](https://github.com/hariharana59/Exp-7-Synchornous-counters-/assets/144980130/3b50b372-8d79-44e9-aa75-26b74911bd74)



## TRUTH TABLE :

### UP COUNTER :
![image](https://github.com/hariharana59/Exp-7-Synchornous-counters-/assets/144980130/d33d2a08-101e-44b3-a0be-332108c01685)

### DOWN COUNTER :
![image](https://github.com/hariharana59/Exp-7-Synchornous-counters-/assets/144980130/b15e1cd5-2162-44a4-b6e3-dd215e3d4694)


### RESULTS 
By this we have verified the truth table of 3-bit up-counter using verilog.
