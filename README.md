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

>
DESCRIPTION
The module consists of a moisture sensor, temperature sensor, priority 
encoders, 3-bit binary adder, magnitude comparator and a crop value 
counter. The working begins with collecting inputs from the moisture and 
temperature sensors. The crop value counter sets the type of crop which is to 
be irrigated. The rest of the components are utilised to manipulate and blend 
the input to perform the functionality of setting an optimal threshold and 
deciding the amount of water needed.
> 
MOISTURE SENSOR:
A capacitive moisture sensor has been used which measures the moisture 
content in a given soil sample. The moisture sensor has been coupled with an 
Arduino device. The output of the moisture sensor is in the range of 0-100.The 
Arduino code written enables us to manipulate the sensed value such that it 
gives 0 if the sensed value is in the range 0-10,1 if the sensed value is in the 
range 11-20 and so on.
>
TEMPERATURE SENSOR:
A capacitive temperature sensor has been employed which measures the 
temperature conditions of the atmosphere at the instant. It is also coupled
with an Arduino device. The range of values is 0-100 but practically speaking 
it is just in very extreme conditions that the temperature exceeds 50. So, the 
Arduino code is written to map the sensed values as 0 in the range 0-10,1 in 
the range 11-20 and so on till 4 in the range 41-50.
>
CROP TYPE SELECTOR:
We have deployed a predefined menu to select the type of crop in use. For,
the sake of the project prototype we have listed down a few crops in the 
order of the increasing amount of water they need. Each of them is given a 
decimal number as reference in the order of their requirement of water. We 
have selected rice, wheat, maize, bean and sugarcane as prototypes. Each of 
the crops is given a value as shown in the table below depending on their 
optimal moisture requirement. Sugarcane is given a value 4 which implies it 
has the highest water requirement from amongst the selected, conversely 
bean is given a value 0 implying it has the least water requirement. The
selection of the crop has been implemented using a synchronous 3-bit updown counter circuit counting from 0 to 4 giving the output in binary format.
>
PRIORITY ENCODERS:
The values given by the moisture sensor and temperature sensors is passed 
into priority encoders to convert them to binary form. The value from the 
moisture sensor is fed into a 4-bit priority encoder and the value from the 
temperature sensor is passed into a 3-bit priority encoder.
>
4-BIT BINARY ADDER:
This component’s functionality is to set an optimal threshold value for the 
moisture content needed depending on the crop type and the input from the
temperature sensor modified using a 3-bit priority encoder. The binary values 
from the 3-bit priority encoder and the crop type selector are fed in as inputs 
with a 0 appended to them to make them as 4-bit inputs. The output of this 4-
bit binary adder gives us with a reasonable threshold for the moisture content 
that is required in the existing conditions.
>
4-BIT MAGNITUDE COMPARATOR:
This component compares the output of the 4-bit binary adder with the value 
given by the moisture sensor encoded to binary using a 4 bit priority encoder.
It gives three outputs after comparing the given values. Now, we water the 
crop only if the value from the moisture sensor is less or equal to the 
threshold value. The following actions are undertaken depending on the 
output of the magnitude comparator assuming a and b are inputs given to it.

>
Outcome ACTION
a<b The crop is watered
a=b The crop is watered
a>b No watering is carried out
BEAN 0
WHEAT 1
MAIZE 2
RICE 3
SUGARCANE 4
>
WORKING OF THE MODULE:
The major functionality of the module is dependent on the following:
1.The Crop type selector.
2.Encoding the output from the sensors.
3.Setting the threshold using the 4-bit binary adder.
4.Comparing the values using the magnitude comparator.

>
SETTING THE THRESHOLD:
This is carried out by the 4-bit binary adder using the outputs from the crop 
type selector and the temperature sensor as inputs according to the 
following functional tables:

>![Screenshot 2023-11-21 110621](https://github.com/VishruthSKumar/S2-T20-HYDROSURE/assets/149406271/f8e68bb2-a51d-4eef-b746-d7fbc511bac0)

 
>
CROP TYPE SELECTOR:
The crop type selector uses synchronous 3-bit up down circuit, counting 
numbers from 0 to 4 since the prototype has 4 types of crops. This circuit 
consists of 3 T flip-flops in the sequential circuit segment and comprises of 
combination of AND & OR gates in combinational part. It uses LED display to 
the output in binary form (7- segment display can also be used). It uses a 
pushbutton to navigate through inputs. Reverser button is used to change the 
direction of navigation (ascending (0) / descending (1)). The upper limit of the 
crop is 4 and returns back to 0 on further push up (vice-versa if direction is 
reversed).

> ![Screenshot 2023-11-21 110651](https://github.com/VishruthSKumar/S2-T20-HYDROSURE/assets/149406271/4a0e69c9-43a4-4e62-8018-5781590948d0)

>
FLOWCHART :

![Screenshot 2023-11-21 110718](https://github.com/VishruthSKumar/S2-T20-HYDROSURE/assets/149406271/362aed40-ecfe-46cd-a8b8-cc8bd8c92787)

  
</details>

<!-- Fourth Section -->
## Logisim Circuit Diagram
<details>
  <summary>Detail</summary>


  > ![Screenshot 2023-11-21 103541](https://github.com/VishruthSKumar/S2-T20-HYDROSURE/assets/149406271/26c281ed-ee21-4896-9df2-bea15e1aaaf3)
> ![Screenshot 2023-11-21 103626](https://github.com/VishruthSKumar/S2-T20-HYDROSURE/assets/149406271/925205de-adca-47a8-a3ff-a43cfd146462)


</details>

<!-- Fifth Section -->
## Verilog Code
<details>
  <summary>Detail</summary>

  > Main code :
-------------------------------------------------------------------------------------------------------------------------
  ```
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
```

 > Testbench : 
 ----------------------------------------------------------------------------------------------------------------------------------------
 ```
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
```
</details>


<!-- Sixth Section -->
## References
<details>
  <summary>Detail</summary>

  >1.https://circuitdigest.com/microcontroller-projects/interfacing-soil-moisture-sensor-with-arduino-uno

>2.https://nevonprojects.com/plant-soil-moisture-ph-sensing-alarm-using-8051

>3.https://youtu.be/ZGlm72xhhqU?feature=shared

>4.https://www.geeksforgeeks.org/soil-moisture-measurement-using-arduino-and-soil-moisture-sensor

>5.https://www.sciencebuddies.org/science-fair-projects/project-ideas/Elec_p066/electricityelectronics/build-an-electronic-soil-moisture-sensor-to-conserve-water
</details>
     

  
