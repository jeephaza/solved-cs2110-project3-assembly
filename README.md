Download Link: https://assignmentchef.com/product/solved-cs2110-project3-assembly
<br>
Hello and welcome to Project 3. In this project, you’ll write some simple programs in assembly, and then build your very own Reverse Polish Notation calculator in assembly!

<h3><a name="_Toc14405"></a>1.2      General Instructions</h3>

<ul>

 <li>You can create your own labels and fill them with data as you see fit.</li>

 <li>You can modify the values stored in some of the helper labels we provide you if you think it’ll make it easier for you to program with</li>

 <li>You are free to create your own helper subroutines (although you are not required to for this project).</li>

 <li>Take a look at Section 6 for details on the LC-3 Assembly Programming requirements that you must adhere to</li>

</ul>

<h3><a name="_Toc14406"></a>1.3      Running the autograder</h3>

Take a look at section 4 for information on how to run the autograder, and how to debug your code.

<h1><a name="_Toc14407"></a>2         Simple ASM Programs</h1>

<h3><a name="_Toc14408"></a>2.1     Compare</h3>

To start off, you will implement the compare function. Comparing two values is something you will do frequently in assembly, so it’s important you know how to do this. The two operands are stored in memory with the labels A and B. You will load them from memory, and store a value in the label RESULT. The value that you store to RESULT depends on whether A is greater than B.

<ul>

 <li>If <em>A&lt;B</em>, you should store −1.</li>

 <li>If <em>A </em>= <em>B</em>, you should store 0.</li>

 <li>If <em>A&gt;B</em>, you should store 1.</li>

</ul>

You may assume that the memory addresses labeled as A, B, RESULT are reachable via a PC-offset instruction with 9-bit offset. Write your code in comp.asm.

<h3><a name="_Toc14409"></a>2.2     Modulus</h3>

In this part of the project, you will be implementing the modulus operator that you will find in a lot of programming languages. Since there are different interpretations of modulus for negative numbers, you should take the absolute values of both your operands and then perform the operation. The two operands are stored in memory with the labels A and B. You will load them from memory, perform the modulus operation, and then store the result in the label RESULT.

<strong>Suggested Pseudocode:</strong>

a = mem[A]; b = mem[B];

a = abs(a); b = abs(b);

while (a &gt;= b) { a = a – b;

} mem[RESULT] = a;

You may assume that the memory addresses labeled as A, B, RESULT are reachable via a PC-offset instruction with 9-bit offset. You do not need to worry about overflow for negation or subtraction. Write your code in mod.asm.

<h3><a name="_Toc14410"></a>2.3      To Uppercase</h3>

Next, you will write a program that prints out an all uppercase version of an input string. You do not need to change the string store in memory, but instead just print the uppercase string to console.

<ul>

 <li>Strings are essentially a contiguous array of ASCII values. In this case, the first character is stored at the address indicated by the <strong>value </strong>at the address labeled as STRING.</li>

 <li>The string continues until the first instance of a null terminator, which has the value of 0.</li>

</ul>

Here is an example layout:

<table width="171">

 <tbody>

  <tr>

   <td width="62">Address</td>

   <td width="58">Label</td>

   <td width="51">Value</td>

  </tr>

  <tr>

   <td width="62">···</td>

   <td width="58">···</td>

   <td width="51">···</td>

  </tr>

  <tr>

   <td width="62">x3021</td>

   <td width="58">STRING</td>

   <td width="51">x4000</td>

  </tr>

  <tr>

   <td width="62">x3022</td>

   <td width="58">RESULT</td>

   <td width="51"> </td>

  </tr>

  <tr>

   <td width="62">···</td>

   <td width="58">···</td>

   <td width="51">···</td>

  </tr>

  <tr>

   <td width="62">x4000</td>

   <td width="58"> </td>

   <td width="51">“h”</td>

  </tr>

  <tr>

   <td width="62">x4001</td>

   <td width="58"> </td>

   <td width="51">“A”</td>

  </tr>

  <tr>

   <td width="62">x4002</td>

   <td width="58"> </td>

   <td width="51">“h”</td>

  </tr>

  <tr>

   <td width="62">x4003</td>

   <td width="58"> </td>

   <td width="51">“A”</td>

  </tr>

 </tbody>

