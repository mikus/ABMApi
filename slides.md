class: center, middle

# ABM API

???

* pół na pół: sztuka i nauka
* wyklarowały się dobre praktyki
* głównie na bazie HTTP (ale nie jest to konieczność)

---

## API REST-owe

* REpresentational State Transfer
* Roy Fielding – [dysertacja doktorska](http://www.ics.uci.edu/~fielding/pubs/dissertation/rest_arch_style.htm)
* Styl architektoniczny oparty o zasoby
    * zasaoby a nie akcje (jak w SOAP)
    * rzeczowniki zamiast czasowników
    * /getUserData?userId=123 -> /user/123/data
    * zasób odseparowany od reprezentacji (np. DB -> XML)
* Więcej w [prezentacji](https://github.com/mikus/RESTfulAPI)


---

## Metody HTTP

* Odpowiadają za dużą część "jednolitego interfejsu"
* Wprowadzenie akcji na rzeczownikowych zasobach

Metoda     | CRUD           | /customers                                | /customers/{id}
-----------|----------------|-------------------------------------------|--------------------------------------------
**POST**   | Create         | 201 (Created), Location: /customers/{id}  | 404 (Not Found), 409 (Conflict)
**GET**    | Read           | 200 (OK), lista klientów                  | 200 (OK), pojedynczy klient, 404 (Not Found)
**PUT**    | Update/Replace | 404 (Not Found), chyba, że wszystko       | 200 (OK), 204 (No Content), 404 (Not Found)
**PATCH**  | Update/Modify  | 404 (Not Found), chyba, że wszystko       | 200 (OK), 204 (No Content), 404 (Not Found)
**DELETE** | Delete         | 404 (Not Found), chyba, że wszystko       | 200 (OK), 204 (No Content), 404 (Not Found)

---

## Wymagania wstępne

* Konto na [test.e-abm.pl](http://test.e-abm.pl)
* [Dokumentacja do ABM API](http://e-abm.com/api_documentation.html)
* [Starter](https://dev.stat/confluence/pages/viewpage.action?pageId=22118410)
* Narzędzie do wywołań REST-owych
    * [cURL](https://curl.haxx.se/) / [HTTPie](https://httpie.org/)
    * [PostMan](https://www.getpostman.com/) / [RESTClient](http://restclient.net/)
    * [Insomnia](https://insomnia.rest)

---

## Autoryzacja

* OAuth 2.0
* Logowanie
* Token do API – generowany na stronie
* Nagłówek autoryzacyjny

```http
Authorization: Bearer eyJhbGciOiJIUz...
```

---

## Zasoby

`https://test.e-abm.pl/api/v1/`

* `/data`
* `/projects`
* `/models`
* `/scoring`

---

### Dane

* listowanie tabel
* import (csv, db)
* eksport (csv, db)
* kasowanie

---

### Projekty

* listowanie projektów
* tworzenie
* kopiowanie
* zmiana ustawień
* uruchamianie / sprawdanie statusu
* informacje o projekcie / moduły / statystyki
* eksport kodu scoringowego
* scorowanie wsadowowe / sprawdzanie statusu
* kasowanie

---

### Modele

* jedno wywołanie
  * import danych
  * utworzenie projektu
  * uruchomienie projektu
* sprawdzenie statusu
* pobranie wyników

---

### Scorowanie

* wdrożenie projektu do RTD - **nowe Id**
* listowanie wdrożonych projektów
* scorowanie real time

---

class: center, middle

# Pytania?
