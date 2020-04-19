# 29 Equity First Bank 2

In this missing, the hacker must copy a new account file and register it with the bank's checking server.  It should then transfer $1 from every other registered checking account into the the new account.  This requires matching credit and debit entries for both accounts for each transaction.

- [XA](01-XA.exa) is responsible for moving the new account and writing credit records.
- [XB](01-XB.exa) is responsible for iterating over each registered account in file 199 and writing a debit entry, registering the new account in file 199 and removing all traces.
- [XC](01-XC.exa) is responsible for transmitting key words for credits and debits

| Solution | Cycles | Size | Activity | EXA Modules|
|:---------|-------:|-----:|---------:|------------|
| 01       |    214 |   51 |        8 | [XA](01-XA.exa) [XB](01-XB.exa) [XC](01-XC.exa) |

![Solution 01](EXAPUNKS%20-%20Equity%20First%20Bank.gif "Solution 01")
