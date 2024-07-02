# Sprawozdanie FIRE

## Miłosz Dubiel
Po zainicjalizowaniu projektu vizualizacji (`fire-visualization`) przez Kacpra przygotowałem środowisko do dalszej pracy: skonfigurowałem formatter i umożliwiłem odświeżanie aplikacji w trybie deweloperskim po wprowadzeniu zmian w kodzie i zapisaniu ich, bez konieczności ponownego uruchomienia aplikacji.

Następnie, wybrałem i dopasowałem do naszych wymagań (związanych między innymi z językiem programowania) wzorzec układu projektu, na podstawie którego zdecydowaliśmy się rozwijać interfejs użytkownika.

Wprowadziłem obsługę map:
Jako pierwsza powstała główna mapa wyświetlająca las, jego granice wraz z nałożoną siatką sektorów. W dalszych etapach pracy rozszerzyłem tę mapę o możliwość wyświetlenia danych sektora po najechaniu na niego kursorem, a następnie o możliwość wybrania konkretnego sektora (poprzez kliknięcie) w celu wyświetlenia jego danych poniżej mapy, w sposób umożliwiający łatwiejszy dostęp do parametrów sektora wraz z możliwością edycji.

Drugi komponent zawierający mapę powstał w ramach możliwości tworzenia nowych konfiguracji lasów. Zaimplementowałem tam mapę, dzięki której użytkownicy mogą interaktywnie zaznaczać granice lasu. Do tej funkcjonalności zaimplementowałem również logikę stojącą za automatycznym podziałem lasów na sektory.

Kolejne mapy, które stworzyłem, znajdują się w obsłudze dodawania czujników, kamer, zastępów strażackich i patrolów leśników. Ich zadaniem jest możliwość zaznaczenia położenia danego obiektu na terenie sektora.
Równocześnie, rozszerzyłem główną mapę o wizualizację czujników, kamer, zastępów strażackich i patrolów leśników w każdym sektorze. Zaimplementowałem również logikę stojącą za obsługą tej funkcjonalności, tzn. przypisywanie obiektu do sektora bazując na jego lokalizacji i granicach wszystkich sektorów.

Ponadto, miałem też swój wkład w drobne poprawki w formularzach parametrów sektora i obsłudze zapisywania nowych konfiguracji, jak również obsłudze stanu konfiguracji mapy w module wizualizacji w trakcie działania programu.

Ostatnim moim zadaniem w module interfejsu użytkownika było ustanowienie połączenia z backendową częścią aplikacji i wprowadzenie możliwości uruchomienia symulacji.

Po zakończeniu pracy nad modułem wizualizacji, zintegrowałem trzy moduły: wizualizację, backend oraz symulację i wprowadziłem wymagane poprawki po stronie wizualizacji oraz backendu, aby proces symulacji przebiegał poprawnie.

Wykonałem również statyczną analizę kodu w module wizualizacji, której wyniki są zamieszczone poniżej:

TODO zrobić zrzuty ekranu z SonarQube'a

## Kacper Cienkosz

Stworzenie środowiska:
Na początku projektu przygotowałem środowisko w `fire-visualization` łącząc Reacta opakowanego w Webpack z Electronem.

Sekcja workspace:
Następnie zająłem się stworzeniem elementu _Workspace_, który polegał na zmianie designu i zawartości panelu po lewej stronie. Dodałem przyciski umożliwiające dodanie nowej konfiguracji, dodanie nowego folderu oraz otworzenie workspace'a w programie. Stworzyłem też system zarządzania elementami workdpace'u będący reprezentacją systemu plików w bazie NoSQL.

Serwis bazodanowy:
Kolejnym etapem było stworzenie mikroserwisu `fire-configurations` będącego aplikacją FastAPI z bazą MongoDB. Stworzyłem logikę przechowywania danych, która reprezentowała drzewiasty system plików. Mikroserwis pozwala na dodawanie, usuwanie (niedostępne po stronie aplikacji `fire-visualization`), modyfikowanie i wyszukiwanie wpisów. Dodatkowo możliwe jest pobranie wszystkich dzieci danego elementu systemu plików. W ten sposób udało się zapewnić wymaganiem, jakim był sysyem bazodanowy.

Nowe konfiguracje, foldery i otwieranie workspaceów:
Dalszym etapem mojej pracy było dostosowanie systemu plików w `fire-visualization` tak, by współpracował sprawnie z `fire-configurations`. Stworzyłem również modale pozwalające na tworzenie nowych konfiguracji, otwieranie workspace'ów oraz tworzenie folderów. Otwieranie workspace'ów korzysta z tego samego elementu wyświetlającego struktórę plików, lecz inaczej obsługuje kliknięcia. Modal ten pobiera dane z `fire-configurations`. Podobnie działa tworzenie folderów, jednak tutaj jest dodatkowe pole zawierające nazwę folderu. Modal tworzący konfigurację działa bardzo podobnie, jednak zawiera mapę, którą dodał Miłosz na podstawie swoich wcześniejszych doświadczeń z mapami.

Zapisywanie danych mapy:
Następnym krokiem było umożliwienie edycji oraz zapisu danych mapy w bazie danych. Wymagało to przerobienia formularzy wcześniej przygotowanych przez Staszka. Od tego momentu dla wszystkich sektorów mogły być edytowane warunki początkowe.

Dodawanie sensorów:
Dalej stworzyłem modale umożliwiające dodanie elementów takich jak czujniki, kamery, brygady strażackie i patrole leśników do konfuguracji i zapisanie konfiguracji z nowymi czujnikami w bazie danych. Wymagało to również przerobienia formularzy wcześniej przygotowanych przez Staszka.

Poprawa wyświetlania:
Ostatnim etapem było stworzenie przejrzystego interfejsu użytkownika umożliwiającego na wypisywanie wszystkich czujników, kamer, brygad strażackich i patroli leśników w formie zwięzłej i czytelnej listy. Dodałem też możliwość usuwania poszczególnych elementów.

Miałem również wkład w otwieranie nowej konfiguracji w programie.

Dodatkowo, napisałem wszystkie funkcje odpowiadające za połączenie serwisu bazodanowego i aplikacji.
