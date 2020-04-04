# 13 Equity First Bank

In this mission, the hacker is telling all cash machines to dispense all of their cash without triggering an alert by attempting to dispense cash when there is none left.  At least five out of seven cash machines will be functional at any given time.

Cycles are kept lower by cloning the EXA unit and operating on all machines at once.  An attempt to serve more money at once was made, but the #DISP register only triggers on individual calls of 20. 

Solution 2 is a minor refactoring to reduce code size, but does increase the number of cycles slightly.  The use of @REP does not reduce compiled lines of code measured by Size, but does reduce the readable lines of code which is not measured.

Solution 3 splits the cash dispensing loops into two.  One loop checks the remaining cash is above a set threshold and then uses the @REP command to maximise the number of dispense calls that don't need to perform an individual check against #CASH. This has a distinct reduction on the number of cycles required.

| Solution | Cycles | Size | Activity | EXA Modules|
|:---------|-------:|-----:|---------:|------------|
| 01       |   3012 |   23 |       10 | [XA](01-XA.exa) |
| 02       |   3024 |   17 |       10 | [XA](02-XA.exa) |
| 03       |   1162 |   50 |       10 | [XA](03-XA.exa) |

![Solution 03](EXAPUNKS%20-%20Equity%20First%20Bank.gif "Solution 03")
