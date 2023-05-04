Download Link: https://assignmentchef.com/product/solved-csc-230-assignment-3
<br>
<u>Part 1</u>: Called a <u>formative submission</u>, contains introductory activities that assist in the development of the final solution. The formative submission is due 1 week earlier than the final due date of the assignment.  This submission is designed to ensure you start to work on the assignment early enough to seek assistance before the final due date. When your Part 1 is as complete as possible, submit it on Connex under the Assignments, Assignment 3 Part 1

link.  If you feel there were any learning issues with this part of the assignment, follow up with the teaching team, during office hours, as early as possible during the week.

<ul>

 <li><u>Part 2</u>: Called a <u>summative submission</u>, this is the final submission of the assignment.  This will be graded in the week that follows the due date.  When your program is complete and tested, including appropriate documentation, submit it on Connex under the Assignments, Assignment 3 Part 2 link. <strong> </strong></li>

</ul>

<h1>Learning Objectives</h1>

Upon successful completion of this assignment, you should be able to write AVR assembly language programs that:

<ul>

 <li>Assemble and execute correctly on the 2560 boards</li>

 <li>Use Immediate, Register, Direct and Indexed address modes.</li>

 <li>Use loop structures</li>

 <li>Use index addressing to simulate arrays in memory</li>

 <li>Use the masks &amp; shift instructors to write bytes of data to LEDs attached to a port.</li>

</ul>

Assignment 3 Part 1:  Formative

<strong><u>Part 1</u></strong>:  The program described in this part must be written, documented and submitted.  Please follow up with any questions you may have with the teaching team during office hours, as early as possible during the following week.  (This <em>formative </em>submission is intended for form your skills, rather than create a grade.  The <em>summative evaluation</em>, which results in a grade, will be reserved for Part 2 below.)

Pseudo-code is a programming-like language that assists in program design, but is simpler or not as well defined as a programming language.  Pseudo-code will be used throughout CSC 230 and will appear similar to statements in the C, Python or Java programming languages.  It will be used to both define algorithms and serve as documentation throughout assembly language code.

Consider the following pseudo-code ‘program’:

number1 = 103; number2 = 41; number3 = 15;

diff = number1; diff -= number2; diff -= number3;

result = diff;

Essentially, this ‘program’ calculates the difference of 3 constant values, number1 – number2 – number3, stores the result in memory location called result.  In Assignment 2 Part 1, this pseudo-code will be:

<ul>

 <li>Translated into AVR assembly language,</li>

 <li>Tested on the AVR studio simulator</li>

</ul>

First, recall that the AVR microcontroller uses the <em>Harvard architecture</em>:

The program that will be run by the microcontroller must be uploaded into the code segment, which is a <em>flash</em> memory, then the program is run by the microcontroller that can use the data segment, which is a <em>static random access</em> <em>memory</em> (SRAM), to store both temporary values and result.  Observe that the code segment can be initialized, as it is when we upload the program, but the data segment cannot.  Thus, we must store the initial (hard coded) values used by the program in the code segment, along with the program.

Below is a template or starting assembly language program outline to be used in

Assignment 3 Part 1.  (It is also provided on the course site as A3P1.asm. )

.include “m2560def.inc”

;

;

***********************************************************

; * Program information goes here.                        *

; *  Examples include:  Course name, assignment number,   *

; *     program name, program description, program input, *

; *     program output, programmer name, creation date,   * ; *     dates of program updates. *

; *********************************************************




; *************************

; * Code segment follows: *

; *************************

.cseg




;************************

; Your code starts here:

;
















;

; Your code finishes here.

;*************************




done:     jmp done




; *************************

; * Data segment follows: *

; *************************

.dseg

.org 0x200

Directions: (This will require the use of the AVR Instruction Set reference document.)

<ul>

 <li>Follow the procedure described in the labs to use AVR studio to create a project called aps.</li>

 <li>Type or copy and paste the template above.</li>

 <li>Build and (if no errors) simulate the run (or debug) of the program. It really should not do anything, as there are no statements in the code segment.</li>

 <li>Type or copy and paste the first three lines of the pseudo-code above into the code segment, placing a semi-colon (;) at the beginning of each line, making them comments.</li>

 <li>After each line use an AVR load instruction, where one operand is a register and the other uses <u>immediate addressing</u>, to create these instructions in assembly language.</li>

</ul>

Build and simulate program execution, checking for correctness.

<ul>

 <li>Build and (if no errors) simulate the run (or debug) of the program.</li>

 <li>Create a comment for the diff = number1; instruction, then code it in assembly language.</li>

 <li>Create a comment for each of the lines that calculate the difference and code in assembly language (using the SUB instruction), where both operands are registers.</li>

 <li>Build and (if no errors) simulate the run (or debug) of the program.</li>

 <li>(Set up the SRAM:) Create a memory location for the result, which we will assume to be 1 byte long, in the Data Segment by typing result .db 1 on the very last line, immediately following the .dseg  and .org 0x200 assembler directives.  Observe that the SRAM memory address (in hexadecimal) 0x200 has been named result and 1 byte has been set aside for it.</li>

 <li>Build and (if no errors) simulate the run (or debug) of the program. Observe the SRAM at location 0x200 in the simulator.</li>

 <li>(Back to the code segment:) Create a comment for the result = difference;   Use the store instruction with <u>direct addressing</u> to specify the location of result.</li>

 <li>Build and (if no errors) simulate the run (or debug) of the program. Observe the</li>

