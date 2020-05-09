# 36 Unknown Network 2

In this mission, the task is to navigate a known network structure and steal all files from the central computer and to erase all enemy EXA units on the other network.  There ar five files with registries somewhere between 200 and 299.

Solution 01 navigates to the central computer and sequentially spawns 100 EXA units that attempt to steal the feels. To optimise the number of cycles for solution 02, I have maximised the original EXA size. Upon reaching the central computer, [XA](02-XA.exa) replicates itself to create 5 spawners that each sequentially spawn 20 EXA units that attempt to steal the files.  The central computer does not reach EXA capacity as an EXA terminates on a failed command such as grabbing a non-existent file.

| Solution | Cycles | Size | Activity | EXA Modules|
|:---------|-------:|-----:|---------:|------------|
| 01       |    424 |   39 |       53 | [XA](01-XA.exa) |
| 02       |    108 |   75 |       53 | [XA](02-XA.exa) |

![Solution 02](EXAPUNKS%20-%20UNKNOWN%20NETWORK%202.gif "Solution 02")