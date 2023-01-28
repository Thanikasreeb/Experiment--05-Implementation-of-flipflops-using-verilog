# Experiment--05-Implementation-of-flipflops-using-verilog

### AIM: 

To implement all the flipflops using verilog and validating their functionality using their functional tables

### HARDWARE REQUIRED: 

PC, Cyclone II , USB flasher

### SOFTWARE REQUIRED: 

 Quartus prime

### THEORY:

SR Flip-Flop

SR flip-flop operates with only positive clock transitions or negative clock transitions. Whereas, SR latch operates with enable signal. The circuit diagram of SR flip-flop is shown in the following figure.

![](/exp5.png)

 
This circuit has two inputs S & R and two outputs Qtt & Qtt’. The operation of SR flipflop is similar to SR Latch. But, this flip-flop affects the outputs only when positive transition of the clock signal is applied instead of active enable.
The following table shows the state table of SR flip-flop.






























































































































































































































































































































































































55 ys






































































































































































































































































o![](/implll.png)

Here, Qtt & Qt+1t+1 are present state & next state respectively. So, SR flip-flop can be used for one of these three functions such as Hold, Reset & Set based on the input conditions, when positive transition of clock signal is applied. The following table shows the characteristic table of SR flip-flop.
Present Inputs	Present State	Next State


![](/167908180-5fc9d589-1cb5-41f5-b2c8-927e04f5f387.png)

By using three variable K-Map, we can get the simplified expression for next state, Qt+1t+1. The three variable K-Map for next state, Qt+1t+1 is shown in the following figure.


![](/167908214-25b30a54-db20-4bcb-9385-5f93a1982a09.png)

The maximum possible groupings of adjacent ones are already shown in the figure. Therefore, the simplified expression for next state Qt+1t+1 is
Q(t+1)=S+R′Q(t)Q(t+1)=S+R′Q(t)


### D Flip-Flop :
![](/impl1.png)

D flip-flop operates with only positive clock transitions or negative clock transitions. Whereas, D latch operates with enable signal. That means, the output of D flip-flop is insensitive to the changes in the input, D except for active transition of the clock signal. The circuit d-1iagram of D flip-flop is shown in the following figure.
 
This circuit has single input D and two outputs Qtt & Qtt’. The operation of D flip-flop is similar to D Latch. But, this flip-flop affects the outputs only when positive transition of the clock signal is applied instead of active enable.

![](/impl2.png)

The following table shows the state table of D flip-flop.

![](/impl3.png)

Therefore, D flip-flop always Hold the information, which is available on data input, D of earlier positive transition of clock signal. From the above state table, we can directly write the next state equation as
Qt+1t+1 = D

![](/imp4.png)

Next state of D flip-flop is always equal to data input, D for every positive transition of the clock signal. Hence, D flip-flops can be used in registers, shift registers and some of the counters.


### JK Flip-Flop:

JK flip-flop is the modified version of SR flip-flop. It operates with only positive clock transitions or negative clock transitions. The circuit diagram of JK flip-flop is shown in the following figure.

![](/impl5.png)

This circuit has two inputs J & K and two outputs Qtt & Qtt’. The operation of JK flip-flop is similar to SR flip-flop. Here, we considered the inputs of SR flip-flop as S = J Qtt’ and R = KQtt in order to utilize the modified SR flip-flop for 4 combinations of inputs.
The following table shows the state table of JK flip-flop.

![](/impl6.png)

Here, Qtt & Qt+1t+1 are present state & next state respectively. So, JK flip-flop can be used for one of these four functions such as Hold, Reset, Set & Complement of present state based on the input conditions, when positive transition of clock signal is applied. The following table shows the characteristic table of JK flip-flop.
Present Inputs	Present State	Next State
  
  ![](/impl7.png)

By using three variable K-Map, we can get the simplified expression for next state, Qt+1t+1. Three variable K-Map for next state, Qt+1t+1 is shown in the following figure.

