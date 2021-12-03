## Tworzenie gniazda
[[socket()]]

## Połącz się (klient)
[[connect()]]

## Połącz gniazdo z portem (serwer)
[[bind()]]

## Nasłuchuj (serwer)
[[listen()]]

## Akceptuj połączenie (serwer)
[[accept()]]

## Zamykanie gniazda
[[close()]]
[[shutdown()]]

## Przykładowe stworzenie socketu
```c
int s;              // Nasz socket
struct addrinfo h;  // Wskazówki configuracyjne (na jego postawie 
                    // będzie stworzona odpowiedź)
struct addrinfo *r; // Zwrócony obiekt (na jego podstawie będzie 
                    // stworzony socket)

memset(&h, 0, sizeof(struct addrinfo)); // memset ustawia bity od danego
                                        // miejsca w pamięci na wybraną wartość
                                        // gdzie ilość bitów to ostatni argument

getaddrinfo("www.moj.serwer.pl", "http", &h, &r) // na podstawie pól zmiennej 
                                                 // h zapełniamy zmienną r
                                                 // informacjami potrzebnymi
                                                 // do stworzenia socketu z
                                                 // podanym serwerem

s = socket(r->ai_family, r->ai_socktype, r->ai_protocol);

if(s == -1){
    printf("ERROR: %s (%s, %d)", strerror(errno), __FILE__, __LINE__);
    // dalszy error handling
}

// Tutaj mamy działające gniazdo, więc korzystamy sobie

// Zwalniamy zasoby !!!

freeaddrinfo(r);
close(s);
```

## Przykładowe połączenie TCP (klient)
```C
#define SERWER "resrepo.tele.pw.edu.pl"

int s;

struct addrinfo h, *r;
memset (&h, 0, sizeof(struct addrinfo));

h.ai_family = AF_INET; 			// AF_INET oznacza IPv4, AF_INET6 IPv6, każda 
								// inna wartość dopasuje gniazdo tak aby 
								// działało z serwerem
								
h.ai_socktype = SOCK_STREAM; 	// SOCK_STREAM oznacza TCP, SOCK_DGRAM UDP

if(getaddrinfo(SERWER, "http", &h, &r)!=0){
	// error handling
}

if((s = socket(r->ai_family, r->ai_socktype, r->ai_protocol)) !=0 ){
	// error handling
}

if(connect(s, r->ai_addr, r->ai_addrlen) != 0){
	// error handling
}

for(;;){
	// Kod klienta
}

freeaddrinfo(r);
close(s);
```

## Przykładowe połączenie TCP (serwer)
```C
int s, new_s;
unsigned char mip_str[INET_ADDRSTRLEN];
struct addrinfo h, *r;

memset (&h, 0, sizeof(struct addrinfo));

h.ai_family = PF_INET;		
h.ai_socktype = SOCK_STREAM;
h.ai_flag = AI_PASSIVE;

if(getaddrinfo(NULL, "123456", &h, &r)!=0){
	// error handling
}

if((s = socket(r->ai_family, r->ai_socktype, r->ai_protocol)) != 0 ){
	// error handling
}

if(bind(s, r->ai_addr, r->ai_addrlen)!=0){
	// error handling
}

if(listen(s, 1) != 0){
	// error handling
}

struct sockaddr_in their_addr;
socklen_t addr_size = sizeof(their_addr);

if((new_s = accept(s, (struct sockaddr *)&their_addr, &addr_size)) == -1){
	// error handling
}

if(inet_ntop(AF_INET, &(their_addr.sin_addr), mip_str, INET_ADDRTRLEN) == NULL){
	// error handling
}

for(;;){
	// Kod serwera
}

freeaddrinfo(r);
close(s);
```