---
name: dyktando-2026-pelne
description: Generuje pełne, literackie teksty dyktand (do 200 słów) w stylu archiwalnych dyktand RJP, łączące zmiany reformy ortografii 2026 r. z klasycznymi pułapkami polskiej ortografii i interpunkcji. Tekst jest dostarczany jako plik .txt (artefakt), NIGDY nie jest cytowany ani ujawniany w treści czatu, żeby użytkownik mógł go wykorzystać jako niespodziankę do dyktowania (np. w narzędziu syntezującym mowę) bez uprzedniego zapoznania się z treścią. Użyj tego skilla, gdy użytkownik prosi o "pełne dyktando", "długi tekst do dyktowania", "dyktando do przećwiczenia całego tekstu" lub podobnie. Nie używaj tego skilla do krótkich, pojedynczych zdań testujących jedną zasadę — to osobny skill (dyktando-2026-cwiczenia-krotkie).
---

# Pełne dyktando 2026 — generator tekstów do dyktowania

## Cel
Ten skill generuje jeden zwarty, literacki tekst dyktanda (maks. 200 słów), gęsto nasycony pułapkami ortograficznymi i interpunkcyjnymi — zarówno tymi wynikającymi ze zmian reformy 2026 r., jak i klasycznymi, niezwiązanymi z reformą. W przeciwieństwie do krótkich ćwiczeń, ten tekst jest już w 100% poprawnie zapisany (sam w sobie jest kluczem) i ma zostać wykorzystany przez użytkownika jako materiał do faktycznego dyktowania (np. przez zewnętrzne narzędzie syntezujące mowę), więc jego treść MUSI pozostać dla użytkownika niespodzianką do momentu, aż sam go odsłucha.

## Krytyczna zasada: nigdy nie ujawniaj treści w czacie
- Wygenerowany tekst trafia WYŁĄCZNIE do pliku .txt zapisanego w `/mnt/user-data/outputs/` i udostępnionego przez `present_files`.
- W wiadomości do użytkownika NIE cytuj ani nie parafrazuj żadnego fragmentu wygenerowanego tekstu — ani pojedynczych zdań, ani nawet pojedynczych "ciekawych" wyrazów.
- Możesz podać wyłącznie metadane: liczbę słów, ogólną tematykę (jeśli nie zdradza kluczowych wyrazów), oraz — jeśli użytkownik o to poprosi — listę NAZW zastosowanych zasad (np. "pół + nazwa własna", "przecinek przed <i>który</i>") bez podawania, w którym miejscu tekstu się pojawiają ani jak dokładnie są zapisane.
- Jeśli w ramach tej samej sesji trzeba coś poprawić w tekście, edytuj plik bezpośrednio (np. `str_replace`) i podawaj użytkownikowi tylko opis zmiany (np. "poprawiłam interpunkcję w trzecim zdaniu"), nie fragment tekstu.
- Weryfikację poprawności wygenerowanego tekstu rób samodzielnie (czytając plik narzędziem `view`), nie proś użytkownika o sprawdzenie fragmentów w czacie.

## Zasada nadrzędna: nie myl "starego" z "nowym" (identyczna jak w skillu krótkich ćwiczeń)
Dokumenty w `reforma-2026/zmiany/` opisują przepisy, które w jakimś stopniu ZMIENIŁY SIĘ względem stanu sprzed 2026 r. — nie cała ich treść jest nowością. Przed wpleceniem danej konstrukcji do tekstu:
1. Sprawdź `reforma-2026/komunikat-rjp.md`, sekcję "Załącznik nr 1" — tam wypisano wprost, co się zmieniło.
2. Jeśli to niejasne, szukaj wskazówek w samym dokumencie zasady (odsyłacze do starych numerów paragrafów, adnotacje, akapity "UWAGA").
3. Upewnij się, że użyta w tekście forma jest zgodna z zasadą OBOWIĄZUJĄCĄ OD 2026 r. — to jest jedyna poprawna wersja dla tego tekstu (nie ma tu miejsca na warianty "stary/nowy", tekst musi być jednoznacznie poprawny na dziś).

## Przebieg sesji

### Krok 1: Ustal parametry
- Domyślnie: swobodny temat, literacki/żartobliwy styl (jak w `archiwum-rjp/*.md`), losowy dobór zasad reformy 2026.
- Jeśli użytkownik poda temat, długość inną niż domyślna, albo konkretny zestaw zasad do wplecenia — dostosuj się.
- Nie pytaj o szczegóły, jeśli użytkownik po prostu poprosił o "dyktando" — zacznij od razu z sensownymi założeniami domyślnymi.

