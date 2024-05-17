# 1.Simulation and Synthesis  of Logic Gates,Adders and Subtractors.
# AIM: To simulate and synthesis Logic Gates,Adders and Subtractor using Vivado 2023.2

# APPARATUS REQUIRED: Vivado 2023.2 

# PROCEDURE:
1. Open Vivado: Launch Xilinx Vivado software on your computer.

2. Create a New Project: Click on "Create Project" from the welcome page or navigate through "File" > "Project" > "New".

3. Project Settings: Follow the prompts to set up your project. Specify the project name, location, and select RTL project type.

4. Add Design Files: Add your Verilog design files to the project. You can do this by right-clicking on "Design Sources" in the Sources window, then selecting "Add Sources". Choose your Verilog files from the file browser.

5. Specify Simulation Settings: Go to "Simulation" > "Simulation Settings". Choose your simulation language (Verilog in this case) and simulation tool (Vivado Simulator).

6. Run Simulation: Go to "Flow" > "Run Simulation" > "Run Behavioral Simulation". This will launch the Vivado Simulator and compile your design for simulation.

7. Set Simulation Time: In the Vivado Simulator window, set the simulation time if it's not set automatically. This determines how long the simulation will run.

8. Run Simulation: Start the simulation by clicking on the "Run" button in the simulation window.

9. View Results: After the simulation completes, you can view waveforms, debug signals, and analyze the behavior of your design.

# Logic Diagram :

Logic Gates:
![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/ee17970c-3ac9-4603-881b-88e2825f41a4)


Half Adder:

![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/0e1ecb96-0c25-4556-832b-aeeedfdfe7b9)


Full adder:

![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/9bb3964c-438f-469d-a3de-c1cca6f323fb)


Half Subtractor:

![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/731470b7-eb4e-49f8-8bb7-2994052a7184)



Full Subtractor:

![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/d66f874b-c1f2-44b3-a035-7149b56430c1)



8 Bit Ripple Carry Adder

![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/7385a408-40a5-4203-8050-b72818622d79)


