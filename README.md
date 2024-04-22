SIMULATION AND IMPLEMENTATION OF COMBINATIONAL LOGIC CIRCUITS

AIM: To simulate and synthesis ENCODER, DECODER, MULTIPLEXER, DEMULTIPLEXER, MAGNITUDE COMPARATOR using Vivado 2023.1.

APPARATUS REQUIRED: Vivado 2023.1

LOGIC DIAGRAM

ENCODER

![image](https://github.com/harivanth2021/VLSI-LAB-EXP-2/assets/165633628/693e95f5-87f1-47ed-938f-edfee0fcb3b0)


DECODER

![image](https://github.com/harivanth2021/VLSI-LAB-EXP-2/assets/165633628/b80b33d5-6232-421e-844a-f284d7cbe87d)


MULTIPLEXER

![image](https://github.com/harivanth2021/VLSI-LAB-EXP-2/assets/165633628/d7e1bda0-0912-4f6a-88a8-b99fd5ad2a4a)


DEMULTIPLEXER

![image](https://github.com/harivanth2021/VLSI-LAB-EXP-2/assets/165633628/b6c61d35-62eb-4aa8-9320-605c7297b253)


MAGNITUDE COMPARATOR

![image](https://github.com/harivanth2021/VLSI-LAB-EXP-2/assets/165633628/d3657a6f-7567-44da-9132-0540d6e5d222)


PROCEDURE:

Open Vivado: Launch Xilinx Vivado software on your computer.

Create a New Project: Click on "Create Project" from the welcome page or navigate through "File" > "Project" > "New".

Project Settings: Follow the prompts to set up your project. Specify the project name, location, and select RTL project type.

Add Design Files: Add your Verilog design files to the project. You can do this by right-clicking on "Design Sources" in the Sources window, then selecting "Add Sources". Choose your Verilog files from the file browser.

Specify Simulation Settings: Go to "Simulation" > "Simulation Settings". Choose your simulation language (Verilog in this case) and simulation tool (Vivado Simulator).

Run Simulation: Go to "Flow" > "Run Simulation" > "Run Behavioral Simulation". This will launch the Vivado Simulator and compile your design for simulation.

Set Simulation Time: In the Vivado Simulator window, set the simulation time if it's not set automatically. This determines how long the simulation will run.

Run Simulation: Start the simulation by clicking on the "Run" button in the simulation window.

View Results: After the simulation completes, you can view waveforms, debug signals, and analyze the behavior of your design.

VERILOG CODE:

ENCODER:

module encoder(d,a,b,c);
input [7:0]d;
output a,b,c;
or(a,d[4],d[5],d[6],d[7]);
or(b,d[2],d[3],d[6],d[7]);
or(c,d[1],d[3],d[5],d[7]);
endmodule
DECODER:

module decoder_8(a,b,c,y);
input a,b,c; 
output[7:0]y; 
and gl(y[0],(~a),(~b),(~c)); 
and g2(y[1],(~a),(~b),(c)); 
and g3(y[2],(~a),(b),(~c));
and g4(y[3],(~a),(b),(c));
and g5(y[4],(a),(~b),(~c));
and g6(y[5],(a), (~b), (c));
and g7(y[6], (a), (b), (~c)); 
and g8(y[7], (a), (b), (c));
endmodule
MULTIPLEXER:

module mux(a,b,c,d,s0,s1,y);
input a,b,c,d,s0,s1;
output y;
assign y=s1 ?(s0?d:c):(s0?b:a);
endmodule
DEMULTIPLEXER:

module demux(in,s0,s1,s2,d0,d1,d2,d3,d4,d5,d6,d7);
input in,s0,s1,s2;
output d0,d1,d2,d3,d4,d5,d6,d7;
assign d0=(in & ~s2 & ~s1 &~s0),
d1=(in & ~s2 & ~s1 &s0),
d2=(in & ~s2 & s1 &~s0),
d3=(in & ~s2 & s1 &s0),
d4=(in & s2 & ~s1 &~s0),
d5=(in & s2 & ~s1 &s0),
d6=(in & s2 & s1 &~s0),
d7=(in & s2 & s1 &s0);
endmodule
MAGNITUDE COMPARATOR:

module magcomp(a,b,l,g,e);
input [3:0]a,b;
output reg l,g,e;
always @(*)
begin
if(a>b)
begin
     l=1'b0;
     g=1'b1;
     e=1'b0;
end
else if(a<b)
begin
     l=1'b1;
     g=1'b0;
     e=1'b0;
end
else
begin
     l=1'b0;
     g=1'b0;
     e=1'b1;
end
end
endmodule
OUTPUT WAVEFORM:

ENCODER:

![image](https://github.com/harivanth2021/VLSI-LAB-EXP-2/assets/165633628/2f5f7310-58f8-465b-943b-2f5ce51c43a0)


DECODER:

![image](https://github.com/harivanth2021/VLSI-LAB-EXP-2/assets/165633628/8700b168-96e5-4bc1-b309-bdb6ea962148)


MULTIPLEXER:

![image](https://github.com/harivanth2021/VLSI-LAB-EXP-2/assets/165633628/6633332d-f5cd-4e01-9f46-1d0eaeb815af)


DEMULTIPLEXER:

![image](https://github.com/harivanth2021/VLSI-LAB-EXP-2/assets/165633628/9b199690-2bef-4071-9934-6e92fe3e3dba)


MAGNITUDE COMPARATOR:

![image](https://github.com/harivanth2021/VLSI-LAB-EXP-2/assets/165633628/794a2e23-b7cc-4471-b624-7ed592abd585)


RESULT:

Hence ENCODER, DECODER, MULTIPLEXER, DEMULTIPLEXER, MAGNITUDE COMPARATOR are simulated and synthesised using Vivado 2023.1.
