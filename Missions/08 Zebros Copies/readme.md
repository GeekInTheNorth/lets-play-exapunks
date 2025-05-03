# 08 Zebros Copies

In this mission, the task is to zero out a friends debt on the balance file and add a payment to the payments file for the same amount.  For robustness, the code must be able to identify the correct line in the balance file regardless of its order.  Cycles in this case is the maximum required to achieve the goal with the minimum being in brackets.

| Solution | Cycles   | Size | Activity | EXA Modules|
|:---------|---------:|-----:|---------:|------------|
| 01       |      145 |   32 |        4 | [XA](#01-xa) [XB](#01-xb) |
| 02       |       73 |   30 |        4 | [XA](#02-xa) [XB](#02-xb) |
| 03       |       73 |   27 |        4 | [XA](#03-xa) [XB](#03-xb) [XC](#03-xc) |
| 04       |       72 |   31 |        2 | [XA](#03-xa) [XB](#03-xb) |

![Solution 03](EXAPUNKS%20-%20Zebros%20Copies.gif "Solution 03")

## Solution 01

### 01 XA

```
GRAB 300
COPY F X
DROP

LINK 800
GRAB 200
MARK LOOP
TEST F = X
TJMP CLONE
JUMP LOOP

MARK CLONE
SEEK -1
@REP 3
COPY F M
@END
JUMP ERASE

MARK ERASE
SEEK -2
@REP 2
COPY 0 F
@END

HALT
```

### 01 XB

```
LINK 800
LINK 801
COPY #DATE X
LINK -1

GRAB 201
SEEK 9999
COPY X F
@REP 3
COPY M F
@END
DROP
HALT
```

## Solution 02

### 02 XA

```
GRAB 300
COPY F X
DROP

LINK 800
GRAB 200
MARK LOOP
TEST F = X
TJMP PAY
SEEK 2
JUMP LOOP

MARK PAY
COPY X M
COPY F M
COPY F M
SEEK -2
COPY 0 F
COPY 0 F

HALT
```

### 02 XB

```
LINK 800
LINK 801
COPY #DATE X
LINK -1

GRAB 201
SEEK 9999
COPY X F
@REP 3
COPY M F
@END
DROP
HALT
```

## Solution 03

### 03 XA

```
GRAB 300
COPY F X
DROP

LINK 800
GRAB 200
MARK LOOP
TEST F = X
TJMP PAY
SEEK 2
JUMP LOOP

MARK PAY
COPY X M
COPY F M
COPY F M
SEEK -2
COPY 0 F
COPY 0 F
```

### 03 XB

```
LINK 800
LINK 801
COPY #DATE M
```

### 03 XC

```
LINK 800
GRAB 201
SEEK 9999
@REP 4
COPY M F
@END
```

## Solution 04

This solution aims to reduce the activity (number of times an EXA has moved between servers) by using the REPL function which does not trigger an activity.  This does however come at a compromise to the best size but does improve overall cycles slightly.

### 04 XA

```
LINK 800
REPL GETDATE
GRAB 200
COPY M X
MARK LOOP
TEST F = X
TJMP PAY
SEEK 2
JUMP LOOP

MARK PAY
COPY X M
COPY F M
COPY F M
SEEK -2
COPY 0 F
COPY 0 F
HALT

MARK GETDATE
REPL WRITER
LINK 801
COPY #DATE M
HALT

MARK WRITER
GRAB 201
SEEK 9999
@REP 4
COPY M F
@END
```

### 04 XB

```
GRAB 300
COPY F M
```

## Steam Achievement

Steam Achievement - TONER_LOW.  This EXA will cause the mission to fail as soon as soon as the first copy is made. This EXA replicates itself onto each printer and recursively triggers the copy function until there is no toner.

```
NOOP
LINK 800
LINK 800

@REP 4
COPY @{800,1} X
REPL START_COPY
@END
HALT

MARK START_COPY
LINK X
COPY 9000 T
MARK COPY_LOOP
COPY 1 #COPY
SUBI T 1 T
TJMP COPY_LOOP
```