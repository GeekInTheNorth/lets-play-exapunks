# 10 UC Berkley

In this mission, the job is to extract a specific file out of a backup tape.  files contained in the backup tape are listed at the end of the tape in a three value format: 

- Filename
- Start Position
- File Size

Due to the limited number of variables that can be held by a single EXA unit, key information is tracked in different EXA units. The EXA saving the file being responsible for tracking remaining file size and communicating it back to the EXA that is seeking and reading the file.

| Solution | Cycles | Size | Activity | EXA Modules|
|:---------|-------:|-----:|---------:|------------|
| 01       |    176 |   38 |        7 | [XA](01-XA.exa) [XB](01-XB.exa) |

![Solution 01](EXAPUNKS%20-%20UC%20Berkeley.gif "Solution 01")