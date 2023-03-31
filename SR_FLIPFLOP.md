module sr_ff(a,b,c,q,q1);//code
    input a,b,c;
    output q,q1;
    reg q,q1 ; 

    always @(c) begin
        case({a,b})
        2'b00:begin q = q ; q1 = q1 ; end
        2'b01:begin q = 1'b0 ; q1 = 1'b1 ;end
        2'b10:begin q = 1'b1 ; q1 = 1'b0 ;end
        2'b11:begin q = 1'bx ; q1 = 1'bx ;end
        endcase        
        
    end
endmodule


//testbench 

`include "sr_flipflop.v"
`timescale 1ps/1ps

module sr_ff_tb;
    reg a,b,c ;
    wire q,q1 ;

    sr_ff uut(a,b,c,q,q1);
    
    initial begin 
        c = 0;
        repeat(10)
        begin
            c = ~c ;#5;
        end
    end

    initial begin
      a = 1 ; b = 0 ; #10;
      a = 0 ; b = 0 ; #10;
      a = 0 ; b = 1 ; #10;
      a = 0 ; b = 0 ; #10;
      a = 1 ; b = 1 ; #10;
    end

    initial begin 
        $dumpfile("sr_flipflop_tb.vcd");
        $dumpvars(0,sr_ff_tb);
    end 

endmodule
