Program do automatycznego logowania czasu pracy w Jira


Używanie:
1. Uruchom program "jira_bot.exe" (możesz zrobić skrót do pliku, jak do każdej innej aplikacji)
2. W konsoli wpisz cyfrowo o której zaczynasz pracę (np. 7, 8 lub 9)
3. Program automatycznie uzupełni czas pracy w dniu dzisiejszym od godziny zaczęcia pracy, na systemach z pliku "config.json"
4. Skrypt doda kafelki w dniu następnym, więc trzeba ręcznie je przeciągnąć na dzień dzisiejszy i kliknąć "Log work" (automatycznie powinna się dodać rola "Service Desk")

Ewentualne błędy zgłaszaj na Microfot Teams do Filipa Mickiewicza



Konfiguracja logowania:
Token jest używany zamiast loginu i hasła, należy go wcześniej utworzyć i dodać do pliku config.json
1. Wejść na stronę https://jira.coi.gov.pl/
2. Zalogować się
3. Wejść w "Profile" (prawy górny róg)
4. Wejść w "Personal Access Tokens"
5. Kliknąć "Create token"
6. Wpisać jaką się chce nazwę tokena
7. Odznaczyć "Automatic expiry"
8. Kliknąć "Create"
9. Skopiować ciąg znaków
10. Wkleić w pliku config.json > "token": "skopiowany_ciąg"

Konfiguracja systemów:
W "config.json" można ustawić na jakich systemach i po ile godzin program będzie logować czas pracy
1. Wejdź lub stwórz plik "config.json"
2. W "systems" możesz dodać więcej syststemów/usunąć te które są
3. Dodany system powinien wyglądać tak:
    "dowolna nazwa, np. cepik": {
        "code": "kod z jiry, np. ZKOUU-644",
        "time_spent": "poświęcony czas, np. 7h 15m",
        "comment": "komentarz, np. Obsługa infolinii i zgłoszeń dotyczących projektu CEPIK"
    }
4. Systemy oddziela się od siebie za pomocą przecinka (,) po ostatnim nawiasie klamrowym
5. Przykładową konfigurację można sprawdzić w "config_preview.json"



Przykładowy wygląd pliku "config.json":
{
    "token": "xxxxxxxxxxxxxx",
    "systems": {
        "cepik": {
            "code": "ZKOUU-644",
            "time_spent": "7h",
            "comment": "infolinia, maile"
        },
        "pz": {
            "code": "ZKOUU-662",
            "time_spent": "1h",
            "comment": "infolinia"
        }
    }
}