</table>

The string that you receive can contain any characters, and you should change all letters to uppercase, and leave non-letters as is. You may assume that the memory address labeled as STRING will be reachable via a PC-offset instruction with 9-bit offset. However, the actual contents of the string might be stored at addressed that can’t be reached via a 9-bit offset. We have given you some labels in the assembly file that you might find helpful. As a hint, take a look at the trap vectors to see how you might print characters to the console. Write your code in toupper.asm.

<h3><a name="_Toc14411"></a>2.4       Alternating array sum</h3>

For this section, you will iterate through an array and either add or subtract from a sum depending on the index of the array. For every element with an even index, you should add its value to the sum. For every element with an odd index, you should subtract its value from the sum. The sum should start from 0, and we are using 0-indexing here. The array length will be stored at the label LENGTH and the <strong>address </strong>of the first element will be stored at the label ARRAY. Note that ARRAY stores the address of the first element instead of the first element itself. An example memory layout might look something like this:

<table width="171">

 <tbody>

  <tr>

   <td width="62">Address</td>

   <td width="58">Label</td>

   <td width="51">Value</td>

  </tr>

  <tr>

   <td width="62">···</td>

   <td width="58">···</td>

   <td width="51">···</td>

  </tr>

  <tr>

   <td width="62">x3020</td>

   <td width="58">LENGTH</td>

   <td width="51">4</td>

  </tr>

  <tr>

   <td width="62">x3021</td>

   <td width="58">ARRAY</td>

   <td width="51">x7000</td>

  </tr>

  <tr>

   <td width="62">x3022</td>

   <td width="58">RESULT</td>

   <td width="51"> </td>

  </tr>

  <tr>

   <td width="62">···</td>

   <td width="58">···</td>

   <td width="51">···</td>

  </tr>

  <tr>

   <td width="62">x7000</td>

   <td width="58"> </td>

   <td width="51">1</td>

  </tr>

  <tr>

   <td width="62">x7001</td>

   <td width="58"> </td>

   <td width="51">2</td>

  </tr>

  <tr>

   <td width="62">x7002</td>

   <td width="58"> </td>

   <td width="51">3</td>

  </tr>

  <tr>

   <td width="62">x7003</td>

   <td width="58"> </td>

   <td width="51">4</td>

  </tr>

 </tbody>

</table>

After you compute the sum, you should store the value in RESULT. You can assume that the labels LENGTH, ARRAY, RESULT will be reachable via a PC-offset instruction with a 9-bit offset, but you cannot make the same assumption about the starting address of the array stored in ARRAY. You might notice that the memory layout is very similar to the previous question, so maybe consider resuing your code. Write your code in sum.asm.

<h1><a name="_Toc14412"></a>3          Building an RPN Calculator</h1>

For this part of the project, you will be implementing a Reverse Polish Notation calculator (RPN) from scratch in LC3 assembly.

Your calculator must support the following operators:

<ol>

 <li>Addition (+)</li>

 <li>Subtraction (−)</li>

 <li>Multiplication (∗)</li>

 <li>Division (<em>/</em>)</li>

</ol>

The operands will be integers in 2’s complement. You don’t have to support floating point numbers.

The part of the project is further subdivided into two sub-parts. For the first sub-part, you will be implementing all of the supported operands (+, -, *, /) as subroutines. For the second sub-part, you will use these subroutines to build the calculator.

Before we lay out the specification for each part, we will discuss some background material.

<h3><a name="_Toc14413"></a>3.1     Background</h3>

