**Metody pomiarowe pasywne** - polegają na obserwacji pakietów przechodzących przez dany punkt pomiarowy i wykonywaniu na nich potrzebnych analiz. 

Jeśli analizujemy tylko w jednym punkcie pomiarowym, możemy zbadać charakterystyki przesyłanego ruchu, jak np. średniej szybkości bitowej ruchu na danym łączu

Analiza na dwóch punktach pomiarowych, możemy dokonać pomiaru wartości metryk jakości przekazu pomiędzy tymi punktami ([[Jakość usługi (QoS)| QoS]]). Z reguły tak zebrane pakiety są wysyłane do serwera zarządzającego pomiarami, gdzie są analizowane. Aby analiza miała sens musimy zapewnić wspólną bazę czasową wszystkich maszyn uczestniczących w procesie. 

Zaleta analizy pasywnej to fakt iż nie obciąża sieci w znaczący sposób. Proces zbierania pakietów nie dodaje żadnego ruchu, a przesłanie danych do głównego serwera nie zmienia zachowania sieci w znaczący sposób, ponieważ pakiety te mogą być przesyłane z mniejszym priorytetem niż te użytkownika.

Największa wada to złożoność implementacji, gdyż najpierw trzeba zapisać pakiety które nas interesują, a po przesłaniu wykonać na nich analizę która dostarczy nam wartości interesujących nas metryk.