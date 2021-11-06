```C
#include <sys/socket.h>  
  
ssize_t send(int socket, const void *buffer, size_t length, int flags);

send(sockfd, &(buf[prev_pos], len - prev_pos, flags));
```