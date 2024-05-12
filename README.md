>## 🌱 Ongoing projects:
>### STM32H7B0_CMSIS
> A Hardware Abstraction Layer (HAL) library for the STM32H7B0
>### Keyboard
> A Keyboard built on the STM32H7B0VBT6 including:
> * Password manager
> * 2FA code generator
> * Macros / Automated functions
> * able design to allow other projects to be built on/for this keyboard
>
>#
>## 🌳 Finished projects:
>### STM32F_CMSIS
> <details>
> <summary>
> </summary>
> A Hardware Abstraction Layer (HAL) library for the STM32F family
> </details>
> 
>### Python_PS3
> <details>
> <summary>
> </summary>
> A python package that maps out the PS3 controller for easy use in python
> </details>
> 
>### Car
> <details>
> <summary>
> </summary>
> A Radio Controlled (RC) car built on the STM32F411CEU6. Subprojects:
> * STM32F_CMSIS
> * Python_PS3
> </details>
> 
>### Info_Generator
> <details>
> <summary>
> </summary>
> A python package that can generate a fake identity for burner accounts
> </details>
> 
>### Software_Serial
> <details>
> <summary>
> </summary>
> A software serial project built on the STM32F411CEU6. Subprojects:
> * STM32F_CMSIS
> </details>
>
>### MOS
> <details>
> <summary>
> </summary>
> A very minimal Operating System / Bootloader that can render a 3d object and text.
> </details>
> 
>#
>## 🍃 Future projects:
> ### Chess Bot
> <details>
> <summary>
> </summary>
> A simple Chess Bot from scratch
> </details>
>
> ### Neural Network
> <details>
> <summary>
> </summary>
> A simple Neural Network from scratch
> </details>
>
> ### NES Emulator
> <details>
> <summary>
> </summary>
> A simple NES Emulator from scratch
> </details>
> 
> ### Compiled Functional Programming Language
> <details>
> <summary>
> </summary>
>### Compiled Functional Programming Language
> This idea for a compiled functional programming language came from spending some time in ELM.
> The basic idea is that the language will use some Assembly tricks to accomplish function composition in an efficient way.
>#### The Idea
>> Lets assume we are working with a simple system comprising of only four registers:
>>* AX (Data register A)
>>* PC (Program counter)
>>* SP (Stack pointer)
>>* BP (Stack base pointer)
>>
>> And for our example program we have two functions:
>> ```ASM
>> f:
>> add AX, 2    ; + 2
>> ret
>> 
>> g:
>> shl AX, 1    ; * 2
>> ret
>> ```
>> 
>> Now Lets say we want to compose these functions like so: ```f(g(x))``` normally we accomplish this by doing:
>> ```ASM
>> main:
>> mov AX, 2    ; x = 2
>> call g       ; x *= 2
>> call f       ; x += 2
>> ret          ; x = 6
>> ```
>> 
>> My Idea then is to alter the way call works, call traditionally preforms the following actions:
>>1. Push PC to the stack       (saving pointer to instruction after call)
>>2. Set PC to the new function (jumping to the function code)
>>
>> My call procedure (with example):
>>1. Push PC to the stack       (saving pointer to instruction after call)
>>2. Push pointer to ```f(x)``` to the stack
>>3. Jump to ```g(x)```
>>
>> The following (pseudo) code is used:
>> ```Python
>> def main():
>>      x = 2
>>      f(g(x))
>>      return
>> ```
>> Compiling into:
>> ```ASM
>> main:
>> mov AX, 2            ; x = 2
>> composite_call f, g  ; composite call f(g(x))
>> ret                  ; x = 6
>> ```
>> *The syntax for this programming language will probably be very different. This is an example!*
>>
>>
>> When executing this code the following will happen:
>>1. ```g(x)``` is executed
>>2. when ret (in ```g(x)```) is executed the pointer to ```f(x)``` is loaded into PC
>>3. ```f(x)``` is executed
>>4. when ret (in ```f(x)```) is executed the pointer to ```main``` is loaded into PC and the composite call ends
>>
>> Thereby accomplishing composite call f(g(x)) in an effective and simple way!
>> This can alternatively be done by inlining like the gcc optimizer often does but this is not always an option.
> </details>


<!--
 TODO introduction
-->