# 4--bit-decimal-counter
// Code your design here
module bcd(rst,clk,bcd_out);
  input rst,clk;
  output reg [3:0] bcd_out;
  
  always @(posedge(clk))
    if(rst)
      if(bcd_out==4'd9)
        bcd_out=4'b0;
      else
        bcd_out=bcd_out+1;
  else
    bcd_out=4'd0;
endmodule

// code for test bench in EDA playground software
// Code your testbench here

module tbs;
  reg rst,clk;
  wire [3:0]bcd_out;
  bcd b1(rst,clk,bcd_out);
  
  initial
    clk=0;
  always #1 clk=~clk;
    begin
      $dumpfile("dump.vcd");$dumpvars;
       clk=0;
      #10 rst=1;
      #10 $finish;
  end 
endmodule
//The code here is to simulate 4 bit decimal counter in Xilinx Design tools or EDA playground software
