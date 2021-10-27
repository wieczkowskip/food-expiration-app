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
### 3. W przeglądarce wpisz:
```
localhost:8080
```
# Galeria zdjęć:

## Widok przeglądu produktów spożywczych:
![first](https://user-images.githubusercontent.com/75487443/139124186-50acbff6-3c58-4330-923a-4208a4d00ef4.JPG)

## Widok dodawania nowego produktu:
![second](https://user-images.githubusercontent.com/75487443/139124214-1ed58c7f-c5ab-4442-a207-082b46fd28cb.JPG)

## Widok podczas nieprawidłowo wypełnionego formularza:
![third](https://user-images.githubusercontent.com/75487443/139124223-19774e0c-e394-4827-8664-7ca15a73cec9.JPG)
