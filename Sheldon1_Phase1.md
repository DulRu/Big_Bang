Analysis

Phase 1 

When we test our inputs using debugger.

Using GDB debugger we can open sheldon1.

![](https://user-images.githubusercontent.com/43363015/77848292-64be6100-71e1-11ea-86f1-6c5011b802d8.jpg)

We need to check the available function. Then we can check the main function.

![](https://user-images.githubusercontent.com/43363015/77848294-6720bb00-71e1-11ea-891b-add8b59b470f.png)

When the program runs we can enter the pass phrase and grant access to the next phase.
The program calls the relevant phase function upon the correct phase phrase.

![](https://user-images.githubusercontent.com/43363015/77848298-6c7e0580-71e1-11ea-9713-8b82348e0919.png)

Then check the phase_1 function.

![](https://user-images.githubusercontent.com/43363015/77848307-743daa00-71e1-11ea-9403-d6517c134e0f.png)

We have a fixed address pushed to the memory and then we got a TEST instruction. $0x80497c0
In that memory address we can print out the first 30 characters.

![](https://user-images.githubusercontent.com/43363015/77848362-caaae880-71e1-11ea-9512-537a4417a9e9.png)

Then we can use gdb to run the program to get the string and therefore we can test this is the right phrase.

![](https://user-images.githubusercontent.com/43363015/77848364-ce3e6f80-71e1-11ea-9ce4-3dc308546a69.png)

![](https://user-images.githubusercontent.com/43363015/77848366-d0083300-71e1-11ea-8c55-6d417555bb6d.png)

-----------------------------------------------------------------------------------------------------------------

![](https://user-images.githubusercontent.com/43363015/77848832-317dd100-71e5-11ea-9457-b4af959b11c0.PNG)