We are used to calculating expressions like (3 + 4)<em>/</em>10 and 5 ∗ 8 − 20<em>/</em>10 using PEMDAS, which helps us discern the order of precedence, i.e., the order in which we should carry out calculations.

Expressions of this form, in which the operator is in between the operands, are called infix expressions. This notation is commonly used in our day-to-day life because it’s easy to read and parse by humans.

However, for computers, computing infix expressions poses some challenges. For simple expressions like 5 + 1 − 10, the task is relatively straightforward: accumulate the results from left to right.

Things get more interesting when we start bringing parentheses and operators with different precedence into the picture. Let’s take 5 ∗ 8 − 20<em>/</em>10. If we were to compute it from left to right, accumulating results as we go, we’ll get 2 as the final answer, which is incorrect. This is because ∗ and <em>/ </em>have a higher precedence that − (as per PEMDAS), and therefore stick to its operands more strongly. As a result, we must first perform 5 ∗ 8, then 20<em>/</em>10, and only then subtract the results. Doing this gives us 38, which is the correct answer.

This is a simple example. It gets even more complicated when we have deep levels of nesting. A standard way to compute infix expressions is by writing a Pratt parser. Making you write such a parser, and then evaluate the resulting tree, in LC3 assembly, would be very mean, and I would like to think that I have a heart &lt;3.

So, how do we solve this problem?

<h4><a name="_Toc14414"></a>3.1.1        Leveraging the Stack</h4>

Lucky for us, there exists another notation for arithmetic and logical expressions. It’s the postfix notation.

In this notation, the operators come after their operands. For example, 3 + 4 in infix notation would be 3 4 + in postfix notation. A very nice property of postfix notation is that we can compute the resulting expression using a stack. Allow me to blow your mind :).

Let’s say we want to compute 3+4. It’s corresponding postfix form is 3 4 +. To begin calculating the result, we will parse tokens (numbers or operators) starting from the left. If we encounter a number, we push it onto the stack. If we encounter an operator, we’ll pop values off the stack, calculate the result of applying the operator on the values we just popped, and the push the result back onto the stack. The final result will be the value that’s on top of the stack.

For 3 4 +, the first token is 3, which is a number. Since it’s a number, we push it onto the stack (Figure 1a). Next, we find 4, which is also a number. So, we push 4 onto the the stack (Figure 1b). Then, we find +, which is an operator. + is a binary operator, and takes in two operands. Therefore, we pop two values off the stack, carry out the addition on these two values, and then push the result back onto the stack. The two values in our case are 3 and 4. Performing the addition gives us 7 (Figure 1c). Pushing 7 results in Figure 1d. Since we don’t have any more tokens to parse, we can stop. The final result 7 is on top of the stack.

Alright, so this is super cool and all, but does it solve the problem that we earlier had with infix expressions? You sure betcha! The postfix form of 5 ∗ 8 − 20<em>/</em>10 is 5 8 ∗ 20 10 <em>/ </em>− (Do not worry about how we got this postfix expression. Interestingly enough, you can build such an expression from the infix form using a stack). Try computing this postfix expression using the method described above. You will get 38 as your final answer, which is indeed the correct answer!

The postfix notation is also known as Reverse Polish Notation (RPN). An RPN calculator, therefore, is a stack based calculator that can compute postfix expressions.

Computerphile has a really neat <a href="https://www.youtube.com/watch?v=7ha78yWRDlE">video on RPN</a><a href="https://www.youtube.com/watch?v=7ha78yWRDlE">.</a> Feel free to take a look if you need help understanding postfix notation a little more.

With background information out of the way, let’s begin writing our RPN calculator!

(a) Push <em>A </em>onto stack                                     (b) Push <em>B </em>onto stack                                    (c) Execute operation

(d) Push <em>A </em>+ <em>B </em>onto stack

Figure 1: Computing (3 4 +) on the stack

<h3><a name="_Toc14415"></a>3.2     Specification</h3>

<h4><a name="_Toc14416"></a>3.2.1         Implementing the Operators</h4>

