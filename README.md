# GastroPulse

Interaktywny prototyp portfolio dla gastronomii: ręczny rejestr strat i panel analityczny. Niezależny od GoPOS; wszystkie początkowe wpisy są fikcyjne. Bez kont, integracji POS, backendu i funkcji AI; wskazówki wynikają z prostego rankingu.

## Uruchomienie

```sh
python3 -m http.server 8000 --bind 0.0.0.0
```
Otwórz aplikację na porcie 8000. Nie wymaga instalacji zależności. Dane i zmiany przechowywane są w localStorage danej przeglądarki; nie używaj danych poufnych ani produkcyjnych. Przycisk „Przywróć dane” usuwa lokalne zmiany.

## Co działa

Osobne widoki: pulpit, rejestr strat, produkty, analityka i ustawienia. Dodawanie i usuwanie wpisów, wyszukiwanie, filtrowanie po okresie, kategorii i przyczynie, sortowanie, podsumowania, ranking, analiza kategorii i przyczyn, wykres oraz eksport filtrowanych wpisów do CSV. Kwota jest całkowitą wartością straty, a najczęstsza przyczyna liczona jest według liczby wpisów. Wykres dla całego okresu pokazuje maksymalnie 10 ostatnich wpisów; dla 7 i 30 dni pokazuje przedziały czasu. Nie należy sumować jednostek o różnych wymiarach.

## Kolejne kroki

Zweryfikować problem i prototyp z użytkownikami; zaprojektować konta, separację lokali, reguły RLS i migracje przed zastosowaniem Supabase. Dostępny konektor nie zwrócił żadnych projektów Supabase. Żadna integracja GoPOS ani baza nie została skonfigurowana. Plan i hipotezy znajdują się w Notion.

## Wdrożenie na Vercel

1. W Vercel wybierz **Add New → Project** i zaimportuj repozytorium `hajtocolor/projekty`.
2. Projekt jest statyczny: wybierz **Framework Preset: Other**, katalog główny repozytorium (`./`), bez polecenia budowania, bez katalogu wynikowego i bez zmiennych środowiskowych.
3. Kod znajduje się na gałęzi `arena/8e6acfe0-projekty`. Aby wdrożyć tę wersję jako produkcyjną, ustaw ją jako **Production Branch** w ustawieniach Git projektu Vercel albo scal zmiany do głównej gałęzi przez pull request. Wdrożenia innych gałęzi zwykle są dostępne jako Preview.
4. Kliknij **Deploy**. Aplikacja nie wymaga bazy ani kluczy API; zapisy pozostają osobne dla każdej przeglądarki i domeny.
