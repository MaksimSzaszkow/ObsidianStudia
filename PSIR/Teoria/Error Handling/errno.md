```C
#include <errno.h>

int errno;
```

**errno** - globalne makro którego wartość jest ustawiana przez system lub niektóre funkcje biblioteczne. Jego wartość to numer błędu który wystąpił, możemy zmienić to na string który nam coś mówi za pomocą funkcji [[strerror()]]