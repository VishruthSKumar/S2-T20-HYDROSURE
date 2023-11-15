# HYDRO-SURE

<!-- First Section -->
## Team Details
<details>
  <summary>Detail</summary>

  > Semester: 3rd Sem B. Tech. CSE

  > Section: S2

  > Member-1: Syed Farhan , 221CS254 , syedfarhan.221cs254@nitk.edu.in

  > member-2: Vishruth S Kumar , 221CS262 , vishruthskumar.221cs262@nitk.edu.in

  > Member-3: Yashas , 221CS265 , yashas.221cs265@nitk.edu.in
</details>

<!-- Second Section -->
## Abstract
<details>
  <summary>Detail</summary>
  
  > 
The objective of the project is to develop a moisture sensing and temperature 
sensing cum watering system for irrigation. This system will combine cutting-edge 
hardware and software technologies to enhance the effectiveness of irrigation 
practices. The core objective is to create a system that can accurately measure the 
moisture content in a given soil sample and sense the temperature conditions at a 
given time. We then integrate those values effectively depending on the crop type to 
decide upon the adequate amount of water needed by the crop in the pertaining 
conditions. Conclusively, the circuit is a blend of moisture and temperature 
sensations aided by the type of crop in use to develop an efficient and sustainable 
system to monitor the sufficiency of water. The system will incorporate automated 
irrigation capabilities, ensuring crops receive the right amount of water at the right 
time.

Agriculture forms the cornerstone of the economy, serving as its foundational pillar. 
The project recognizes the global challenges of water scarcity and climate change, 
which underscore the urgency of adopting efficient irrigation techniques. The 
project emphasizes the importance of technology driven solutions in modern 
agriculture to meet the growing global demand for food. The project underscores 
the importance of responsible environmental stewardship. By reducing the
environmental footprint of agriculture, it aligns with global efforts to protect 
ecosystems and biodiversity.

We are designing and implement advanced algorithms to process the sensor data 
efficiently, providing real-time insights into soil moisture levels. Additionally, we are 
developing predictive models to optimize irrigation strategies, ensuring precise 
water delivery for maximum crop yields. Our experience in integrating hardware and 
software solutions will be instrumental in creating a seamless and user-friendly 
interface for farmers. Ultimately, our skills will play a vital role in harnessing the
power of technology to enhance the project's overall effectiveness and impact.



</details>

<!-- Third Section -->
## Working
<details>
  <summary>Detail</summary>

  > https://drive.google.com/file/d/1rYcJ-d5nwh42e9u8xAcuKVaSAy0qt3nu/view?usp=sharing
</details>

<!-- Fourth Section -->
## Logisim Circuit Diagram
<details>
  <summary>Detail</summary>

  > https://github.com/VishruthSKumar/S2_TEAM_20_/blob/07b0044c5a9d5c05510642b7ed797be4a005b0c0/Logisim/LOGISIM.circ
</details>

<!-- Fifth Section -->
## Verilog Code
<details>
  <summary>Detail</summary>

  > Main code : https://github.com/VishruthSKumar/S2_TEAM_20_/blob/df3108d6bb7835548d40711aef36a32e99e59a83/Verilog/S2-T20.v
  > Testbench : https://github.com/VishruthSKumar/S2_TEAM_20_/blob/6970d05a4999e1d13abd378c3d10114265bc41ed/Verilog/S2-T20_tb.v
  
