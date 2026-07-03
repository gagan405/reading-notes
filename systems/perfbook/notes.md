# The Book

Source: [link](https://mirrors.edge.kernel.org/pub/linux/kernel/people/paulmck/perfbook/perfbook.html)

## Ch 3

### Date : 26/12/2025

[3.1.2 - 3.1.6]
* Memory access patterns introduce latency - more random, more the latency. That's why linkedlists suck.
* Atomic operations - done through cacheline flush, multiple CPUs share same pipeline. Introduces latency obviously.
* Memory barriers - to order the instructions. Adds latency, reduces performance.
* Multiple functional units - CPUs usually have multiple FUs of their own - helps with ILP
* HTM - Hardware Txn Memory - mem operations applied like ACID transactions within the CPU.
* Packed wide registers also can do atomic instructions over multiple data units

```
| 8 bits | 8 bits | 8 bits | 8 bits |
```
```c
uint32_t packed;
atomic_compare_exchange(&packed, old, new);
```
* __Thermal Throttling__ - overheated CPUs can reduce the clock frequency. Which means optimizations at micro code level
  to squeeze out every performance juice of every single FU can actually backfire. Gamers do custom cooling with liquid
  nitrogen or aluminium sinks.

### 11/01/2026
[3.1.6 - 3.2.1]
* Cache line ownership and I/O operations are complex in multi-processor systems - expectedly
* Multi-processor systems do similar stuff as software concurrency - flush, lock, readonly etc.
* [Cache-coherency protocols](https://en.wikipedia.org/wiki/List_of_cache_coherency_protocols)  exist to make sure CPUs work with clean and correct expected data. But it also means that a single instruction working with a shared variable can create significant delays due to cache traffic and transactions.
## References
### Hardware Transactional Memory
[1] https://www.steveblackburn.org/pubs/papers/htm-ismm-2021.pdf  
[2] https://www.cs.cmu.edu/afs/cs/academic/class/15418-s12/www/lectures/20_transactionalmem.pdf  
[3] https://www.youtube.com/watch?v=0jy4Sc_IY7o
### Cache
[4] https://en.wikipedia.org/wiki/List_of_cache_coherency_protocols