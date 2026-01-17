# Analiza i klasteryzacja miast europejskich

## Cel projektu
Celem projektu jest zbadanie, czy wśród europejskich miast można wyróżnić grupy o podobnych cechach społeczno-demograficznych i ekonomicznych. Analiza pozwala:
- Identyfikować typy miast (np. metropolie, miasta turystyczne, miasta z dużym udziałem cudzoziemców),
- Wspierać planowanie miejskie i regionalne,
- Ułatwiać porównania między miastami i krajami.

Hipoteza: europejskie miasta można podzielić na kilka charakterystycznych klastrów na podstawie danych społeczno-ekonomicznych.

---

## Źródła danych
Dane pochodzą z Eurostatu i obejmują wskaźniki demograficzne, społeczne, edukacyjne i infrastrukturalne.  
Liczba miast w zbiorze: 926 (od ~40 tys. do największych metropolii).  
Więcej informacji:  
- [Eurostat – Urban Europe](https://ec.europa.eu/eurostat/databrowser/explore/all/general?sort=category&lang=en&subtheme=urb.urb_cgc&display=list)  
- [Metadane](https://ec.europa.eu/eurostat/cache/metadata/en/urb_esms.htm)

---

## Przygotowanie danych
1. Wczytanie i połączenie kilkunastu tabel w jeden DataFrame.
2. Selekcja zmiennych kluczowych: populacja, powierzchnia mieszkalna, wskaźniki demograficzne, edukacja, bezrobocie, liczba samochodów, udział cudzoziemców.
3. Czyszczenie danych:
   - usunięcie braków i obserwacji o niskiej jakości,
   - przeliczenie wskaźników względnych (np. na mieszkańca),
   - standaryzacja zmiennych numerycznych.
4. Imputacja braków:
   - średnia, mediana, KNN i MICE w zależności od charakteru zmiennej.

---

## Metodologia
- Algorytm: **K-means clustering**
- Dobór liczby klastrów:
  - metoda łokcia (inertia),
  - **silhouette score**.
- Redukcja wymiarowości: **PCA do wizualizacji**.
- Ostateczny wybór: **k = 3**, ze względu na czytelność i interpretowalność klastrów.

---

## Wyniki klasteryzacji

### Charakterystyka klastrów

| Klaster | Opis | Przykładowe miasta |
|---------|------|------------------|
| 0 | Duże metropolie i miasta globalne: wysoki udział cudzoziemców, liczba studentów, niska stopa bezrobocia | Paryż, Londyn, Berlin, Madryt, Barcelona, Mediolan, Amsterdam |
| 1 | Miasta zachodnioeuropejskie o stabilnej, starzejącej się populacji: duża powierzchnia mieszkalna, wysoki wskaźnik osób starszych, wyższe bezrobocie | Rzym, Turyn, Palermo, Bologna, Florencja, Genua |
| 2 | Miasta Europy Środkowo-Wschodniej i peryferyjne: mniejsza powierzchnia mieszkalna, niski udział cudzoziemców i studentów | Warszawa, Budapeszt, Praga, Kraków, Wrocław, Sofia, Wilno, Zagrzeb |

### Rozkład klastrów w krajach
- Polska, Rumunia, Turcja: głównie cluster 2  
- Włochy: głównie cluster 1  
- Francja, Niemcy: mieszanka cluster 0 i 1  
- Wielka Brytania: znaczący udział cluster 0 i 2

---

## Wnioski
- Europejskie miasta tworzą **ciągłe spektrum cech**, brak wyraźnych naturalnych klastrów.
- Klastry 0–2 stanowią **przydatne typologie**, ułatwiające interpretację i porównanie miast.
- Wyniki są zgodne z oczekiwaniami: podział od dużych metropolii, przez miasta zachodnioeuropejskie, po średnie miasta Europy Środkowo-Wschodniej.
- Analiza może wspierać planowanie urbanistyczne, decyzje biznesowe i badania porównawcze.

---

## Ograniczenia
- Dane pochodzą z różnych lat.  
- Wybór zmiennych miał charakter arbitralny.  
- Algorytm K-means wymusza kulistą strukturę klastrów.  
- Brak danych przestrzennych ogranicza analizę geograficzną.

---

## Możliwe kierunki dalszych badań
- Wypróbowanie innych algorytmów klasteryzacji (DBSCAN, HDBSCAN, GMM).  
- Analiza zmian w czasie.  
- Uwzględnienie danych przestrzennych i geograficznych.  
- Szczegółowa analiza poszczególnych krajów i regionów.

---

## Autor
Projekt wykonany w ramach zaliczenia przedmiotu "Uczenie Maszynowe" SGGW 2026
Michał Wroński
