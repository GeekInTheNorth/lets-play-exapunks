# 10 Unknown Network 1

In this mission, the task is to locate and steal a file from an unknown position on a network that branches out by two at each node.

| Solution | Cycles | Size | Activity | EXA Modules|
|:---------|-------:|-----:|---------:|------------|
| 01       |     57 |   46 |       45 | [XA](#01-xa) [XB](#01-xb) |
| 02       |     35 |   17 |       27 | [XA](#02-xa) |
| 03       |     24 |   38 |       28 | [XA](#03-xa) [XB](#03-xb) |
| 04       |     25 |   21 |       27 | [XA](#04-xa) |

![Solution 02](EXAPUNKS%20-%20UNKNOWN%20NETWORK%201.gif "Solution 02")

## Solution 01

### 01 XA

```
MARK START
COPY M X
TEST X = 8
TJMP STEAL
REPL START

LINK 800

NOTE DEC1
TEST X > 3
FJMP RIGHT1

NOTE LEFT1
LINK 800
SUBI X 4 X
JUMP DEC2

MARK RIGHT1
LINK 801

MARK DEC2
TEST X > 1
FJMP RIGHT2

NOTE LEFT2
LINK 800
SUBI X 2 X
JUMP DEC3

MARK RIGHT2
LINK 801

MARK DEC3
TEST X > 0
FJMP RIGHT3

NOTE LEFT3
LINK 800
JUMP STEAL

MARK RIGHT3
LINK 801

MARK STEAL
KILL
GRAB 276
LINK -1
LINK -1
LINK -1
LINK -1
DROP
HALT
```

### 01 XB

```
@REP 9
COPY @{0,1} M
@END
```

## Solution 02

### 02 XA

```
MARK START
ADDI X 1 X
TEST X = 5
TJMP END
REPL RIGHT

NOTE LEFT
LINK 800
JUMP START

MARK RIGHT
LINK 801
JUMP START

MARK END
KILL
GRAB 276
@REP 4
LINK -1
@END
```

## Solution 03

By switching our positional tracking from counting up in `X` to counting down in `T`, we can remove the `TEST` calls and reduce the number of cycles.  `TJMP` and `FJMP` test the zero or non-zero state of T and this quick can be exploited.

Duplicating the EXA and navigating to the next tier before reverting to `REPL` commands also allows us to streamline by one more cycle.

### 03 XA

```
LINK 800
LINK 800
COPY 3 T

MARK START
SUBI T 1 T
FJMP END
REPL RIGHT

NOTE LEFT
LINK 800
JUMP START

MARK RIGHT
LINK 801
JUMP START

MARK END
KILL
GRAB 276
@REP 4
LINK -1
@END
```

### 03 XB

```
LINK 800
LINK 801
COPY 3 T

MARK START
SUBI T 1 T
FJMP END
REPL RIGHT

NOTE LEFT
LINK 800
JUMP START

MARK RIGHT
LINK 801
JUMP START

MARK END
KILL
GRAB 276
@REP 4
LINK -1
@END
```

## Solution 04

### 04 XA

```
LINK 800
COPY 3 T
REPL RIGHT
LINK 800

MARK START
SUBI T 1 T
FJMP END
REPL RIGHT

MARK LEFT
LINK 800
JUMP START

MARK RIGHT
LINK 801
JUMP START

MARK END
KILL
GRAB 276
@REP 4
LINK -1
@END
```