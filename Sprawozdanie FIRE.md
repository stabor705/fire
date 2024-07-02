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