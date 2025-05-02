# 05 Euclid's Pizza

In this mission the hacker is trying to get a free pizza by adding their order to the order queue of Euclid's Pizzas.

| Solution | Cycles | Size | Activity | EXA Modules|
|:---------|-------:|-----:|---------:|------------|
| 01       |     31 |   22 |        1 | [XA](#01-xa) [XB](01-xb) |
| 02       |     14 |   18 |        1 | [XA](#02-xa) [XB](#02-xb) |
| 03       |     13 |   14 |        1 | [XA](#02-xa) [XB](#02-xb) |

![Solution 02](EXAPUNKS%20-%20Euclid%27s%20Pizza.gif "Solution 02")

## Solution 01

### 01 XA

```
NOOP
NOOP
GRAB 300
COPY 5 X
MARK LOOP
COPY F M
SUBI X 1 X
TEST X = 0
FJMP LOOP
WIPE
HALT
```

### 01 XB

```
LINK 800
GRAB 200
SEEK 9999
COPY 5 X
MARK LOOP
COPY M F
SUBI X 1 X
TEST X = 0
FJMP LOOP
DROP
HALT
```

## Solution 02

### 02 XA

```
GRAB 300
@REP 5
COPY F M
@END
WIPE
HALT
```

### 02 XB

```
LINK 800
GRAB 200
SEEK 9999
@REP 5
COPY M F
@END
DROP
HALT
```

## Solution 03

This solution builds on solution 02 by removing defunct commands.  EXAs self terminate when they run out of commands to execute.  So the DROP and HALT commands are not needed.

### 03 XA

```
GRAB 300
@REP 5
COPY F M
@END
```

### 03 XB

```
LINK 800
GRAB 200
SEEK 9999
@REP 5
COPY M F
@END
```

## Steam Achievement

Steam Achievement - PIZZA_PARTY.  This EXA will cause the mission to fail as soon as the first call to the lights #POWR register.  This simply toggles the lights on and off repeatidly.

```
LINK 800
LINK 800
LINK 805
COPY 100 T
MARK RAVE_LOOP
MODI T 2 X
COPY X #POWR
SUBI T 1 T
TJMP RAVE_LOOP
```