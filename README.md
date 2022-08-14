# 🌍 Jak podłączyć domenę do mojego serwera Minecraft?
Witaj w tym jakże skromnym poradniku, dot. podłączania domen do serwera.
Moim celem było zachowanie powszechnie znanej zasady - minimum tekstu, maksimum treści.
Myślę, że udało mi się stworzyć ten samouczek tak jak chciałem, żeby wyglądał.
Miłego czytania.

Wszelkie błędy napotkane podczas czytania należy zgłaszać na DM: **igoyek#0001**.

## 🔧 Wybór dostawcy usług
Często przed zakupem domeny padają pytania - "Jakiego dostawcę wybrać?", OVH? AZ? NAZWA?
Osobiście uważam, że różnica jest niewielka. Co innego gdybyśmy mieli zakupić maszynę dedykowaną.
Wtedy wszcząłbym szerszy research i poczytał opinie na różnych forach.
Pierwszą domenę, którą posiadałem zakupiłem u dostawcy widniejącego pod szyldem **NETMARK**.
Nie było źle, nie mniej jednak po przejściu na **OVHCloud** poczułem ulgę.
Większość poradników, które znajdziecie w internecie będą dotyczyły właśnie OVH.

## ⛏ Podłączanie domeny do serwera gry
### Ustawienie rekordu A
Pierwszym krokiem jaki musimy poczynić jest zdefiniowanie adresu docelowego naszej maszyny.
Jeśli rekord A w strefie DNS naszej domeny istnieje, usuwamy go i tworzymy nowy.

**Subdomena:** W to miejsce wpisujemy jaki ma być prefiks naszego adresu połączenia z serwerem. Przykładowo może być to `mc.domena.pl`, bądź `serwer.domena.pl`. Jeśli natomiast pole zostanie puste, do naszego serwera będziemy łączyć się przez `domena.pl`.

**TTL:** Zostawiamy domyślne.

**Wartość:** Tutaj wpisujemy docelowy adres naszego serwera. Może być to IP numeryczne, np. `127.0.0.1`, bądź host (w zależności od hostingu), np. `n1.hosting.pl`.
**UWAGA!** W tym polu nie podajemy portu docelowego serwera!

### Ustawienie rekordu SRV
**Subdomena:** Wpisujemy wartość `_minecraft._tcp.PREFIX.`
W miejsce *DOMENA* wprowadzamy wartość, którą ustaliliśmy w rekordzie A jako subdomenę, np. `mc`.domena.pl, bądź `serwer`.domena.pl.

**TTL:** Zostawiamy domyślne.

**Priorytet:** Ustawiamy na wartość "0".

**Waga:** Ustawiamy na wartość "0".

**Port:** Tutaj wprowadzamy port docelowy naszego serwera, np. `25565`.

**Adres docelowy:** Tutaj wpisujemy wartość podaną w rekordzie A jako *subdomenę*, np. `mc.domena.pl` lub `serwer.domena.pl`.

**Docelowa wartość rekordu:** "{priorytet} {waga} {port} {adres docelowy}", np. `0 0 25565 mc.domena.pl`
