**Metody pomiarowe aktywne** - pozwalają zmierzyć wartości [[Jakość usługi (QoS) | QoS]] (opóźnienie, [[Zmienność opóźnienia przekazu pakietów (IPDV) IETF | zmienność opóźnienia]], [[Poziom strat pakietów (IPLR)| poziom strat pakietów,]] [[Przepływność| przepływność]]) przez wysłanie specjalnych pakietów pomiarowych (probing packets) w ramach monitorowanego strumienia ruchu. Pomiar taki zakłada że te specjalne pakiety są obsługiwane **tak samo** jak zwykłe pakiety, przez co za ich pomocą możemy wyznaczyć **przybliżone** wartości metryk dla użytkownika. 

Przesyłane pakiety posiadają znacznik czasowy w polu danych określający czas wysłania, po odebraniu od razu wysyłany jest packet z znacznikiem czasowym z momentu odebrania. Oznacza to że nadajnik i odbiornik muszą mieć identyczną podstawę czasową.

Wadą metod pomiarowych aktywnych jest stworzenie ruchu obciążającego sieć, gdyż wysłany pakiet aby przetestować sieć dla wybranej wielkości ruchu musi stworzyć ruch o podobnej wielkości, zatem nie może być za mały bo nie będzie to porównywalne z faktycznymi wartościami metryk, ale nie może być też za duży, bo wtedy zmieni parametry sieci przez fakt że uczestniczy w ruchu.

Poza wielkością ruchu, należy również wybrać profil ruchu, z reguły wykorzystywane są profile o stałej szybkości bitowej lub generowanej losowo. 

Ze względu na prostotę implementacji metoda ta jest wykorzystywana przez większość narzędzi