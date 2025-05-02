# 07 Peanut Blast

In this mission, the task is to remove peanuts from a randomly ordered list of ingredients for the Peanut Blast bar to cause outrage in fans of the bar.  Cycles in this case is the maximum required to achieve the goal.

| Solution | Cycles | Size | Activity | EXA Modules|
|:---------|-------:|-----:|---------:|------------|
| 01       |     43 |   28 |        5 | [XA](#01-xa) [XB](#01-xb) |
| 02       |     32 |   13 |        2 | [XA](#02-xa) |
| 03       |     31 |   11 |        2 | [XA](#03-xa) |

![Solution 03](EXAPUNKS%20-%20Last%20Stop%20SNAXNET.gif "Solution 03")

## Solution 01

### 01 XA

```
GRAB 300
COPY F X
@REP 11
COPY X M
@END
HALT
```

### 01 XB

```
LINK 800
LINK 800
GRAB 237
MARK LOOP
COPY F X
TEST X = M
FJMP LOOP
SEEK -1
VOID F
DROP
LINK -1
LINK -1
KILL
HALT
```

## Solution 02

### 02 XA

```
GRAB 300
COPY F X
DROP

LINK 800
LINK 800

GRAB 237
MARK LOOP
TEST F = X
FJMP LOOP
SEEK -1
VOID F
DROP
HALT
```

## Solution 02

### 03 XA

```
GRAB 300
COPY F X
DROP

LINK 800
LINK 800

GRAB 237
MARK LOOP
TEST F = X
FJMP LOOP
SEEK -1
VOID F
```