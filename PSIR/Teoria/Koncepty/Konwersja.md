## Konwersja na język "sieci"
Ogólno przyjętym standardem kodowania oktetów w sieci jest [[Big-endian | big-endian]], ale na lokalnych maszynach nie mamy gwarancji ze tak będzie. Dlatego właśnie mamy funkcje które pozwolą nam zmienić zapis który jest na naszej maszynie na poprawny zapis sieciowy:
- [[htonl]]
- [[htons]]

## Konwersja na język "ludzki"
Ogólno przyjętym standardem kodowania bitów w ludzkim mózgu jest alfabet, co oznacza że potrzebujemy funkcji które zmienią bity na tekst zrozumiały dla nas:
- [[inet_ntop()]]
- [[inet_pton]]