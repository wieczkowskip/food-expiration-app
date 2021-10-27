# food-expiration-app

Projekt mini-aplikacji do zarządzania produktami spożywczymi poprzez kontrolę daty ważności. W aplikacji można dodawać oraz przeglądać swoje produkty spożywcze. Lista produktów wyświetla się w kolejności od produktów z najkrótszą datą ważności. Produkty mają 3 stany: dobry, z krótką datą ważności oraz przeterminowany. Dobry produkt to taki, który ma dłuższą datę ważności niż 2 dni - takie produkty wyświetlają się na zielono. Produkty z krótką datą ważności to takie które przeterminują się najpóźniej niż za 2 dni - te produkty są oznaczone kolorem pomarańczowym. Produkty przeterminowane to takie, których data ważności mineła - produkty tego typu są wyświetlane na czerwono.

Dodawanie produktu w aplikacji jest zabezpieczone podstawową walidacją danych, jeżeli są jakieś błędy to wyświetlana jest wtedy informacja o błędzie w formularzu.
Dane w aplikacji są przechowywane w bazie danych przy pomocy Firebase.

Proces instalacji projektu:

### 1. Instalacja potrzebnych paczek:
```
npm install
```
### 2. Uruchomienie serwera:
```
npm run serve
```
### 3. W przeglądarce wpisz "localhost:8080"
