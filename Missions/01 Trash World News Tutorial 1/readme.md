# 01 Trash World News Tutorial 1

In this mission, the hacker is moving a file from the inbox to the outbox.

| Solution | Cycles | Size | Activity | EXA Modules|
|:---------|-------:|-----:|---------:|------------|
| 01       |      4 |    4 |        2 | [XA](#01-xa) |
| 02       |      4 |    3 |        2 | [XA](#02-xa) |

![Solution 02](EXAPUNKS%20-%20TRASH%20WORLD%20NEWS.gif "Solution 02")

## Solution 01

### 01 XA
```
LINK 800
GRAB 200
LINK 800
HALT
```

## Solution 02

This solution improves over solution 1 by dropping the defunct `HALT` command.

### 02 XA
```
LINK 800
GRAB 200
LINK 800
```