# 09 SFCTA Highway Sign #4902

In this mission, the task is to hack a motorway sign and change it's message.  The sign takes three numbers per letter (row, column, character) on a board that is 9 x 3 characters in size. The hacker has a file which contains only the digits to be displayed and must correctly reset the board and set each value.

| Solution | Cycles | Size | Activity | EXA Modules|
|:---------|-------:|-----:|---------:|------------|
| 01       |    355 |   33 |        1 | [XA](01-XA.exa) [XB](01-XB.exa) |
| 02       |    250 |   33 |        3 | [XA](02-XA.exa) [XB](02-XB.exa) |
| 03       |    169 |   28 |        1 | [XA](03-XA.exa) |
| 04       |    167 |   12 |        1 | [XA](04-XA.exa) |

Solution 04 is almost the same as Solution 03, but at less than half the lines of code due to using the following two commands for the first time.

| Function | Action |
|----------|--------|
| DIVI A B C | Divides A by B and outputs the remainder to C |
| MODI A B C | Divides A by B and outputs the whole number to C |

![Solution 04](EXAPUNKS%20-%20SFCTA%20Highway%20Sign%20%234902.gif "Solution 04")