# 10 UC Berkley

In this mission, the job is to extract a specific file out of a backup tape.  files contained in the backup tape are listed at the end of the tape in a three value format: 

- Filename
- Start Position
- File Size

Due to the limited number of variables that can be held by a single EXA unit, key information is tracked in different EXA units. The EXA saving the file being responsible for tracking remaining file size and communicating it back to the EXA that is seeking and reading the file.

| Solution | Cycles | Size | Activity | EXA Modules|
|:---------|-------:|-----:|---------:|------------|
| 01       |    176 |   38 |        7 | [XA](#01-xa) [XB](#01-xb) |
| 02       |    127 |   37 |        7 | [XA](#02-xa) [XB](#02-xb) |
| 03       |    121 |   46 |       13 | [XA](#02-xa) [XB](#02-xb) |

![Solution 01](EXAPUNKS%20-%20UC%20Berkeley.gif "Solution 01")

## Solution 01

### 01 XA

```
NOTE WAIT FOR TAPE NAME
COPY M X

MARK NAVIGATE
LINK 800
HOST T
TEST T = X
FJMP NAVIGATE

NOTE GRAB TAPE
GRAB 200

NOTE FIND FILE DATA
COPY M X
SEEK 9999
SEEK -3
MARK FILELOOP
TEST F = X
TJMP FILESIZE
SEEK -4
JUMP FILELOOP

NOTE GET FILE SIZE
MARK FILESIZE
COPY F X
COPY F M

NOTE READ FILE
SEEK -9999
SEEK X
MARK CLONE
COPY F M
TEST M = 0
FJMP CLONE
HALT
```

### 01 XB

```
NOTE TRANSMIT FILE INFO
GRAB 300
COPY F M
COPY F M
WIPE

MAKE

NOTE AWAIT LENGTH
COPY M X
MARK COPY
COPY M F
SUBI X 1 X
COPY X M
TEST X = 0
FJMP COPY

HALT
```

## Solution 02

Coming back to the game in 2025 I improved the cycle times by leveraging the fact TJMP always performing a positive action with a value over 1 and counting down the file size loop in the T register.  I've then removed redundant calls to HALT.  The final improvement was to add a second LINK call to the initial loop to avoid pointless tests in the connector systems.

### 02 XA

```
LINK 800

NOTE WAIT FOR TAPE NAME
COPY M X

MARK NAVIGATE
LINK 800
LINK 800
HOST T
TEST T = X
FJMP NAVIGATE

NOTE GRAB TAPE
GRAB 200

NOTE FIND FILE DATA
COPY M X
SEEK 9999
SEEK -3
MARK FILELOOP
TEST F = X
TJMP FILESIZE
SEEK -4
JUMP FILELOOP

NOTE GET FILE SIZE
MARK FILESIZE
COPY F X
COPY F T
COPY T M

NOTE READ FILE
SEEK -9999
SEEK X
MARK CLONE
COPY F M
SUBI T 1 T
TJMP CLONE
```

### 02 XB

```
NOTE TRANSMIT FILE INFO
GRAB 300
COPY F M
COPY F M
WIPE

MAKE

NOTE AWAIT LENGTH
COPY M T
MARK COPY
COPY M F
SUBI T 1 T
TJMP COPY
```

## Solution 03

This solution improves on cycle time some more at the expense of size.  By using the REPL command, cloned EXAs can already be moving into the additional tape machines while tests are being performed in earlier tapes.  Recognising that the tapes always contain 126 data entries before the reference entries allowed me to optimize navigating file 200 to find the correct reference entry.

### 03 XA

```
LINK 800

NOTE WAIT FOR TAPE NAME
COPY M X
REPL NAVIGATE3
REPL NAVIGATE2
JUMP NAVIGATE1

MARK NAVIGATE3
LINK 800
LINK 800

MARK NAVIGATE2
LINK 800
LINK 800

MARK NAVIGATE1
LINK 800
LINK 800

NOTE HOST CHECK
HOST T
TEST T = X
FJMP ENDER

NOTE GRAB TAPE
GRAB 200

NOTE FIND FILE DATA
COPY M X
SEEK 126
MARK FILELOOP
TEST F = X
TJMP FILESIZE
SEEK 2
JUMP FILELOOP

NOTE GET FILE SIZE
MARK FILESIZE
COPY F X
COPY F T
COPY T M

NOTE READ FILE
SEEK -9999
SEEK X
MARK CLONE
COPY F M
SUBI T 1 T
TJMP CLONE

MARK ENDER
```

### 03 XB

```
NOTE TRANSMIT FILE INFO
GRAB 300
COPY F M
COPY F M
WIPE

MAKE

NOTE AWAIT LENGTH
COPY M T
MARK COPY
COPY M F
SUBI T 1 T
TJMP COPY
```