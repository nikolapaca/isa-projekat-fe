# OnlyBuns – frontend

Klijentski deo web aplikacije **OnlyBuns**, društvene mreže posvećene zecevima, urađene u okviru predmeta
**Internet softverske arhitekture (ISA)** (2025).

Backend se nalazi u repozitorijumu [isa-projekat](https://github.com/nikolapaca/isa-projekat).

## O projektu

Korisnici na OnlyBuns-u objavljuju slike svojih kunića sa opisom i lokacijom, lajkuju i komentarišu objave, prate
druge korisnike, pregledaju profile i dopisuju se u grupnim ćaskanjima. Administrator ima stranicu sa analitikom
korišćenja aplikacije.

## Tehnologije

- Angular 19 (Angular Material)
- Leaflet (mapa i izbor lokacije)
- Chart.js / ng2-charts i ApexCharts (grafikoni analitike)
- SockJS i STOMP (WebSocket komunikacija za ćaskanje)

## Pokretanje

Potreban je pokrenut backend (`http://localhost:8080`).

```
npm install
ng serve
```

Aplikacija je dostupna na `http://localhost:4200/`.

## Moj doprinos

### Dodavanje objave

- Komponenta `add-post` (`src/app/post/add-post`) sa formom za novu objavu: izbor slike, opis i lokacija
  (geografska dužina i širina) uz validaciju obaveznih polja (Reactive Forms).
- Prihvataju se samo fajlovi tipa slike; slika se prvo otprema na server, a zatim se kreira objava sa dobijenom
  putanjom slike.
- Lokacija se može uneti ručno ili izabrati klikom na mapu u modalnom prozoru (`app-map`).
- Servis `PostService`: metode `addPost`, `uploadImage` (otpremanje slike sa JWT tokenom u zaglavlju)
  i `getImage`.
- Na profilu korisnika dodato je dugme za dodavanje objave koje otvara formu u modalnom prozoru, a prikaz slika
  objava prebačen je na slike sa servera.