For this part, we will be implementing four operators:

<ol>

 <li>Addition (+)</li>

 <li>Subtraction (−)</li>

 <li>Multiplication (∗)</li>

 <li>Division (<em>/</em>)</li>

</ol>

You will write your code in rpn.asm.

For each subroutine in rpn.asm, you will find comments that document the expected API contract that you need to uphold.

For multiplication and division, we highly recommend that you use the following pseudocode as a guide when writing your assembly. Recursive implementations of these operations exist, and you can definitely solve it that way for an added challenge, but we don’t test for recursion, and so you are not required to do it.

<strong>Suggested Pseudocode:</strong>

Multiply:

result = 0; counter = B; negate = 0; if (counter &lt; 0) { counter = -1 * counter; negate = 1;

} while (counter &gt; 0) { result = result + A; counter = counter -1;

}

if (negate &gt; 0) { result = -1 * result;

}

Divide:

result = 0; tempA = A; negate = 0; if (tempA &lt; 0) { negate = negate – 1; tempA = -1 * tempA;

} tempB = B; if (tempB &lt; 0) { negate = negate + 1; tempB = -1 * tempB;

} while (tempA &gt;= tempB) { result = result + 1; tempA = tempA – tempB

}

if (negate != 0) { result = -1 * result; }

<h4><a name="_Toc14417"></a>3.2.2         Bringing it all together</h4>

Now that we have all of our operators implemented, it is time to build the RPN calculator.

You will write your code for this part in rpn.asm as a subroutine under the label rpn. The comments above the subroutine document the expected API contract that you need to uphold.

<h1><a name="_Toc14418"></a>4       Debugging</h1>

When you turn in your files on Gradescope for the first time, you might not receive a perfect score. Does this mean you change one line and spam Gradescope until you get a 100? No! You can use a handy tool known as tester strings.

<ol>

 <li>First off, we can get these tester strings in two places: the local grader or off of Gradescope. To run the local grader:

  <ul>

   <li>Mac/Linux Users:

    <ul>

     <li>Navigate to the directory your project is in. <strong>In your terminal, not in your browser</strong></li>

     <li>Run the command sudo chmod +x grade.sh</li>

     <li>Now run ./grade.sh</li>

    </ul></li>

   <li>Windows Users:

    <ul>

     <li>On <strong>docker quickstart</strong>, navigate to the directory your project is in (b) Run ./grade.sh</li>

    </ul></li>

  </ul></li>

</ol>

When you run the script, you should see an output like this:

Copy the string, starting with the leading ‘B’ and ending with the final backslace. Do not include the quotations.

<strong>Side Note: </strong>If you do not have docker installed, you can still use the tester strings to debug your assembly code. In your Gradescope error output, you will see a tester string. When copying, make sure you copy from the first letter to the final backslace and again, don’t copy the quotations.

<ol start="2">

 <li>Secondly, navigate to the clipboard in your docker image and paste in the string.</li>

 <li>Next, go to the Test Tab and click Setup Replay String</li>

 <li>Now, paste your tester string in the box!</li>

 <li>Now, complx is set up with the test that you failed! The nicest part of complx is the ability to step through each instruction and see how they change register values. To do so, click the step button. To change the number representation of the registers, double click inside the register box.</li>

 <li>If you are interested in looking how your code changes different portions of memory, click the view tab and indicate ‘New View’</li>

 <li>Now in your new view, go to the area of memory where your data is stored by CTRL+G and insert the address</li>

 <li>One final tip: to automatically shrink your view down to only those parts of memory that you care about (instructions and data), you can use View Tab → Hide Addresses → Show Only Code/Data. Just be careful: if you misclick and select Show Non Zero, it <em>may </em>make the window freeze (it’s a known Complx bug).</li>

</ol>

<h1><a name="_Toc14419"></a>5      Deliverables</h1>

