module arith_op(input a,b, output sum,sub,div,mul,mod);
  assign sum = a+b;
  assign sub = a-b;
  assign div = a/b;
  assign mod = a%b;
  assign mul = a*b;
endmodule































































