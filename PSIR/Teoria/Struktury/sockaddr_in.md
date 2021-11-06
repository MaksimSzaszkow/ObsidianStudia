Nowsza wersja [[sockaddr]] z nowymi polami i wyciągniętym adresem ip do [[in_addr]]

```C
struct sockaddr_in{
	short int sin_family;
	unsigned short int sin_port;
	struct in_addr sin_addr;
	unsigned char sin_zero[8]
}
```