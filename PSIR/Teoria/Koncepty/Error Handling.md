# Error Handling w C
W języku C przyjęte jest że w momencie wykrycia błędu jego kod numeryczny będzie zapisany w globalnym makrze [[errno]], który można odczytać w "ludzki" sposób za pomocą [[strerror()]].

Typowe errory z którymi można się spotkać to:
- [[EINVAL]]
- [[EPROTONOSUPPORT]] 
- [[EMFILE]] 
- [[EACCESS]] 
- [[ENOBUFFS]]
