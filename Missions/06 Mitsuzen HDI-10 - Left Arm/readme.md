# 06 Mitsuzen HDI-10 - Left Arm

The main character has the Phage which is causing their body to degrade. In this mission, you are using the EXA bots to maintain the nerv connection between your central nervous system and your left arm. The Exa bots must efficiently transfer signals from the former to the later while compensating for the failing nervous system sending signals outside of the -120 to 50 range.

| Solution | Cycles | Size | Activity | EXA Modules|
|:---------|-------:|-----:|---------:|------------|
| 01       |    187 |   22 |        6 | [XA](#01-xa) [XB](#01-xb) |
| 02       |     87 |   16 |        6 | [XA](#02-xa) [XB](#02-xb) |
| 03       |     67 |   17 |        6 | [XA](#03-xa) [XB](#03-xb) |
| 04       |     46 |   21 |        6 | [XA](#04-xa) [XB](#04-xb) |

![Solution 04](EXAPUNKS%20-%20Mitsuzen%20HDI-10.gif "Solution 04")

## Solution 01

### 01 XA

```
LINK 800
MARK READ
COPY #NERV X
TEST X > 50
FJMP UPPER
COPY 50 X
MARK UPPER
COPY X M
JUMP READ
```

### 01 XB

```
LINK 800
LINK 1
LINK 1
LINK 1
LINK 1
MARK READ
COPY M X
TEST X < -120
FJMP LOWER
COPY -120 X
MARK LOWER
COPY X #NERV
JUMP READ
```

## Solution 02

### 02 XA

```
LINK 800
MARK READ
ADDI 9949 #NERV X
REPL READ
SUBI X 9949 X
SUBI X 9879 X
ADDI X 9879 M
HALT
```

### 02 XB

```
LINK 800
LINK 1
LINK 1
LINK 1
LINK 1
MARK READ
COPY M #NERV
JUMP READ
```

## Solution 03

### 03 XA

```
LINK 800
MARK READ
ADDI 9949 #NERV X
REPL READ
SUBI X 9949 M
HALT
```

### 03 XB

```
LINK 800
LINK 1
LINK 1
LINK 1
LINK 1
MARK READ
SUBI M 9879 X
REPL READ
ADDI X 9879 #NERV
HALT
```

## Solution 04

### 04 XA

```
LINK 800
REPL DELAY1
REPL DELAY1

MARK READ
ADDI #NERV 9949 X
SUBI X 9949 M
JUMP READ

MARK DELAY1
NOOP
JUMP READ
```

### 04 XB

```
LINK 800
@REP 4
LINK 1
@END
REPL READ
REPL READ

MARK READ
SUBI M 9879 X
ADDI X 9879 #NERV
JUMP READ
```