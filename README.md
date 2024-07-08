# redis-c

A Redis clone written in C/C++ from scratch. Practice makes perfect!

### current to do:

1. **Use epoll instead of poll in the event loop.**  

2. **Optimize the use of memmove in the read buffer.**  
   We are using `memmove` to reclaim read buffer space. However, using `memmove` on every request is unnecessary. Change the code to perform `memmove` only before reading.

3. **Improve the write process in the `state_res` function.**  
   In the `state_res` function, write was performed for a single response. In pipelined scenarios, we could buffer multiple responses and flush them at the end with a single write call. Note that the write buffer could be full in the middle.