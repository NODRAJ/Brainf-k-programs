Takes 2 different bytes as input and outputs the smallest: 

`> ,`

`> ,`

`[<<< + >> - > - [<] >>]` Decrements both values until one of them is 0, a count is kept of how many times the values have been decreased

`<< +`

`[<]`

`< .` The count is output

-----------------------------------------------------------------------------------------------------------------------------------------
Takes 4 different bytes as input and outputs those bytes in ascending order:

`>>>>>> ,`

`> ,`

`> ,`

`> ,`

`>>>>> ++++`

`[`

`[<<<<< - < - < - < - << + >> [>] >>>>]` Decrements all values until one of them is 0, a count is kept of how many times the values have been decreased

`<<<<< [<]`

`< .` The count is output

`>>>>>>>>>> -`

`]`

-----------------------------------------------------------------------------------------------------------------------------------------
Takes up to 255 different bytes as input and outputs those bytes in ascending order:

`> ,`

`[`

`[<] < + >> [>] , ]`

`> +`

`>>> +`

`<<<<< [<] <`

`[`

`>> [>]`

`>>>> [+ <<<<< [- <] > [>] > [>] >>]` Decrements all values until one of them is 0, a count is kept of how many times the values have been decreased

`>> - . +` The count is output

`<<<<< [<] -`

`[<] < -`

`]`
Link to showcase video:

https://www.youtube.com/watch?v=b3ADj_XEAfc

-----------------------------------------------------------------------------------------------------------------------------------------
Takes any byte N as input then takes any sequence of bytes as input and outputs that sequence N times:

`++++++++++ > ,`

`>> ,` Byte N input

`[> ,]` Sequence of bytes input (value of 0 denotes the end of the sequence)

`< [<]` Pointer is moved to the start of the sequence

`< [- >> [. >] < [<] << . >]` Sequence is output N times

-----------------------------------------------------------------------------------------------------------------------------------------
Takes 2 bytes as input and outputs the sum of those bytes (most of the complexity comes from summing numbers with a total of 10 or greater)

`> ++++++++++++++++++++++++++++++++++++++++++++++++` Value of 48 is stored as this is the offset between actual values and ascii numbers (i.e. ascii 1 = byte value 49 = actual value (1) + 48)

`>>> ,`

`>> ,`

`<<<<< [- >>> - >> - <<<<<]` Reduces byte values down to actual values to make them easier to process (not necessary for adding 2 numbers but could help when expanding the program to adding more values)

`>>>>> [- < + < + >> ]` Adds the actual values together

`< [-]`

`<< ++++++++++` Stores the value 10 to check if the sum is 10 or greater

`>>>> ------------------------------------------------` Decrements the value that will be next to the counter created below to prevent any other characters being printed when the sum is less than 10

`<<<< [- > - >> + <<< [>] <<]` Decrements the stored 10 and the sum of the actual values until one is 0. A counter is made to check the number of times the values have been decremented

`> [>]`

`> +`

`<< [>]`

`>> ++++++++++++++++++++++++++++++++++++++++++++++++ .` If the 10 was 0 (sum of actual values is greater than or equal to 10) the pointer will now be where the 10 was (which will now be an ascii 1), otherwise it will be on the counter value created above

`> ++++++++++++++++++++++++++++++++++++++++++++++++ .` If the 10 was 0 the pointer will now be on the value next to where the 10 was (which will be the remainder of dividing the sum by 10), otherwise it will be next to the counter value created above which was decremented earlier to offset the increase (causing the value to be 0 which doesn't print a character).
