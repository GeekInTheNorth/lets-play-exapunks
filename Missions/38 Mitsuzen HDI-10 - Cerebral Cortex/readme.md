# 38 Mitsuzen HDI-10 - Cerebral Cortex

The main character has the Phage which is causing their body to degrade. In this mission, you are using the EXA bots to clone your central cortex so that it can be uploaded electronically to live on as part of EMBER-2's system.  The host name and #NERV value must be copied into a new file in order of host name.

[XA](01-XA.exa) is responsible for navigating the Cerebral Cortex and leaving a replicated EXA in each host node that can later be used to send the information back to the core.  Since the Cerebral Cortex does not have a static regular structure, there is no set path for navigating.  Therefore there is a lot of replication and failed navigations happening.  Logic is in place to make sure navigation replicants are not spawned to go backward.

[XB](01-XB.exa) is responsible for reading and sorting the key value pairs of host names and #NERV values. Due to each Central Cortex potentially having a different number of paired values, replication, timers and kill commands are required to process these actions in stages.

| Solution | Cycles | Size | Activity | EXA Modules|
|:---------|-------:|-----:|---------:|------------|
| 01       |   3126 |   48 |      304 | [XA](01-XA.exa) [XB](01-XB.exa) |

![Solution 01](EXAPUNKS%20-%20Mitsuzen%20HDI-10.gif "Solution 01")