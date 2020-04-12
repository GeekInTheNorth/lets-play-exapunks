# 21 Valhalla

This is a hacker battle.  There are 9 nodes, every time the hacker writes to the CTRL register of a node, they take control of it. Points are scored for controlling more nodes than the opponent, points are lost for every kill command that is issued.  Only 10 EXA units can exist per hacker at any given time.

This solution works by keeping one EXA in the host so that it cannot be taken out.  This EXA continually spawns new EXA units which navigate in alternate directions writing to all the registers. 

This is mission is re-runnable against the solutions made by Steam Friends. This succeeded in defeating the AI opponent in all scenarios.

| Solution | Score | Cycles | Size | Activity | EXA Modules|
|:---------|------:|-------:|-----:|---------:|------------|
| 01       |    85 |    100 |   12 |        - | [XA](01-XA.exa) |

![Solution 01](EXAPUNKS%20-%20Valhalla.gif "Solution 01")