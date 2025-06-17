![image](https://github.com/user-attachments/assets/efed3c54-fb47-43ed-addb-d402147d4800)# Design-of-8-1-Mux-using-Verilog-HDL-Functional-Verification-using-UVM-and-Generate-GDS-II-layout

A multiplexer (MUX) is a fundamental building block in digital electronics used to select one of 
many input signals and forward the selected input to a single output line. This functionality makes it 
an essential component in data routing, control systems, communication hardware, and processor 
design. In this project, an 8:1 multiplexer is designed and implemented using Verilog HDL, a 
hardware description language widely used in VLSI design and FPGA development. 
An 8:1 MUX has eight input lines, three selection inputs, and one output. The selection lines 
determine which input is routed to the output at any given time. The efficient design of such 
multiplexers is crucial for developing high-speed and low-latency digital systems. The project 
emphasizes structural, behavioural, and RTL-level modelling approaches to demonstrate modularity, 
clarity, and synthesis compatibility in Verilog.
# Block Diagram  and Truth Table

![image](https://github.com/user-attachments/assets/25d31889-7f22-47ba-a0f9-8743142015bb)
![image](https://github.com/user-attachments/assets/e6b8603d-d5c9-4b20-a243-ddc22698a664)

# UVM Testbench Architecture
![image](https://github.com/user-attachments/assets/039d03ee-728a-4207-b5ee-54084e17f781)

# Verilog Design Methodology 

This project uses RTL modelling in Verilog HDL to describe the behaviour of the 8:1 MUX. RTL 
(Register Transfer Level) allows designers to focus on data flow and control logic rather than low
level gates. 
Verilog RTL Code 

module mux8to1 ( 
input  [7:0] in,         // 8-bit input vector (I0 to I7) 
input  [2:0] sel,        // 3-bit select input 
output reg out           // Output 
); 
always @(*) begin 
case (sel) 
3'b000: out = in[0]; 
3'b001: out = in[1]; 
3'b010: out = in[2]; 
3'b011: out = in[3]; 
3'b100: out = in[4];
3'b101: out = in[5]; 
3'b110: out = in[6]; 
3'b111: out = in[7]; 
default: out = 1'b0; 
endcase 
end 
endmodule 

# Testbench Code 
`timescale 1ns / 1ps 
module mux8to1_tb; 
// Testbench signals 
reg [7:0] d; 
reg [2:0] sel; 
wire y; 
// Instantiate the MUX 
mux8to1 uut ( 
.d(d), 
.sel(sel), 
.y(y) 
); 
initial begin 
$display("Time\t sel \t d \t\t y"); 
$monitor("%0t\t %b \t %b \t %b", $time, sel, d, y); 
// Test 1: All data 0 
d = 8'b00000000; 
sel = 3'b000; 
#10; 
// Test 2: Set only one bit in data, check selection 
d = 8'b00000001; sel = 3'b000; #10; 
d = 8'b00000010; sel = 3'b001; #10; 
d = 8'b00000100; sel = 3'b010; #10; 
d = 8'b00001000; sel = 3'b011; #10; 
d = 8'b00010000; sel = 3'b100; #10; 
d = 8'b00100000; sel = 3'b101; #10; 
d = 8'b01000000; sel = 3'b110; #10; 
d = 8'b10000000; sel = 3'b111; #10; 
// Test 3: All data 1 
d = 8'b11111111; 
sel = 3'b010; 
#10; 
// Finish simulation 
$finish; 
end 
endmodule

# Simulation  

![image](https://github.com/user-attachments/assets/f5dc958f-3d2a-4202-9a1f-717c2c3468b9)

# Evaluation Criteria for Block-Level Verification in UVM

EDA LInk: https://www.edaplayground.com/x/GSAD 

# Generate GDS using OpenROAD Tool
Layout of the Design
![image](https://github.com/user-attachments/assets/d63ee678-fb12-4d84-861c-f62c3d2000d2)

# Power Measurement
![image](https://github.com/user-attachments/assets/d4c80286-7bf1-44b2-bb53-1f93b30634c8)

# Area Measurement and Timing Information
![image](https://github.com/user-attachments/assets/8bae2fdf-d29d-4c16-a452-4a4e34ed9384)
![image](https://github.com/user-attachments/assets/1f05e542-4af8-4b10-9160-82420c2e0d66)

# Generated GDS 
![image](https://github.com/user-attachments/assets/d0102df7-b203-449e-8ddf-f16f9c82abee)





