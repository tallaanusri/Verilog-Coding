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

3)
The diagram below illustrates how each part of the circuit corresponds to each bit of Verilog code. From outside the module, there are three input ports and four output ports.

When you have multiple assign statements, the order in which they appear in the code does not matter. Unlike a programming language, assign statements ("continuous assignments") describe connections between things, not the action of copying a value from one thing to another.
<img width="815" height="281" alt="Wire4" src="https://github.com/user-attachments/assets/30cef5d5-f6a1-497f-b8e7-96056b57881d" />

 # Problem Statement
 Create a module with 3 inputs and 4 outputs that behaves like wires that makes these connections:
a -> w
b -> x
b -> y
c -> z

# solution
```
module top_module( 
    input a,b,c,
    output w,x,y,z );
    assign w=a;
    assign x=b;
    assign y=b;
    assign z=c;
// If we're certain about the width of each signal, using 
	// the concatenation operator is equivalent and shorter:
	// assign {w,x,y,z} = {a,b,b,c};<img width="420" height="470" alt="wavedrom (2)" src="https://github.com/user-attachments/assets/5bd5867a-a626-44f9-b563-1dfa375d3965" />

endmodule
```
# output:
<img width="420" height="470" alt="wavedrom (2)" src="https://github.com/user-attachments/assets/0c13634b-b86f-4784-9f77-67188c8aad99" />

4)
 # Problem Statement
Create a module that implements a NOT gate.

This circuit is similar to wire, but with a slight difference. When making the connection from the wire in to the wire out we're going to implement an inverter (or "NOT-gate") instead of a plain wire.

Use an assign statement. The assign statement will continuously drive the inverse of in onto wire out.
<img width="575" height="281" alt="Notgate" src="https://github.com/user-attachments/assets/3c20a29e-4d8a-43fa-b10c-f76ea7358f5e" />

# solution
```
module top_module( input in, output out );
assign out = ~in;
endmodule

```
# output:
<img width="880" height="230" alt="wavedrom (3)" src="https://github.com/user-attachments/assets/98d2a0b4-7b17-4d7a-9482-071c628e9269" />

5)
# Problem Statement
Create a module that implements an AND gate.
This circuit now has three wires (a, b, and out). Wires a and b already have values driven onto them by the input ports. But wire out currently is not driven by anything. Write an assign statement that drives out with the AND of signals a and b.
<img width="586" height="281" alt="Andgate" src="https://github.com/user-attachments/assets/020c37de-eddb-4047-a716-05d09a68b3d4" />

# solution
```
module top_module( 
    input a, 
    input b, 
    output out );
assign out=a&b;
endmodule

```
# output:
<img width="480" height="260" alt="wavedrom (4)" src="https://github.com/user-attachments/assets/5bb6a880-c3d3-434d-8c18-406c7b49410e" />

6)
# Problem Statement
Create a module that implements a NOR gate. A NOR gate is an OR gate with its output inverted. A NOR function needs two operators when written in Verilog.
<img width="586" height="281" alt="Norgate" src="https://github.com/user-attachments/assets/8e2bca70-94c4-4ee0-b6be-b1ef29f9c375" />

# solution
```
module top_module( 
    input a, 
    input b, 
    output out );
    assign out=~(a|b);
endmodule
```
# output:
<img width="480" height="260" alt="wavedrom (5)" src="https://github.com/user-attachments/assets/f7a9a37a-d6dd-4243-91cc-b9d5737b628e" />

7)
# Problem Statement
Create a module that implements an XNOR gate.
<img width="586" height="281" alt="Xnorgate" src="https://github.com/user-attachments/assets/afb3fa16-23eb-4de3-837b-08fbb171fc44" />

# solution
```
module top_module( 
    input a, 
    input b, 
    output out );
    assign out=~(a^b);
endmodule
```
# output:
<img width="480" height="260" alt="wavedrom (6)" src="https://github.com/user-attachments/assets/cd9ec652-ce46-4e5c-afe9-91029bed432b" />

8)
# Problem Statement
mplement the following circuit. Create two intermediate wires (named anything you want) to connect the AND and OR gates together. Note that the wire that feeds the NOT gate is really wire out, so you do not necessarily need to declare a third wire here. Notice how wires are driven by exactly one source (output of a gate), but can feed multiple inputs.

If you're following the circuit structure in the diagram, you should end up with four assign statements, as there are four signals that need a value assigned.
(Yes, it is possible to create a circuit with the same functionality without the intermediate wires.)
<img width="620" height="264" alt="Wiredecl2" src="https://github.com/user-attachments/assets/9e2b4c22-bb9b-4b40-9843-9685bea44dfc" />

# solution
```
module top_module(
    input a,
    input b,
    input c,
    input d,
    output out,
    output out_n   ); 
    wire w1,w2,w3;
    assign w1=a&b;
    assign w2=c&d;
    assign w3=w1|w2;
    assign out=w3;
    assign out_n=~w3;

//OR The other way:-
wire w1, w2;		// Declare two wires (named w1 and w2)
assign w1 = a&b;	// First AND gate
assign w2 = c&d;	// Second AND gate
assign out = w1|w2;	// OR gate: Feeds both 'out' and the NOT gate
assign out_n = ~out;	// NOT gate
 //
	
endmodule
```
# output:
<img width="500" height="380" alt="wavedrom (7)" src="https://github.com/user-attachments/assets/bfc95ed2-9df5-4cf0-ba72-dfd1f6a42bd2" />

9)
# Problem Statement
Create a module with the same functionality as the 7458 chip. It has 10 inputs and 2 outputs. You may choose to use an assign statement to drive each of the output wires, or you may choose to declare (four) wires for use as intermediate signals, where each internal wire is driven by the output of one of the AND gates. For extra practice, try it both ways.

<img width="723" height="428" alt="7458" src="https://github.com/user-attachments/assets/dcbf9dab-97c0-4707-8f53-601741058960" />

# solution
```
module top_module ( 
    input p1a, p1b, p1c, p1d, p1e, p1f,
    output p1y,
    input p2a, p2b, p2c, p2d,
    output p2y );
    assign p2y=(p2c & p2d)| (p2a & p2b);
    assign p1y=(p1a & p1c & p1b)| (p1d & p1e & p1f);
// OR The other way:-

wire w1,w2,w3,w4;
    assign w1=(p2c & p2d);
    assign w2=(p2a & p2b);
    assign w3=(p1a & p1c & p1b);
    assign w4= (p1d & p1e & p1f);
    assign p2y=w1| w2;
    assign p1y=w3| w4;
//

endmodule

```
# output:
<img width="880" height="560" alt="wavedrom (9)" src="https://github.com/user-attachments/assets/abfb1524-48df-415d-8fe8-011c9ed30218" />










 