![](/impl8.png)

The maximum possible groupings of adjacent ones are already shown in the figure. Therefore, the simplified expression for next state Qt+1t+1 is
Q(t+1)=JQ(t)′+K′Q(t)Q(t+1)=JQ(t)′+K′Q(t)


### T Flip-Flop:

T flip-flop is the simplified version of JK flip-flop. It is obtained by connecting the same input ‘T’ to both inputs of JK flip-flop. It operates with only positive clock transitions or negative clock transitions. The circuit diagram of T flip-flop is shown in the following figure.

![](/impl9.png)

This circuit has single input T and two outputs Qtt & Qtt’. The operation of T flip-flop is same as that of JK flip-flop. Here, we considered the inputs of JK flip-flop as J = T and K = T in order to utilize the modified JK flip-flop for 2 combinations of inputs. So, we eliminated the other two combinations of J & K, for which those two values are complement to each other in T flip-flop.
The following table shows the state table of T flip-flop.


Here, Qtt & Qt+1t+1 are present state & next state respectively. So, T flip-flop can be used for one of these two functions such as Hold, & Complement of present state based on the input conditions, when positive transition of clock signal is applied. The following table shows the characteristic table of T flip-flop.
Inputs	Present State	Next State
 
 ![](/exp9.png)

From the above characteristic table, we can directly write the next state equation as
Q(t+1)=T′Q(t)+TQ(t)′
⇒Q(t+1)=T⊕Q(t)

### Procedure :

Step 1:

Open Quartus II and select new project and choose the file location.

Step 2:

Module Declaration. Module should have the file name.

Step 3:

Use assign declaration and wire to define the functionality of logic circuits.

Step 4:

At the end give endmodule.

Step 5:

Run the program and choose RTL viewer to get RTL realization.

step 6:

Do the timing diagram

### PROGRAM  :
```
Program for flipflops  and verify its truth table in quartus using Verilog programming.
Developed by: Thanika sree b
RegisterNumber: 22008978

module SR(S,R,clk,Q,Qbar);
input S,R,clk;
output Q,Qbar;
wire X,Y;
nand (X,S,clk);
nand (Y,R,clk);
nand (Q,X,Qbar);
nand (Qbar,Y,Q);
endmodule

D FLIPFLOP:

module DF(D,clk,Q,Qbar);
input D,clk;
output Q,Qbar;
assign Dbar=~D;
wire X,Y;
nand (X,D,clk);
nand (Y,Dbar,clk);
nand (Q,X,Qbar);
nand (Qbar,Y,Q);
endmodule

JK FLIPFLOP:

module JK(J,K,clk,Q,Qbar);
input J,K,clk;
output Q,Qbar;
wire X,Y;
nand (X,J,clk,Qbar);
nand (Y,K,clk,Q);
nand (Q,X,Qbar);
nand (Qbar,Y,Q);
endmodule

T FLIPFLOP:

module TF(T,clk,Q,Qbar);
input T,clk;
output Q,Qbar;
wire S,R;
nand (S,T,clk,Qbar);
nand (R,T,clk,Q);
nand (Q,S,Qbar);
nand (Qbar,R,Q);
endmodule
```
### RTL LOGIC FOR FLIPFLOPS 

SR FLIPFLOP:

![](/rtl1.png)

D FLIPFLOP:

![](/rtl2.png)

JK FLIPFLOP:

![](/rtl3.png)

T FLIPFLOP:

![](/rtl4.png)

TIMING DIGRAMS FOR FLIP FLOPS:

SR FLIPFLOP:

![](/td11.png)

D FLIPFLOP:

![](/td22.png)

JK FLIPFLOP:

![](/td33.png)

T FLIPFLOP:

![](/td44.png)

### RESULTS :

Thus, the program for flipflops is implemented and its functional table is successfully verified in quartus using Verilog programming.
