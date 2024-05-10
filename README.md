SIMULATION AND IMPLEMENTATION OF  COMBINATIONAL LOGIC CIRCUITS

AIM: 
 To simulate and synthesis ENCODER, DECODER, MULTIPLEXER, DEMULTIPLEXER, MAGNITUDE COMPARATOR using vivado 2023.2.

APPARATUS REQUIRED:
vivado 2023.2.

**LOGIC DIAGRAM**

ENCODER

![image](https://github.com/navaneethans/VLSI-LAB-EXP-2/assets/6987778/3cd1f95e-7531-4cad-9154-fdd397ac439e)


DECODER

![image](https://github.com/navaneethans/VLSI-LAB-EXP-2/assets/6987778/45a5e6cf-bbe0-4fd5-ac84-e5ad4477483b)


MULTIPLEXER

![image](https://github.com/navaneethans/VLSI-LAB-EXP-2/assets/6987778/427f75b2-8e67-44b9-ac45-a66651787436)


DEMULTIPLEXER

![image](https://github.com/navaneethans/VLSI-LAB-EXP-2/assets/6987778/1c45a7fc-08ac-4f76-87f2-c084e7150557)


MAGNITUDE COMPARATOR

![image](https://github.com/navaneethans/VLSI-LAB-EXP-2/assets/6987778/b2fe7a05-6bf7-4dcb-8f5d-28abbf7ea8c2)


  
PROCEDURE:
1. Open Vivado: Launch Xilinx Vivado software on your computer.

2. Create a New Project: Click on "Create Project" from the welcome page or navigate through "File" > "Project" > "New".

3. Project Settings: Follow the prompts to set up your project. Specify the project name, location, and select RTL project type.

4. Add Design Files: Add your Verilog design files to the project. You can do this by right-clicking on "Design Sources" in the Sources window, then selecting "Add Sources". Choose your Verilog files from the file browser.

5. Specify Simulation Settings: Go to "Simulation" > "Simulation Settings". Choose your simulation language (Verilog in this case) and simulation tool (Vivado Simulator).

6. Run Simulation: Go to "Flow" > "Run Simulation" > "Run Behavioral Simulation". This will launch the Vivado Simulator and compile your design for simulation.

7. Set Simulation Time: In the Vivado Simulator window, set the simulation time if it's not set automatically. This determines how long the simulation will run.

8. Run Simulation: Start the simulation by clicking on the "Run" button in the simulation window.

9. View Results: After the simulation completes, you can view waveforms, debug signals, and analyze the behavior of your design

VERILOG CODE


Encoder 8to3:
~~~
module encoder_8_to_3(a0,a1,a2,d0,d1,d2,d3,d4,d5,d6,d7);input d0,d1,d2,d3,d4,d5,d6,d7;
output a0,a1,a2;
or g1(a0,d1,d3,d5,d7);
or g2(a1,d2,d3,d6,d7);
or g3(a2,d4,d5,d6,d7);
endmodule
~~~
OUTPUT:
![WhatsApp Image 2024-04-23 at 6 50 08 PM](https://github.com/Kirthana-2004/VLSI-LAB-EXP-2/assets/144320880/833b6baa-41b0-44fc-8bc7-035b6e19b9c0)

![WhatsApp Image 2024-04-23 at 6 50 08 PM (1)](https://github.com/Kirthana-2004/VLSI-LAB-EXP-2/assets/144320880/4bb7c3e1-5dc6-44be-81fb-5a48f96806f0)

Decoder 3to8:

~~~
module decoder_3to8(
    input [2:0] a,
    output [7:0] d );
assign d[0]=(~a[2])&(~a[1])&(~a[0]);
assign d[1]=(~a[2])&(~a[1])&(a[0]);
assign d[2]=(~a[2])&(a[1])&(~a[0]);
assign d[3]=(~a[2])&(a[1])&(a[0]);
assign d[4]=(a[2])&(~a[1])&(~a[0]);
assign d[5]=(a[2])&(~a[1])&(a[0]);
assign d[6]=(a[2])&(a[1])&(~a[0]);
assign d[7]=(a[2])&(a[1])&(a[0]);
endmodule
~~~
OUTPUT:
![image](https://github.com/Kirthana-2004/VLSI-LAB-EXP-2/assets/144320880/47c9326c-3119-4d4b-b67d-98718b2805fe)
![image](https://github.com/Kirthana-2004/VLSI-LAB-EXP-2/assets/144320880/a6a2fbd0-0af9-4766-8003-c065071727f7)

Multiplexer 8to1:
~~~
module mux_8to1(in,sel,out);
  input[7:0]in;
  output reg out;
  always @(*)
    begin
      case(sel)
        3'b000: out = in[0];
        3'b001: out = in[1];
        3'b010: out = in[2];
        3'b011: out = in[3];
        3'b100: out = in[4];
        3'b101: out = in[5];
        3'b110: out = in[6];
        3'b111: out = in[7];
        default: out = 1'bx;
      endcase
    end
endmodule
~~~
OUTPUT:
![WhatsApp Image 2024-04-23 at 6 50 08 PM (2)](https://github.com/Kirthana-2004/VLSI-LAB-EXP-2/assets/144320880/3bfc3d5d-5daf-41cf-9950-7171fe8d0cff)

![WhatsApp Image 2024-04-23 at 6 50 09 PM](https://github.com/Kirthana-2004/VLSI-LAB-EXP-2/assets/144320880/74df8f11-9703-4b33-bd37-ba9bcbaa7751)

Demultiplexer 1to8:

~~~
module demux_1_8(y,s,a);
output reg [7:0]y;
input [2:0]s;
input a;

always @(*)
begin 
y=0;
case(s)
3'd0: y[0]=a;
3'd1: y[1]=a;
3'd2: y[2]=a;
3'd3: y[3]=a;
3'd4: y[4]=a;
3'd5: y[5]=a;
3'd6: y[6]=a;
3'd7: y[7]=a;
endcase
end
endmodule
~~~
OUTPUT:
![WhatsApp Image 2024-04-23 at 6 50 09 PM (1)](https://github.com/Kirthana-2004/VLSI-LAB-EXP-2/assets/144320880/bef98284-cdbd-4c09-bb8d-61ba5396a467)
![WhatsApp Image 2024-04-23 at 6 50 09 PM (2)](https://github.com/Kirthana-2004/VLSI-LAB-EXP-2/assets/144320880/e751b980-b1a3-43f0-ac4a-6b8ed49f8e21)

Magnitudecomparator:
~~~
module comparator(a,b,eq,lt,gt);
input [3:0] a,b;
output reg eq,lt,gt;
always @(a,b)
begin
 if (a==b)
 begin
  eq = 1'b1;
  lt = 1'b0;
  gt = 1'b0;
 end
 else if (a>b)
begin
  eq = 1'b0;
  lt = 1'b0;
  gt = 1'b1;
 end
 else
 begin
  eq = 1'b0;
  lt = 1'b1;
  gt = 1'b0;
 end
end 
endmodule
~~~
OUTPUT:
![WhatsApp Image 2024-04-23 at 6 50 10 PM (1)](https://github.com/Kirthana-2004/VLSI-LAB-EXP-2/assets/144320880/49ceb93e-8860-4596-a145-16bf3987cc1c)
![WhatsApp Image 2024-04-23 at 6 50 10 PM](https://github.com/Kirthana-2004/VLSI-LAB-EXP-2/assets/144320880/623e02c5-2f9f-4c9f-84cc-7ed5aa80054d)

RESULT:
Thus the simulation and synthesis of ENCODER, DECODER, MULTIPLEXER, DEMULTIPLEXER, MAGNITUDE COMPARATOR using vivado has been successfully executed and verified. 


