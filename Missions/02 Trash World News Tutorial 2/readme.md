# 02 Trash World News Tutorial 2

In this mission, the hacker has to access a file containing 4 numbers and perform the following formula and save it to the end of the file before moving it to the outbox:

E = ((A + B) * C) - D

| Solution | Cycles | Size | Activity | EXA Modules|
|:---------|-------:|-----:|---------:|------------|
| 01       |      8 |    8 |        2 | [XA](#01-xa) |
| 02       |      7 |    7 |        2 | [XA](#02-xa) |
| 03       |      7 |    6 |        2 | [XA](#03-xa) |

![Solution 03](EXAPUNKS%20-%20TRASH%20WORLD%20NEWS.gif "Solution 03")

## Solution 01

### 01 XA
```
LINK 800
GRAB 200
COPY F X
ADDI X F X
MULI X F X
SUBI X F F
LINK 800
HALT
```

## Solution 02

### 02 XA
```
LINK 800
GRAB 200
ADDI F F X
MULI X F X
SUBI X F F
LINK 800
HALT
```

## Solution 03

### 03 XA
```
LINK 800
GRAB 200
ADDI F F X
MULI X F X
SUBI X F F
LINK 800
```