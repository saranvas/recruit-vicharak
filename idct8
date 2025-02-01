`timescale 1ns / 1ps


module idct8 #(parameter width_x =16,
parameter width_y=22)(
input wire signed [width_x-1 :0] x0,
input wire signed [width_x-1 :0] x1,
input wire signed [width_x-1 :0] x2,
input wire signed [width_x-1 :0] x3,
input wire signed [width_x-1 :0] x4,
input wire signed [width_x-1 :0] x5,
input wire signed [width_x-1 :0] x6,
input wire signed [width_x-1 :0] x7,
input wire clk,rst,
input wire load,
output wire signed[width_y-1:0] y0,
output wire signed[width_y-1:0] y1,
output wire signed[width_y-1:0] y2,
output wire signed[width_y-1:0] y3,
output wire signed[width_y-1:0] y4,
output wire signed[width_y-1:0] y5,
output wire signed[width_y-1:0] y6,
output wire signed[width_y-1:0] y7);

reg signed [width_x-1:0] x0_reg;
reg signed [width_x-1:0] x1_reg;
reg signed [width_x-1:0] x2_reg;
reg signed [width_x-1:0] x3_reg;
reg signed [width_x-1:0] x4_reg;
reg signed [width_x-1:0] x5_reg;
reg signed [width_x-1:0] x6_reg;
reg signed [width_x-1:0] x7_reg;

reg signed[width_x-1:0] z0_reg;
reg signed[width_x-1:0] z1_reg;
reg signed[width_x-1:0] z2_reg;
reg signed[width_x-1:0] z3_reg;
reg signed[width_x-1:0] z4_reg;
reg signed[width_x-1:0] z5_reg;
reg signed[width_x-1:0] z6_reg;
reg signed[width_x-1:0] z7_reg;

 wire signed [width_y:0] z0_nxt;
wire signed [width_y:0] z1_nxt;
wire signed [width_y:0] z2_nxt;
wire signed [width_y:0] z3_nxt;
wire signed [width_y:0] z4_nxt;
wire signed [width_y:0] z5_nxt;
wire signed [width_y:0] z6_nxt;
wire signed [width_y:0] z7_nxt;

always @(posedge clk)
begin
if(rst) begin
x0_reg <= 0;
x1_reg <= 0;
x2_reg <= 0;
x3_reg <= 0;
x4_reg <= 0;
x5_reg <= 0;
x6_reg <= 0;
x7_reg <= 0;

z0_reg <=0;
z1_reg <= 0;
z2_reg <= 0;
z3_reg <= 0;
z4_reg <= 0;
z5_reg <= 0;
z6_reg <= 0;
z7_reg <= 0;

end
else begin 
if(load) begin
x0_reg <= x0;
x1_reg<=x1;
x2_reg<=x2;
x3_reg<=x3;
x4_reg<=x5;
x5_reg<=x5;
x6_reg<=x6;
x7_reg<=x7;

end
z0_reg <= z0_nxt;
z1_reg <= z1_nxt;
z2_reg <= z2_nxt;
z3_reg <= z3_nxt;
z4_reg <= z4_nxt;
z5_reg <= z5_nxt;
z6_reg <= z6_nxt;
z7_reg <= z7_nxt;

end
end

IDCT4 #(.width_x(width_x),.width_y(width_x)) idct4(.clk(clk),.rst(rst),.load(load),.x0(x0_reg),.x1(x1_reg),.x2(x2_reg),.x3(x3_reg),.y0(z0_nxt),.y1(z1_nxt),.y2(z2_nxt),.y3(z3_nxt) );


assign z4_nxt =(-x1_reg *2) + (x3_reg*18)-(x5_reg*9)+(x7_reg * 36);
assign z5_nxt  =(-x1_reg *18) + (x3_reg*9)-(x5_reg*18)-(x7_reg * 36);
assign z6_nxt = (-x1_reg *9) + (x3_reg*18)+(x5_reg*36)+(x7_reg * 36);
assign z7_nxt  =(-x1_reg *2) - (x3_reg*18)-(x5_reg*9)-(x7_reg * 36);

assign y0 = z0_reg-z7_reg;
assign y1 = z1_reg-z6_reg;
assign y2 = z2_reg-z5_reg;
assign y3 = z3_reg-z4_reg;
assign y4 = z3_reg+z4_reg;
assign y5 = z2_reg+z5_reg;

assign y6 = z1_reg+z6_reg;
assign y7 = z0_reg+z7_reg;
endmodule






































