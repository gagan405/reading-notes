## Memory Management
**Date**: 30/12/2025
**Title**: **Mesh: compacting memory management for C/C++ applications**
**Link**: https://dl.acm.org/doi/10.1145/3314221.3314582

Notes:

Claimed as drop in replacement for C/C++ #malloc.

Standard allocation algorithms end up in too many fragmented memory pages. Which is a major concern in non-GCed languages. Over the duration of program run, it ends up using too many memory due to all the holes that were never reclaimed. The mem usage can go substantially above the actual program needs.

In this approach, they do not play around virtual memory addresses. But rather make use of hardware supported virtual memory. They assign blocks uniformly in mem pages, and periodically merge the pages to reduce defragmentation. This only works when multiple pages do not have the same used offset. Which is guaranteed through the Fisher-Yates shuffle while allocating the mem.

This is also suitable for block sizes of 4KB and not for cases where block sizes are large (in MBs).

My take:

Appears too good. But, mangling the pages without touching the pointers, seems too risky and can be hard to debug. I think this will require some battle testing to build confidence - similar to many #GC algos or other #memory-allocation techniques.

### References:
* [https://www.youtube.com/watch?v=VMP2w5o4Yco](https://www.youtube.com/watch?v=VMP2w5o4Yco)
