Phase1

Using GDB debugger we can open sheldon1.

![](https://user-images.githubusercontent.com/43363015/78663566-f881e280-78ef-11ea-9fe0-3f1a7ec04e6a.PNG)

Use gdb's disassemble command to get all available assembler code for function in sheldon1.
But this time we can use disas phase_2.

![](https://user-images.githubusercontent.com/43363015/78664041-d63c9480-78f0-11ea-93ca-5bc11cfed876.PNG)

The first thing to notice here is that <phase_2> is calling a function by the name of <read_six_numbers>.
It looks to make sure the stdin input has six integers in it, each separated by a space.
our answer takes the format a b c d e f where a-f are integers.

set a breakpoint on phase_2.

![](https://user-images.githubusercontent.com/43363015/78665025-ca51d200-78f2-11ea-8a00-4baf03105d91.PNG)

 Using 'r' we can run the program in gdb,
 Then we can enter six random, distinct intergers before we stop through the phase.
 
![](https://user-images.githubusercontent.com/43363015/78665621-bb1f5400-78f3-11ea-8339-bf539ab38937.PNG)

Now that we are stopped at our breakpoint.

Let’s run disas phase_2 to take a look at the assembly code.

![](https://user-images.githubusercontent.com/43363015/78666641-41886580-78f5-11ea-86c0-1266ef723ab8.PNG)

Disassemble the function using disas

![](https://user-images.githubusercontent.com/43363015/78696180-b9b65180-791c-11ea-926f-8d199be4c6e7.PNG)

First comparison is compared with number 1 in the assembly code it represent as bellow,

cmp DWORD PTR [ebp-0x18], 0x1 =>> we can guess that the first number is " 1 ".

The second thing to note is that the function is looping over its input. 
After %eax is compared to (%esi, %ebx, 4) at <+54>, %ebx gets incremented and, as long as its less than 5, 
the function jumps back to above the comparison so that it can do it again.
This means that our input integers will probably be a pattern of some sort, where <+46> is where the math that increments the pattern happens.

![](https://user-images.githubusercontent.com/43363015/78696434-0c900900-791d-11ea-9b52-a7cc4fb73a78.PNG)

Once we’ve arrived at the comparison statement, we can use the i r command to see the contents of our registers.
%eax, which is the register to which our value is being compared, is equal to 2. 
Therefore, the second integer in our passphrase should be 2.

![](https://user-images.githubusercontent.com/43363015/78696768-7c9e8f00-791d-11ea-8e1c-5d8d3677284d.PNG)

The simplest way to solve this level completely is by continuing to step through the code, 
seeing what %eax is equal to after each iteration. Next you’ll find 6, then 24, then 120 followed by 720. 

v[0] = 1  
v[i] = (i+i) * v[i-1]  

Either way, the second passphrase ends up being 1 2 6 24 120 720.

![](https://user-images.githubusercontent.com/43363015/78697326-43b2ea00-791e-11ea-82e5-f52170e2d644.PNG)

key =>> 1 2 6 24 120 720
















