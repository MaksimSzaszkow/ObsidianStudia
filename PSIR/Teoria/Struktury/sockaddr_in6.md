wersja [[sockaddr_in]] dla sieci IPv6

```C
struct sockaddr_in6{
	u_int16_t sin6_family;
	u_int16_t sin6_port;
	u_int32_t sin6_flowinfo;
	struct in6_addr sin6_addr;
	u_int32_t sin6_scope_id;
}
```