# 03 Trash World News Tutorial 3

In this mission, the hacker has to access a file containing 2 values and copy them in the reverse order to a new file in the outbox before destroying the original.

With the REPL command it's possible to do this with one EXA module with an increase in size by 1 and a reduction in activity by 1. But the point is to learn how to use multiple EXA units.

| Solution | Cycles | Size | Activity | EXA Modules|
|:---------|-------:|-----:|---------:|------------|
| 01       |     10 |   14 |        4 | [XA](#01-xa) [XB](#01-xb) |
| 02       |      9 |   13 |        4 | [XA](#02-xa) [XB](#02-xb) [XC](#02-xc) |

![Solution 01](EXAPUNKS%20-%20TRASH%20WORLD%20NEWS.gif "Solution 01")

## Solution 01

### 01 XA

```
LINK 800
LINK 799
GRAB 199
COPY F M
COPY F M
WIPE
HALT
```

### 01 XB

```
LINK 800
LINK 800
MAKE
COPY M X
COPY M F
COPY X F
HALT
```

## Solution 02

### 02 XA

```
LINK 800
LINK 799
GRAB 199
COPY F M
COPY F M
WIPE
```

### 02 XA

```
LINK 800
LINK 800
MAKE
COPY M X
COPY M F
COPY X F
```

### 02 XC

This EXA only exists to trigger a delay and synchronize EXA A and EXA B

```
HALT
```