Turn in the files comp.asm, mod.asm, toupper.asm, sum.asm, and rpn.asm to Gradescope by the due date.

<strong>Note: Please do not wait until the last minute to run/test your project, history has proved that last minute turn-ins will result in long queue times for grading on Gradescope. You have been warned.</strong>

<h1><a name="_Toc14420"></a>6         LC-3 Assembly Programming Requirements</h1>

<h3><a name="_Toc14421"></a>6.1     Overview</h3>

<ol>

 <li>Your code must assemble with <strong>NO WARNINGS OR ERRORS</strong>. To assemble your program, open the file with Complx. It will complain if there are any issues. <strong>If your code does not assemble you WILL get a zero for that file.</strong></li>

 <li><strong>Comment your code! </strong>This is especially important in assembly, because it’s much harder to interpret what is happening later, and you’ll be glad you left yourself notes on what certain instructions are contributing to the code. Comment things like what registers are being used for and what less intuitive lines of code are actually doing. To comment code in LC-3 assembly just type a semicolon (;), and the rest of that line will be a comment.</li>

 <li>Avoid stating the obvious in your comments, it doesn’t help in understanding what the code is doing.</li>

</ol>

<strong>Good Comment</strong>

<table width="404">

 <tbody>

  <tr>

   <td width="167">ADD R3, R3, -1</td>

   <td width="237">; counter–</td>

  </tr>

  <tr>

   <td width="167">BRp LOOP<strong>Bad Comment</strong></td>

   <td width="237">; if counter == 0 don’t loop again</td>

  </tr>

  <tr>

   <td width="167">ADD R3, R3, -1</td>

   <td width="237">; Decrement R3</td>

  </tr>

  <tr>

   <td width="167">BRp LOOP</td>

   <td width="237">; Branch to LOOP if positive</td>

  </tr>

 </tbody>

</table>

<ol start="4">

 <li><strong>DO NOT assume that ANYTHING in the LC-3 is already zero. </strong>Treat the machine as if your program was loaded into a machine with random values stored in the memory and register file.</li>

 <li>Following from 3. You can randomize the memory and load your program by doing File – Randomize and Load.</li>

 <li>Use the LC-3 calling convention. This means that all local variables, frame pointer, etc… must be pushed onto the stack. Our autograder will be checking for correct stack setup.</li>

 <li>Start the stack at xF000. <strong>The stack pointer always points to the last used stack location. </strong>This means you will allocate space <strong>first</strong>, then store onto the stack pointer.</li>

 <li>Do NOT execute any data as if it were an instruction (meaning you should put .fills after <strong>HALT </strong>or RET).</li>

 <li>Do not add any comments beginning with @plugin or change any comments of this kind.</li>

 <li><strong>Test your assembly. </strong>Don’t just assume it works and turn it in.</li>

</ol>

<h1><a name="_Toc14422"></a>7      Demos</h1>

<strong>This project will be demoed. </strong>Demos are designed to make sure that you understand the content of the project and related topics. They may include technical and/or conceptual questions.

<ul>

 <li>Sign up for a demo time slot via Canvas <strong>before </strong>the beginning of the first demo slot. This is the only way you can ensure you will have a slot.</li>

 <li>If you cannot attend any of the predetermined demo time slots, e-mail the Head TA <strong>before </strong>the beginning of the first demo slot.</li>

 <li>If you know you are going to miss your demo, you can cancel your slot on Canvas with no penalty. However, you are <strong>not </strong>guaranteed another time slot. You cannot cancel your demo within 24 hours or else it will be counted as a missed demo.</li>

 <li>Your overall project score will be ((autograder_score * 0.5) + (demo_score * 0.5)), meaning if you received a 90% on your autograder, but a 30% on the demo you would receive an overall score of 60%. <strong>If you miss your demo you will not receive any of these points and the maximum you can receive on the project is 50%.</strong></li>

 <li>You will be able to makeup one of your demos at the end of the semester for half credit.</li>

</ul>