Main code
-------------------------------------------------------------------------------------------------------------------------
  module circuit(ms,ts,ct,o1,o2,o3);

   input [3:0]ms;
   input [3:0]ts;
   input [3:0]ct;
   output o1,o2,o3;
   wire [3:0]s1;
   wire c1out;

   adder_four_bit A1(s1,c1out,ts,ct);

   comparator C1(ms,s1,o2,o3,o1);

   endmodule



   module adder_four_bit(output [3:0]sum, output cout , input [3:0]a,input [3:0]b);

   wire c1,c2,c3,c4;

   full_3 ad0( .a(a[0]), .b(b[0]),.cin(1'b0), .s(sum[0]), .cout(c1));
   full_3 ad1( .a(a[1]), .b(b[1]),.cin(c1), .s(sum[1]), .cout(c2));
   full_3 ad2( .a(a[2]), .b(b[2]),.cin(c2), .s(sum[2]), .cout(c3));
   full_3 ad3( .a(a[3]), .b(b[3]),.cin(c3), .s(sum[3]), .cout(c4));
   assign cout= c4;
   endmodule

   module full_3(a,b,cin,s,cout);
   input a,b,cin;
   output s, cout;
   assign s=a^b^cin;
   assign cout = (a&b) | (b&cin) | (cin&a);
   endmodule

   module comparator(A,B,E,G,S);
   input[3:0]A;
   input [3:0]B;
   output E,G,S;
  
   assign E=!(A[3]^B[3])&!(A[2]^B[2])&!(A[1]^B[1])&!(A[0]^B[0]);
  
   assign G=(A[3]&(!(B[3])))|(!(A[3]^B[3])&(A[2]&(!(B[2]))))|((!(A[3]^B[3])&!(A[2]^B[2]))&(A[1]&(!(B[1]))))|((!(A[3]^B[3])&!(A[2]^B[2])&! 
            (A[1]^B[1]))&(A[0]&(!(B[0]))));
   
   assign S=(B[3]&(!(A[3])))|(!(A[3]^B[3])&(B[2]&(!(A[2]))))|((!(A[3]^B[3])&!(A[2]^B[2]))&(B[1]&(!(A[1]))))|((!(A[3]^B[3])&!(A[2]^B[2])&! 
            (A[1]^B[1]))&(B[0]&(!(A[0]))));

   endmodule  

 Testbench : 
 ----------------------------------------------------------------------------------------------------------------------------------------
 module ddsproject_tb;
	wire o1,o2,o3;
	reg [3:0]ms;
    reg [3:0]ts;
    reg [3:0]ct;
	circuit C1(ms,ts,ct,o1,o2,o3); 

    initial 
       begin 
        $dumpfile("ddsproject.vcd");
        $dumpvars(0,ddsproject_tb);
       end
		
	initial begin
    $display("|   Crop    |tp_sensor  | M_sensor  | Outputs|");
    $display("----------------------------------------------");
    $display("|c3|c2|c1|c0|t3|t2|t1|t0|m3|m2|m1|m0|o1|o2|o3|");
    $display("----------------------------------------------");
    
    ct = 4'b0000;
    ts = 4'b0000;
    ms = 4'b0000;
    
    $monitor("|%b|%b|%b|%b|%b|%b|%b|%b|%b|%b|%b|%b|%b|%b|%b|",ct[3],ct[2],ct[1],ct[0],ts[3],ts[2],ts[1],ts[0],ms[3],ms[2],ms[1],ms[0],o1,o2,o3);
    
    repeat(5) begin
        ts = 4'b0000;
        repeat(5) begin
        ms = 4'b0000;
            repeat(15) begin
                #10 ms = ms + 4'b0001;
            end
         #10 ts = ts + 4'b0001;
        end
    #10 ct = ct + 4'b0001;
    end
  end
initial #10000 $finish;
endmodule


<!-- Sixth Section -->
## References
<details>
  <summary>Detail</summary>

  > >https://circuitdigest.com/microcontroller-projects/interfacing-soil-moisture-sensor-with-arduino-uno
> https://nevonprojects.com/plant-soil-moisture-ph-sensing-alarm-using-8051/
>https://youtu.be/ZGlm72xhhqU?feature=shared
>https://www.geeksforgeeks.org/soil-moisture-measurement-using-arduino-and-soil-moisture-sensor/
>https://www.sciencebuddies.org/science-fair-projects/project-ideas/Elec_p066/electricityelectronics/build-an-electronic-soil-moisture-sensor-to-conserve-water
</details>
     

  
