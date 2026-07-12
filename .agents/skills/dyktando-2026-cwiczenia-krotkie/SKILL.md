---
name: dyktando-2026-cwiczenia-krotkie
description: "Generuje krótkie, celowane ćwiczenia dyktandowe (pojedyncze zdania, jedno na raz) testujące znajomość zmian w pisowni polskiej wprowadzonych reformą ortografii 2026 r. Użyj tego skilla, gdy użytkownik prosi o krótkie ćwiczenie, przetestowanie, przepytanie, quiz lub szybką naukę zasad pisowni związanych z reformą 2026, np. \"przepytaj mnie\", \"daj mi zdanie do przećwiczenia\", \"chcę poćwiczyć pisownię\". Nie używaj tego skilla, jeśli użytkownik prosi o pełne, długie, literackie dyktando (wielozdaniowy tekst) — to osobny skill. Zawsze konsultuj ten skill przy sesjach szybkiej, celowanej nauki pisowni w tym projekcie."
---

# Krótkie ćwiczenia dyktandowe 2026 — trener zmian ortograficznych

## Cel
Ten skill prowadzi sesję ćwiczeniową: generuje jedno krótkie zdanie na raz, testujące jedną konkretną zmianę wprowadzoną reformą ortografii 2026 r., czeka na odpowiedź użytkownika, a potem daje pełną informację zwrotną (poprawna pisownia + stara zasada vs nowa zasada + odsyłacz do numeru paragrafu).

## Zasada nadrzędna: nie myl "starego" z "nowym"
Dokumenty w `reforma-2026/zmiany/` opisują przepisy, które w jakimś stopniu ZMIENIŁY SIĘ względem stanu sprzed 2026 r. — ale to nie znaczy, że CAŁA treść dokumentu jest nowością. Większość treści to często stare, niezmienione reguły — nowością bywa tylko jeden wyjątek, jedna UWAGA, jedno rozszerzenie zakresu.

Zanim wygenerujesz zdanie testujące jakąś zasadę, ZAWSZE ustal, co dokładnie jest nowe:
1. Sprawdź `reforma-2026/komunikat-rjp.md`, sekcję "Załącznik nr 1" — tam wypisano wprost, co się zmieniło.
2. Jeśli dana zmiana nie jest tam jasno opisana, poszukaj wskazówek w samym dokumencie zasady (np. odsyłacze do starych numerów paragrafów, adnotacje typu "ZGODNE Z REFORMĄ ORTOGRAFII '26", akapity "UWAGA" przy nowych wyjątkach).
3. Testuj zdaniem WŁAŚNIE tę zmienioną część zasady — nie losowy przykład z całego dokumentu, bo może on ilustrować regułę sprzed 2026 r., która się nie zmieniła.

Przykład: dokument 138.md (pół + rzeczownik) w większości opisuje starą, niezmienioną regułę pisowni łącznej (np. "półkula", "półmrok"). Nowością jest wyłącznie UWAGA 2 dot. łącznika w PODWÓJNYCH konstrukcjach typu "pół-Polka, pół-Francuzka" opisujących jedną osobę (zob. też 139.md i komunikat RJP, pkt 6). Zdanie testowe powinno więc dotyczyć tej podwójnej konstrukcji, a nie np. słowa "półkula".

Jeśli nie masz pewności, czy coś jest nowe czy stare — powiedz to wprost użytkownikowi zamiast zgadywać.

## Przebieg sesji

### Krok 1: Ustal zakres
- Domyślnie: losuj z całej puli zmienionych zasad (pliki w `reforma-2026/zmiany/`).
- Jeśli użytkownik prosi o konkretny zakres (numer zasady, temat, np. "tylko pół i quasi-/niby-"), ogranicz się do niego.
- Nie pytaj o zakres, jeśli użytkownik już poprosił o ćwiczenie bez dodatkowych wytycznych — po prostu losuj i zaczynaj.

### Krok 2: Wybierz zasadę i konkretną zmianę
- Zajrzyj do `reforma-2026/zmiany/index.md` po listę dostępnych plików.
- Wybierz jeden plik (a w ramach dłuższej sesji kolejno różne pliki, żeby nie powtarzać się bez potrzeby).
- Zidentyfikuj zmienioną część zgodnie z sekcją "Zasada nadrzędna" powyżej.
- **Poziom trudności: wysoki (przygotowanie do najtrudniejszego dyktanda w kraju).** Nie wybieraj pierwszego z brzegu, najbardziej oczywistego przykładu. Słowo/wyrażenie testujące daną zmianę może pochodzić:
  a) z listy przykładów w dokumencie źródłowym (`reforma-2026/zmiany/*.md`), lub
  b) spoza tej listy — z ogólnej wiedzy o języku polskim — jeśli lepiej ilustruje daną zasadę i jest trudniejsze/rzadsze niż przykłady podane w dokumencie.
  W obu przypadkach: dobierz słowo rzadkie, mało znane, archaiczne lub łatwe do pomylenia z podobną, ale inaczej zapisywaną konstrukcją. Unikaj przykładów podręcznikowych/oczywistych (np. "Polka", "Warszawianin").
  **Zastrzeżenie:** swoboda w doborze SŁOWA nie oznacza swobody w ustalaniu SAMEJ ZASADY. To, czy dana zmiana jest nowa (2026) czy stara, oraz jak dokładnie brzmi reguła, musi zawsze wynikać z dokumentów źródłowych (`komunikat-rjp.md`, `zmiany/*.md`) zgodnie z sekcją "Zasada nadrzędna" — nigdy nie zgaduj tego na podstawie ogólnej wiedzy, nawet jeśli akurat dobierasz słowo spoza dokumentów.
  **W razie wątpliwości lub gdy szukasz dodatkowej trudności** — np. przy sprawdzaniu, czy jakieś słowo spoza dokumentu (opcja b powyżej) jest rzeczywiście trudne/rzadkie, albo przy weryfikacji poprawności gramatycznej otoczenia zdania — sięgnij do `zasady/zasady-pisowni-i-interpunkcji.md`. To ogólne źródło referencyjne zasad pisowni i interpunkcji spoza reformy 2026.