### Krok 2: Zaplanuj zestaw testowanych zasad (PRZED napisaniem tekstu)
- Przejrzyj `reforma-2026/zmiany/index.md` i wybierz kilka (orientacyjnie 4–7, zależnie od gęstości) różnych zmienionych zasad reformy 2026 — różnorodnych kategorii (np. nie tylko "pół-", ale też wielkie litery mieszkańców, cząstki -by, przedrostki, niby-/quasi-, nazwy geograficzne/astronomiczne itd.), żeby dyktando nie było jednostajne.
- Dodatkowo zaplanuj kilka klasycznych, niezwiązanych z reformą pułapek ortograficznych i interpunkcyjnych — na WYSOKIM poziomie trudności, adekwatnym do najtrudniejszego dyktanda w kraju, a nie podstawowych szkolnych zasad. Wzoruj się na `archiwum-rjp/*.md`, gdzie takie pułapki występują masowo. Przykładowe kategorie (nie wyczerpujące — szukaj też innych):
  - **imiesłowowy równoważnik zdania** — zawsze wydzielony przecinkami z obu stron, łatwo pominąć jeden z nich przy dłuższej wtrąconej frazie (np. "Przypomniawszy sobie, że..., ustalono, że...");
  - **partykuły wzmacniające -że, -no, -li, -ż** pisane łącznie z czasownikiem/spójnikiem (np. "chodźże", "dalibóg", "pozwoliszli", "jakoż", "czyliż") — łatwe do pomylenia z pisownią rozdzielną;
  - **nieprzyswojone zapożyczenia i wyrażenia obce zapisywane kursywą/oryginalnie** (np. "à propos", "vis-à-vis", "dell'arte", "ad hoc", "de facto") — w tym ich odmiana z apostrofem przy nazwiskach obcych (np. "u Woody'ego Allena", "z Goethego");
  - **homofony i quasi-homofony** różniące się pisownią (np. "morze/może", "wziąć/wziąść", "żeby/że by", "gdyż/gdyż by") — do rozróżnienia wyłącznie z kontekstu zdania;
  - **trudne złożenia z liczebnikami** (np. "dwuipółletni", "stopięćdziesięciolecie", "ponaddwudziestoletni") — pisane łącznie mimo pozornej złożoności;
  - **interpunkcja w zdaniach z porównaniami bez "jak"** (np. konstrukcje z "niż", "aniżeli", "im... tym...") oraz przy wtrąceniach imiesłowowych, apozycjach i zdaniach wielokrotnie złożonych z kilkoma spójnikami podrzędnymi naraz;
  - **cudzysłowy zagnieżdżone** (cytat w cytacie) oraz różnice między cudzysłowem a znakiem stosowanym przy tytułach/nazwach własnych w tym samym zdaniu.
  Unikaj podstawowych, szkolnych przykładów typu "przecinek przed że/który" jako GŁÓWNEGO testowanego elementu — takie proste konstrukcje mogą pojawić się w tle zdania, ale nie powinny być twoim celowym, zaplanowanym punktem trudności.
- Zapisz sobie (wewnętrznie, nie w odpowiedzi dla użytkownika) krótką listę zaplanowanych zasad — posłuży do weryfikacji na Kroku 4.
- Poziom trudności: wysoki, jak w krótkich ćwiczeniach — sięgaj po rzadkie, archaiczne lub mało oczywiste słownictwo, wzorem `archiwum-rjp/*.md`, a nie podręcznikowe przykłady.

### Krok 3: Napisz tekst
- Styl: literacki, żartobliwy, gęsty od trudnych wyrazów — wzorowany na tekstach z `archiwum-rjp/` (dialogi, gra słów, archaizmy, rzadkie zapożyczenia), ale BEZ nawiasów z wariantami pisowni typu "[albo: ...]" — tekst ma być czytany/odsłuchiwany, więc musi mieć jedną, jednoznaczną wersję każdego wyrazu.
- Limit: maksymalnie 200 słów. Policz słowa przed zapisaniem pliku; jeśli przekracza limit, skróć.
- Zadbaj o naturalność — mimo gęstości pułapek, tekst musi być gramatycznie i logicznie spójny, a nie sztucznym zlepkiem trudnych słów.
- Upewnij się, że KAŻDA forma związana z reformą 2026 jest zapisana zgodnie z zasadą obowiązującą OD 2026 r. (zob. sekcja "Zasada nadrzędna").

### Krok 4: Zweryfikuj przed zapisaniem
- Przeczytaj własny tekst jeszcze raz, zdanie po zdaniu, i sprawdź każdą zaplanowaną z Kroku 2 zasadę — czy rzeczywiście jest obecna i poprawnie zapisana.
- Sprawdź limit słów (dokładne liczenie, nie szacunek).
- Sprawdź podstawową poprawność gramatyczną (zgodność przypadków, liczby, rodzaju) — błąd gramatyczny w dyktandzie jest niedopuszczalny, bo tekst ma być dyktowany jako wzorcowy.

### Krok 5: Zapisz jako plik i udostępnij
- Zapisz tekst jako plik `.txt` (samy tekst, bez nagłówków markdown, bez adnotacji) w `/mnt/user-data/outputs/`, np. `dyktando-2026-{krotki-opis-tematu}.txt`.
- Udostępnij plik przez `present_files`.
- W odpowiedzi do użytkownika NIE cytuj treści — podaj tylko: liczbę słów oraz (opcjonalnie) ogólnikową informację o liczbie i różnorodności wplecionych zasad, bez zdradzania które to konkretnie miejsca w tekście.

### Krok 6: Kontynuacja
Zapytaj, czy użytkownik chce kolejne dyktando (np. na inny temat, z innym zestawem zasad), czy to na razie wystarczy.

## Ważne zasady stylu
- Jeden plik = jedno dyktando. Nie generuj kilku wariantów naraz, chyba że użytkownik wyraźnie o to poprosi.
- Nie proponuj poprawek "na oko" bez ponownego przeczytania całego pliku — po każdej edycji zweryfikuj plik od nowa (Krok 4).
- Jeśli użytkownik prosi o sprawdzenie swojej odpowiedzi (np. wkleja to, co sam zapisał, po odsłuchaniu dyktanda), możesz wtedy porównać jego tekst z plikiem źródłowym i wskazać różnice — to jedyny moment, w którym można odnosić się do treści pliku wprost, bo użytkownik już go usłyszał.

## Źródła
- `archiwum-rjp/*.md` — wzorzec stylistyczny (literacki, żartobliwy, gęsty od archaizmów i rzadkich wyrazów).
- `reforma-2026/komunikat-rjp.md` — źródło prawdy o tym, co dokładnie zmieniła reforma (Załącznik nr 1).
- `reforma-2026/zmiany/*.md` — pełne teksty zmienionych zasad, źródło poprawnych form po 2026 r.
- `reforma-2026/zmiany/index.md` — lista dostępnych plików zasad.