# HALF ADDER
VERILOG CODE:
```
module half_adder(Sum,carry,a,b);
input a,b;
output Sum,carry;
assign Sum = a ^ b;
assign carry = a & b;
endmodule 
``

OUTPUT:

![image](https://github.com/sakthivelM24/VLSI-LAB-EXP-1/assets/165649785/4b71581b-8890-460d-94c6-4367529a68a8)

![image](https://github.com/sakthivelM24/VLSI-LAB-EXP-1/assets/165649785/d38a4c87-436c-471d-bf73-609ffde281ef)

# FULL ADDER
VERILOG CODE:
```
module fulladder(sum,cout,a,b,c);
input a,b,c;
output sum,cout;
wire w1,w2,w3,w4,w5;
xor x1(w1,a,b);
xor x2(sum,w1,c);
and a1(w2,a,b);
and a2(w3,b,c);
and a3(w4,a,c);
or o1(w5,c1,c2);
or o2(cout,w5,c3);
endmodule 
```
OUTPUT:

![image](https://github.com/sakthivelM24/VLSI-LAB-EXP-1/assets/165649785/0ad6d833-3a2f-400e-a915-b5b652798395)
![image](https://github.com/sakthivelM24/VLSI-LAB-EXP-1/assets/165649785/00406313-e91b-4c4e-9c1a-3d4f3341aade)

# FULL SUBTRACTOR
VERILOG CODE:
```
module full_sub(borrow,diff,a,b,c);
output borrow,diff;
input a,b,c;
wire w1,w4,w5,w6;
xor (diff,a,b,c);
not n1(w1,a);
and a1(w4,w1,b);
and a2(w5,w1,c);
and a3(w6,b,c);
or o1(borrow,w4,w5,w6);
endmodule 
```
OUTPUT:
![image](https://github.com/sakthivelM24/VLSI-LAB-EXP-1/assets/165649785/7c8c6f7d-d64a-42c2-916d-1e321ce74495)
![image](https://github.com/sakthivelM24/VLSI-LAB-EXP-1/assets/165649785/28d59836-db26-4a31-8248-57ad630937a7)

# HALF SUBTRACTOR
VERILOG CODE:
```
module half_sub(Diff,Borrow,a,b);
input a,b;
output Diff,Borrow;
wire w1;
not(w1,a);
xor(Diff,a,b);
and(Borrow,b,w1);
endmodule
```
OUTPUT:
![image](https://github.com/sakthivelM24/VLSI-LAB-EXP-1/assets/165649785/258115c9-d822-4d38-8669-479134a859e7)
![image](https://github.com/sakthivelM24/VLSI-LAB-EXP-1/assets/165649785/62e014d2-b7b5-4991-b4c9-2a4ea489c049)

# LOGIC GATES
VERILOG CODE:
```
module logicgates(a,b,andgate,orgate,xorgate,nandgate,norgate,xnorgate,notgate);
input a,b;
output andgate,orgate,xorgate,nandgate,norgate,xnorgate,notgate;
and(andgate,a,b);
or(orgate,a,b);
xor(xorgate,a,b);
nand(nandgate,a,b);
nor(norgate,a,b);
xnor(xnorgate,a,b);
not(notgate,a);
endmodule
```
OUTPUT:
![image](https://github.com/sakthivelM24/VLSI-LAB-EXP-1/assets/165649785/4551aff2-8b4e-45ae-9303-3609713c2095)
![image](https://github.com/sakthivelM24/VLSI-LAB-EXP-1/assets/165649785/31292a47-f7d8-4c64-8be4-056edd998c7b)

# 4-BIT RIPPLE CARRY ADDER
VERILOG CODE:
```
module rippe_adder(S, Cout, X, Y,Cin);
input [3:0] X, Y;
input Cin;
output [3:0] S;
output Cout;
wire w1, w2, w3;
fulladder u1(S[0], w1,X[0], Y[0], Cin);
fulladder u2(S[1], w2,X[1], Y[1], w1);
fulladder u3(S[2], w3,X[2], Y[2], w2);
fulladder u4(S[3], Cout, X[3], Y[3], w3);
endmodule
module fulladder(S, Co, X, Y, Ci);
input X, Y, Ci;
output S, Co;
wire w1,w2,w3;
xor G1(w1, X, Y);
xor G2(S, w1, Ci);
and G3(w2, w1, Ci);
and G4(w3, X, Y);
or G5(Co, w2, w3);
endmodule
```

OUTPUT:
![image](https://github.com/sakthivelM24/VLSI-LAB-EXP-1/assets/165649785/e88cb55a-75a5-47f0-8790-bbca4facd989)
![image](https://github.com/sakthivelM24/VLSI-LAB-EXP-1/assets/165649785/20009d22-b109-4274-84a4-5fbc92c71fb0)

# 8-BIT RIPPLE CARRY ADDER
VERILOG CODE:
```1
module rippe_adder(S, Cout, X, Y,Cin);
input [7:0] X, Y;
// Two 4-bit inputsinput Cin;
output [7:0] S;
output Cout;
wire w1, w2, w3, w4, w5, w6, w7; 
// instantiating 8 1-bit full adders in Verilogfulladder u1(S[0], w1,X[0], Y[0], Cin);
fulladder u2(S[1], w2,X[1], Y[1], w1);
fulladder u3(S[2], w3,X[2], Y[2], w2);
fulladder u4(S[3], w4,X[3], Y[3], w3);
fulladder u5(S[4], w5,X[4], Y[4], w4);
fulladder u6(S[5], w6,X[5], Y[5], w5);
fulladder u7(S[6], w7,X[6], Y[6], w6);
fulladder u8(S[7], Cout,X[7], Y[7], w7);
endmodulemodule fulladder(S, Co, X, Y, Ci);
input X, Y, Ci;
output S, Co;
wire w1,w2,w3;
//Structural code for one bit full adderxor G1(w1, X, Y);
xor G2(S, w1, Ci);
and G3(w2, w1, Ci);
and G4(w3, X, Y);
or G5(Co, w2, w3);
endmodule
```
OUTPUT:
![image](https://github.com/sakthivelM24/VLSI-LAB-EXP-1/assets/165649785/b5a0f9a6-4c35-451c-b85f-3034ddfdeed8)
![image](https://github.com/sakthivelM24/VLSI-LAB-EXP-1/assets/165649785/4e00de5e-edc2-4002-8287-b349ee0dfcd4)

RESULT:
THUS THE VERILOG CODE FOR LOGIC GATES,ADDERS,SUBTRACTORS WAS SIMULATEDAND OUTPUT IS VERIFIED SUCCESSFULLY.



