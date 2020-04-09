# 18 Digital Library Project

In this mission, the hacker needs to copy the content of five files without leaving a trace on the server. Each file will be contained in a different folder with the hacker's host containing a file detailing the five file references.

Solution 01 searches for each file in turn and copies the data over the global channel to where original exa unit writes the file.  Solution 02 searches for the files in parallel, opting to copy the file locally before manually moving back over the folder structure to the host.  This comes at an Activity cost while drastically reducing the number of cycles it takes to complete the mission.

| Solution | Cycles | Size | Activity | EXA Modules|
|:---------|-------:|-----:|---------:|------------|
| 01       |   1485 |   34 |       37 | [XA](01-XA.exa) |
| 02       |    345 |   37 |       87 | [XA](02-XA.exa) |

![Solution 02](EXAPUNKS%20-%20Digital%20Library%20Project.gif "Solution 02")