### Krok 3: Wygeneruj JEDNO krótkie zdanie
- Krótkie, neutralne zdanie (NIE stylizowane na archiwalne dyktanda RJP — to ma być celowane ćwiczenie, nie literacki popis) zawierające dokładnie jedno słowo/konstrukcję testującą wybraną zmianę.
- Nie zdradzaj w zdaniu ani w komentarzu, jaka zasada jest testowana.
- **To ćwiczenie testuje WYŁĄCZNIE ortografię (wielka/mała litera, łącznik, pisownia łączna/rozdzielna), NIGDY odmianę.** Testowany wyraz musi być osadzony w zdaniu już w poprawnej, docelowej formie gramatycznej (właściwy przypadek, liczba, rodzaj) wynikającej z kontekstu zdania. To Ty (jako autor zdania) odmieniasz wyraz poprawnie — użytkownik ma decydować tylko o zapisie (np. "warszawianką" czy "Warszawianką"), a nie o tym, jaka końcówka/forma gramatyczna pasuje. Nigdy nie przedstawiaj wyboru w rodzaju "(mianownik / mianownik z wielką literą)", jeśli zdanie wymaga innego przypadka — to myli ortografię z gramatyką.
- Sprawdź poprawność gramatyczną całego zdania, zanim je pokażesz — w szczególności zgodność przypadka testowanego wyrazu z resztą zdania (np. po "jest", "był", "z", "bez" itp. wymagany jest odpowiedni przypadek, nie mianownik "z automatu").
- **NIGDY nie ujawniaj poprawnej pisowni w treści pytania.** Testowany fragment musi być przedstawiony w sposób, który realnie wymaga decyzji użytkownika. Zawsze pokaż pełne alternatywne wersje zapisu wprost, jedna obok drugiej, do wyboru — np. "kometę Hale'a-Boppa" czy "Kometę Hale'a-Boppa"? Nie zadawaj pytania opisowego (np. "z małej czy wielkiej litery?") bez pokazania obu wariantów w pełnej formie — użytkownik ma wskazać, który zapis jest poprawny, a nie samodzielnie go zrekonstruować z opisu.
- **Jeśli więcej niż jeden wariant zapisu jest poprawny** (np. dopuszczalna pisownia łączna, z łącznikiem i/lub rozdzielna — sprawdź to w dokumencie źródłowym), pokaż WSZYSTKIE warianty istotne dla danej zasady (poprawne i niepoprawne razem, min. 3 opcje, jeśli to możliwe) i poproś użytkownika o wskazanie WSZYSTKICH poprawnych — nie tylko jednego. To realnie sprawdza, czy użytkownik zna pełny zakres dopuszczalności, a nie tylko jedną z kilku poprawnych form.
- Przedstaw zdanie użytkownikowi z prośbą o wskazanie/zapisanie poprawnej pisowni testowanego fragmentu (w formie już podanej w zdaniu). Podaj tylko jedno zdanie na raz.

### Krok 4: Poczekaj na odpowiedź użytkownika
Nie generuj kolejnego zdania ani nie ujawniaj odpowiedzi, dopóki użytkownik nie odpowie na bieżące.

### Krok 5: Pełna informacja zwrotna
Po odpowiedzi użytkownika podaj zwięźle:
1. Czy odpowiedź była poprawna.
2. Poprawną pisownię testowanego fragmentu.
3. Zasadę SPRZED 2026 r. (jak było wcześniej).
4. Zasadę OD 2026 r. (co się zmieniło i dlaczego).
5. Odsyłacz do źródła (np. "zob. 138, UWAGA 2" albo "komunikat RJP, Załącznik 1, pkt 6").

### Krok 6: Kontynuacja
Zapytaj (albo, jeśli z kontekstu jasno wynika, że to sesja ciągła — po prostu kontynuuj), czy użytkownik chce kolejne zdanie.

## Ważne zasady stylu
- Jedno zdanie na raz. Nigdy nie wysyłaj kilku zdań naraz, chyba że użytkownik wyraźnie o to poprosi.
- Ćwiczenia zawsze wprost w czacie — nie twórz plików/artefaktów dla pojedynczych zdań.
- Nie testuj tej samej zasady dwa razy pod rząd w obrębie jednej sesji, chyba że użytkownik o to prosi (np. "jeszcze raz to samo, bo się pomyliłam/em").
- Jeśli użytkownik odpowie błędnie, nie przechodź od razu dalej bez wyjaśnienia — najpierw pełna informacja zwrotna z Kroku 5, dopiero potem pytanie o kontynuację.

## Źródła
- `reforma-2026/komunikat-rjp.md` — najważniejsze źródło: co dokładnie się zmieniło (Załącznik nr 1).
- `reforma-2026/zmiany/*.md` — pełne teksty zmienionych zasad.
- `reforma-2026/zmiany/index.md` — lista dostępnych plików zasad
- `zasady/zasady-pisowni-i-interpunkcji.md` — ogólne (spoza reformy 2026) zasady ortografii i interpunkcji; sprawdzaj tu w razie wątpliwości oraz przy szukaniu dodatkowo trudnych przykładów spoza dokumentów reformy.