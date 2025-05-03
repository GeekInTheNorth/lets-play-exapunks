# 09 SFCTA Highway Sign #4902

In this mission, the task is to hack a motorway sign and change it's message.  The sign takes three numbers per letter (row, column, character) on a board that is 9 x 3 characters in size. The hacker has a file which contains only the digits to be displayed and must correctly reset the board and set each value.

| Solution | Cycles | Size | Activity | EXA Modules|
|:---------|-------:|-----:|---------:|------------|
| 01       |    355 |   33 |        1 | [XA](#01-xa) [XB](#01-xb) |
| 02       |    250 |   33 |        3 | [XA](#02-xa) [XB](#02-xb) |
| 03       |    169 |   28 |        1 | [XA](#03-xa) |
| 04       |    167 |   12 |        1 | [XA](#04-xa) |

![Solution 04](EXAPUNKS%20-%20SFCTA%20Highway%20Sign%20%234902.gif "Solution 04")

## Solution 01

### 01 XA

```
LINK 800
COPY 0 #CLRS
MARK READ
COPY M #DATA
ADDI X 1 X
TEST X = 81
FJMP READ
HALT
```

### 01 XB

```
GRAB 300

MARK READ1
COPY 0 M
COPY X M
COPY F M
ADDI X 1 X
TEST X = 9
FJMP READ1
COPY 0 X

MARK READ2
COPY 1 M
COPY X M
COPY F M
ADDI X 1 X
TEST X = 9
FJMP READ2
COPY 0 X

MARK READ3
COPY 2 M
COPY X M
COPY F M
ADDI X 1 X
TEST X = 9
FJMP READ3

HALT
```

## Solution 02

### 02 XA

```
LINK 800
COPY 0 #CLRS
MARK READ
COPY M #DATA
JUMP READ
```

### 02 XB

```
GRAB 300

MARK READ1
COPY 0 M
COPY X M
COPY F M
ADDI X 1 X
TEST X = 9
FJMP READ1
COPY 0 X

MARK READ2
COPY 1 M
COPY X M
COPY F M
ADDI X 1 X
TEST X = 9
FJMP READ2
COPY 0 X

MARK READ3
COPY 2 M
COPY X M
COPY F M
ADDI X 1 X
TEST X = 9
FJMP READ3

DROP
LINK 800
KILL
HALT
```

## Solution 03

### 03 XA

```
GRAB 300
LINK 800

COPY 0 #CLRS
MARK READ1
COPY 0 #DATA
COPY X #DATA
COPY F #DATA
ADDI X 1 X
TEST X = 9
FJMP READ1
COPY 0 X

MARK READ2
COPY 1 #DATA
COPY X #DATA
COPY F #DATA
ADDI X 1 X
TEST X = 9
FJMP READ2
COPY 0 X

MARK READ3
COPY 2 #DATA
COPY X #DATA
COPY F #DATA
ADDI X 1 X
TEST X = 9
FJMP READ3

WIPE
HALT
```

## Solution 04

Solution 04 is almost the same as Solution 03, but at less than half the lines of code due to using the following two commands for the first time.

| Function | Action |
|----------|--------|
| DIVI A B C | Divides A by B and outputs the remainder to C |
| MODI A B C | Divides A by B and outputs the whole number to C |

### 04 XA

```
GRAB 300
LINK 800

COPY 0 #CLRS
MARK READ
DIVI X 9 #DATA
MODI X 9 #DATA
COPY F #DATA
ADDI X 1 X
TEST X = 27
FJMP READ

WIPE
HALT
```