# Tehnologije:

* [Angular 12](https://angular.io)
* [Angular Material 12](https://material.angular.io)

# Izvor podataka:

* REST API:
  * https://my-json-server.typicode.com/msinkovic/BookRepository/db
  * Sastoji se od REST 4 endpointa
  * `/book`
    * sadrži podatke o knjigama, ima vezu prema izvoru podataka `author`
  * `/author`   
    * sadrži podatke o autorima
  * `/client`
    * sadrži podatke o korisnicima
  * `/client-book`
    * sadrži podatke o posudbama knjiga
    * ima vezu prema `book` i `client` izvoru podataka
  * Prema njemu se mogu raditi GET, POST, PUT, PATCH and DELETE pozivi
    * Promjene neće perzisitirati (jer se radi o JSON-u na mom GIT-u)

# Što je potrebno:

## Potrebno je kreirati aplikaciju koja ce se sastojati od sljedećih dijelova:

* Header
* Landing Page
* Main View
* Side Navigation
* Footer

### Header treba sadržavati:

* Naziv aplikacije, ikonu koja može proširiti ili smanjiti navigaciju, trenutni datum i vrijeme u formatu `dd.MM.yyyy. hh:mm:ss` gdje se vrijeme ažurira svake sekunde
* Ime ulogiranog korisnika

### Landing page treba sadržavati:

* Formu s poljima za ime i prezime korisnika te poljem za odabir role (`admin` ili `user`)
* Gumb za prijavu u aplikaciju

### Main dio treba sadržavati:
* Tablice sa podacima ovisno o tome što se odabere u navigaciji

### Side Navigation treba sadržavati:

* Ovisno o roli korisnika
  * Books (svi korisnici)
  * Authors (admin)
  * Clients (admin)
  * Home (svi korisnici)
  * Logout (svi korisnici)

### Books dio:

* Treba sadržavati tablicu s prikazom osnovnih podataka o knjigama
* Potrebno je omogućiti sortiranje po imenu i autoru
* Knjige mogu dodavati i brisati samo korisnici s rolom administratora
* Gumb za dodavanje knjige
  * Klikom na gumb otvara se dialog za dodavanje knjige
  * Autor se dodaje iz padajućeg izbornika
  * Knjiga ima naslov, autora, godinu izdanja, izdavača i ISBN

### Authors dio:

* Treba sadržavati tablicu sa ispisom podataka o autorima
* Potrebno je omogućiti sortiranje po imenu i prezimenu
* Autore mogu dodavati i brisati samo korisnici s rolom administratora
* Gumb za dodavanje autora
  * Klikom na gumb otvara se dijalog s formom za dodavanje autora
  * Autor ima ime, prezime i datum rođenja

### Clients dio:

* Treba sadržavati tablicu sa ispisom podataka o kontaktima
* Klijente mogu dodavati i brisati samo korisnici s rolom administratora
* Prilikom brisanja klijenta potrebno je dodati razlog brisanja
* Potrebno je u tablici prikazati koliko knjiga svaki klijent ima posuđeno
* Klikom na broj posuđenih knjiga otvara se dijalog s listom naslova posuđenih knjiga
* Gumb za dodavanje klijenta
  * Klikom na gumb otvara se dijalog s formom za dodavanje klijenta
  * Klijent ima ime, prezime, email, broj telefona i spol

### Home dio:
* Ovisno o roli ulogiranog korisnika prikazuje:
  * Za klijente:
    * Tablicu s posuđenim knjigama s datumom posuđivanja i krajnjim datumom vraćanja
      * Knjige s kojima se kasni trebaju biti ispisane crvenim tekstom
        * Datum vraćanja je prije današnjeg datuma
    
  * Za administratore
    * Tablicu sa svim posuđenim knjigama
      * Tablica uključuje
        * Filtriranje knjiga po nazivu ili autoru
        * Sortiranje po nazivu iliu autoru
      * Tablica sadrži naslov knjige, datum posuđivanja, krajnji datum vraćanja, ime i prezime klijenta koji je posudio knjigu i gumb `Returned`
        * Klikom na gumb `Returned` otvara se dijalog za potvrdu vraćanja nakon čeg se knjiga briše iz tablice
      * Knjige s kojima se kasni trebaju biti ispisane crvenim tekstom
    * Gumb za posuđivanje knjiga
      * Klikom na gumb otvara se forma s poljem za odabir knjige, poljem za odabir klijenta te s poljem za odabir datuma vraćanja knjige

### Logout dio:
* Vraća na Landing page

### Footer treba sadržavati:
* Copyright tekst i verziju aplikacije

# Napomene:

* Aplikacija mora biti responzivna - dobro se prikazivati na rezolucijama 1920x1080, 1280x1024 i 768x1024
* Aplikacija mora sadržavati loader/spinner kod promjene prozora
* Aplikacija mora sadržavati potrebne validacije na formama  (email. broj telefona, tekst)
* Aplikacija mora sadržavati 401 i 404 stranicu (Unauthorized i Not Found)
* Delete akcije moraju imati confirm dialog
* Aplikacija mora koristiti Angular Material komponente
