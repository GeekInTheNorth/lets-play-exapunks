# 12 Workhouse

In this mission, the hacker is overwriting an expenses file so that the sum of all values is the same, but no value is more than $75 and the final value is less than or equal to $75.

Minor improvement in solution 2 after identifying that COPY X F overwrites the entry where the cursor is in a file, it does not insert the value.

| Solution | Cycles | Size | Activity | EXA Modules|
|:---------|-------:|-----:|---------:|------------|
| 01       |    579 |   32 |        2 | [XA](#01-xa) |
| 02       |    531 |   28 |        2 | [XA](#02-xa) |
| 03       |    218 |   53 |        3 | [XA](#03-xa) [XB](#03-xb) [XC](#03-xc) |

![Solution 03](EXAPUNKS%20-%20WorkHouse.gif "Solution 03")

## Solution 01

### 01 XA

```
NOTE GET USER
GRAB 300
COPY F X
DROP

LINK 800
GRAB 199
MARK READ
TEST F = X
FJMP READ

NOTE COPY USER DATA
COPY F T
COPY F X
DROP

NOTE CHECK USERS
LINK 799
GRAB X
SEEK 2
COPY F X
MARK READNUMBERS
ADDI X F X
TEST EOF
FJMP READNUMBERS

NOTE RESET
SEEK -9999
SEEK 2
MARK WIPE
VOID F
TEST EOF
FJMP WIPE

NOTE OUTPUT REMAINING
MARK APPEND
COPY 75 F
SUBI X 75 X
TEST X > 75
TJMP APPEND
COPY X F

HALT
```

## Solution 02

### 02 XA

```
NOTE GET USER
GRAB 300
COPY F X
DROP

LINK 800
GRAB 199
MARK READ
TEST F = X
FJMP READ

NOTE COPY USER DATA
COPY F T
COPY F X
DROP

NOTE CHECK USERS
LINK 799
GRAB X
SEEK 2
COPY F X
MARK READNUMBERS
ADDI X F X
TEST EOF
FJMP READNUMBERS

NOTE OVERWRITE VALUES
SEEK -9999
SEEK 2
MARK APPEND
COPY 75 F
SUBI X 75 X
TEST X > 75
TJMP APPEND
COPY X F

HALT
```

## Solution 03

This solution improves on cycle speed by splitting the logic into separate EXA units that travel to different nodes in the network.  Then using DIVI to work out how many times the total amount can be divided by 750, the writes can be done in batches of 10 reducing the number of test lines.  Another tactic is to understand the lowest number of transactions to read in the user's file and then negate the need for testing for the end of the file in those scenarios.

### 03 XA

```
NOTE GET USER
GRAB 300
COPY F M
```

### 03 XB

```
LINK 800
GRAB 199
COPY M X

MARK READ
TEST F = X
SEEK 2
FJMP READ

NOTE COPY USER DATA
SEEK -1
COPY F M
```

### 03 XC

```
LINK 800
LINK 799
GRAB M

NOTE CHECK USERS
SEEK 2
ADDI F F X
@REP 7
ADDI F X X
@END
MARK READNUMBERS
ADDI X F X
TEST EOF
FJMP READNUMBERS

NOTE OVERWRITE VALUES
SEEK -9999
SEEK 2
DIVI X 750 T
MARK APPEND
@REP 10
COPY 75 F
@END
SUBI X 750 X
SUBI T 1 T
TJMP APPEND

DIVI X 75 T
FJMP FINALISE
MARK APPEND2
COPY 75 F
SUBI X 75 X
SUBI T 1 T
TJMP APPEND2
MARK FINALISE
COPY X F
```
