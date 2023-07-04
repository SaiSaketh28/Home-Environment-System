# Home-Environment-System
![image](https://github.com/SaiSaketh28/Home-Environment-System/assets/97435804/0db2d36d-51ae-4517-a065-4e98fc4b1096)

# Verilog Code:
* module Home_Environment_Controller(T,reset,clock,y);
* input T;
* input reset;
* input clock;
* output reg [0:2]y;
* reg [0:2]state;
* parameter s0=3'b000,s1=3'b001,s2=3'b010,s3=3'b011,s4=3'b100,s5=3'b101,s6=3'b110,s7=3'b111;
* // s = 3'bxyz -> x->A.C, y->Fan, z->Heater
* always@ (posedge clock)
* begin
* if(reset == 1'b1)
* state <= s0;
* else
* begin
* case(state)
* s0 : state=(T==1'b1)?s2:s1;
* s1 : state=(T==1'b1)?s0:s1;
* s2 : state=(T==1'b1)?s6:s2;
* s6 : state=(T==1'b1)?s6:s0;
* default : state <= s0;
* endcase
* end 
* y[0:2] <= state[0:2];
* end
* endmodule

# TestBench
![image](https://github.com/SaiSaketh28/Home-Environment-System/assets/97435804/2c24bceb-213d-4529-8a41-24de3fee7afe)