</ul>

SRAM at location 0x200 in the simulator.

<ul>

 <li>Adjust the top of code comments to appropriately describe the program.</li>

</ul>

Make sure your code is fully documented, as described above.  Observe that the AVR Studio created a file in your directory called A3P1.asm.

<u>Assignment 3 Part 2</u>:  Summative  (will be graded)

<strong><u>Part 2</u></strong>:  Follow the procedure described in the labs to use AVR studio to create a project called A3P2.aps.

<ol>

 <li>Use a loop to write decrementing hexadecimal numbers into consecutive memory locations in the data memory, starting at memory address 0x200. The starting number, which is between 0x0 (inclusive) and 0xFF (inclusive) should be placed into a register (R16).  That starting number needs to be stored in the first data memory location.  Then the number will be decremented by 1 and stored in the next consecutive memory location.  This process of decrementing and storing will continue until the number 0 is the final value stored.   After each number is stored in memory, output the binary equivalent of the number on the LEDs attached to Ports L and B, with the least significant bit on Port L: bit 7.  Here is the pseudocode:</li>

</ol>

number = /* choose a number in (0x00, 0xFF] */ ; count = 0; while (number &gt; 0) {  dest[count++] = number;      * Output number on LEDs *      * delay 0.5 second *

number –;

Observe that your documentation *should* include the above pseudo code.

<ol start="2">

 <li>The fifth line of the above pseudo code (* Output number on LEDs * ) is described as follows: after each number is placed in memory, display the number, in binary on the LEDs on the board that are attached to Ports L and B.</li>

</ol>

Recall from lab 4 that the number must be spread out on every other bit to output to the port.  For example, to output the number 0xB = 0b1011 on port L, each of those 4 bits must be followed by another bit, lets use 0, such that the binary number becomes 0b<u>1</u>0<u>0</u>0<u>1</u>0<u>1</u>0.  Observe that the 4 underlined bits were the original bits.  The conversion from (for example) 0b1111 to 0b10101010 is accomplished using a ‘mask’ to separate out a single bit, shifting it to the proper location and then using an OR operation to combine the bits together.

<ol start="3">

 <li>The sixth line of the above pseudo code ( * delay 0.5 second * ). Please place the following lines in your code where the delay should occur:</li>

</ol>

<strong>rjmp delay: after:  ;next instruction </strong>

<strong> </strong>

Then place the following at the very end of your code segment (i.e., after done: jmp done. )

<strong>; The delay code, which is placed *after* the done: jmp done </strong>

<table width="487">

 <tbody>

  <tr>

   <td width="96"><strong>delay: </strong></td>

   <td width="144"><strong>ldi r24, 0x2A </strong></td>

   <td width="247"><strong> ; approx. 0.5 second delay </strong></td>

  </tr>

  <tr>

   <td width="96"><strong>outer: </strong></td>

   <td width="144"><strong>ldi r23, 0xFF </strong></td>

   <td width="247"></td>

  </tr>

  <tr>

   <td width="96"><strong>middle:  </strong></td>

   <td width="144"><strong>ldi r22, 0xFF </strong></td>

   <td width="247"></td>

  </tr>

  <tr>

   <td width="96"><strong>inner:  </strong></td>

   <td width="144"><strong>dec r22 </strong></td>

   <td width="247"></td>

  </tr>

  <tr>

   <td width="96"><strong>       </strong></td>

   <td width="144"><strong>brne inner </strong></td>

   <td width="247"></td>

  </tr>

  <tr>

   <td width="96"><strong>       </strong></td>

   <td width="144"><strong>dec r23 </strong></td>

   <td width="247"></td>

  </tr>

  <tr>

   <td width="96"><strong>       </strong></td>

   <td width="144"><strong>brne middle </strong></td>

   <td width="247"></td>

  </tr>

  <tr>

   <td width="96"><strong>       </strong></td>

   <td width="144"><strong>dec r24 </strong></td>

   <td width="247"></td>

  </tr>

  <tr>

   <td width="96"><strong>       </strong></td>

   <td width="144"><strong>brne outer </strong></td>

   <td width="247"></td>

  </tr>

  <tr>

   <td width="96"><strong>       </strong></td>

   <td width="144"><strong>rjmp after </strong></td>

   <td width="247"></td>

  </tr>

 </tbody>

</table>




(Academic Integrity altert:  Always give credit to an author who agrees to let you use their code. For example, consider adding “Credit: L. Jackson for the writing the following 9 lines:”)

Test your code on the simulator in the AVR studio, then upload it onto an Arduino 2560 board in the ECS 249 lab and test.


