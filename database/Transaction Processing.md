#database #transaction
### Date 03/07/2026
#### Transaction Models till 4.5
Gives a theoretical treatment on modeling the transaction as a state machine. Transactions when started, dont start again. End states: Abort/Committed. In practice, Aborted could also be user driven or system driven.

The section talks about flat transactions.

One interesting thing I need to read more and explore is the save points. Do any production DBs do transaction checkpointing (save points)?
