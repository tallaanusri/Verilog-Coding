# Day 1
---
1)
# Problem Statement
Build a circuit with no inputs and one output. That output should always drive 1 (or logic high).

# solution
```
module top_module( output one );
    assign one = 1'b1;

endmodule
```
# output:
<img width="480" height="170" alt="wavedrom" src="https://github.com/user-attachments/assets/eb2b3524-d846-4f6e-9af3-85fe0850db2f" />

2)
 # Problem Statement
 Build a circuit with no inputs and one output that outputs a constant 0
 
 # solution
```
module top_module(
    output zero
);// Module body starts after semicolon
assign zero = 1'b0;
endmodule
```
# output:
<img width="480" height="170" alt="wavedrom" src="https://github.com/user-attachments/assets/8e7682fa-75a9-41b5-9b28-17e1b3dacd1e" />
3)
The ports on a module also have a direction (usually input or output). An input port is driven by something from outside the module, while an output port drives something outside. When viewed from inside the module, an input port is a driver or source, while an output port is a sink.
The diagram below illustrates how each part of the circuit corresponds to each bit of Verilog code. The module and port declarations create the black portions of the circuit.
<img width="800" height="324" alt="Wire" src="https://github.com/user-attachments/assets/1b2f64cf-fe06-41f7-b919-7f79f0e70e62" />

 # Problem Statement
Your task is to create a wire (in green) by adding an assign statement to connect in to out. The parts outside the box are not your concern, but you should know that your circuit is tested by connecting signals from our test harness to the ports on your top_module.

# solution
```
module top_module( input in, output out );
	
	assign out = in;
	// Note that wires are directional, so "assign in = out" is not equivalent.
	
endmodule
```
# output:
<img width="480" height="230" alt="wavedrom (1)" src="https://github.com/user-attachments/assets/5701c818-5deb-462a-84b8-8cc24749ae13" />




