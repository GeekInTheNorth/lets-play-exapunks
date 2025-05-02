# 04 Trash World News Tutorial 4

In this mission, the hacker has to access a file containing 1 number and write a new file in the containing 2 values and copy them in the reverse order to a new file in the outbox before destroying the original.

With the REPL command it's possible to do this with one EXA module with an increase in size by 1 and a reduction in activity by 1. But the point is to learn how to use multiple EXA units.

Better size scores are achievable with a single EXA with optimized Cycles.

| Solution | Cycles | Size | Activity | EXA Modules|
|:---------|-------:|-----:|---------:|------------|
| 01       |    404 |   13 |        2 | [XA](#01-xa) |
| 02       |    307 |   10 |        2 | [XA](#02-xa) |

![Solution 01](EXAPUNKS%20-%20TRASH%20WORLD%20NEWS.gif "Solution 01")

## Solution 01

### 01 XA

```
LINK 800
GRAB 200
COPY F X
WIPE
LINK 800
MAKE
COPY X F
MARK LOOP
SUBI X 1 X
COPY X F
TEST X = 0
FJMP LOOP
HALT
```

## Solution 02

### 02 XA

```
LINK 800
GRAB 200
ADDI F 1 T
WIPE
LINK 800
MAKE
MARK LOOP
SUBI T 1 T
COPY T F
TJMP LOOP
```