# Java Chat Application - Socket-Based Communication

> **Uwaga:** To repozytorium zostało utworzone jako projekt edukacyjny mający na celu rozwinięcie umiejętności programowania w Javie, ze szczególnym naciskiem na programowanie sieciowe, wielowątkowość i architekturę klient-serwer.

## Opis projektu

To repozytorium zawiera implementację aplikacji czatu w Javie wykorzystującej gniazda sieciowe (sockets) do komunikacji. Projekt składa się z dwóch głównych komponentów:

### 🖥️ Serwer czatu (`Server`)
- Nasłuchuje na porcie 8020
- Obsługuje wielu klientów jednocześnie za pomocą wielowątkowości
- Zarządza połączeniami klientów i ich identyfikacją
- Umożliwia przesyłanie wiadomości broadcast do wszystkich użytkowników
- Wspiera prywatne wiadomości między użytkownikami

### 💬 Klient czatu (`Client`)
- Łączy się z serwerem przez localhost:8020
- Używa dwóch oddzielnych wątków:
  - Wątek odczytu - odbiera wiadomości z serwera
  - Wątek zapisu - wysyła wiadomości do serwera
- Pozwala na interaktywną komunikację przez konsolę

## Struktura projektu

```
ChatServerClient/
├── src/main/java/pl/G0bi74/
│   ├── Main.java                    # Główna klasa (Hello World)
│   ├── Server/
│   │   ├── ServerMain.java          # Punkt wejścia serwera
│   │   ├── Server.java              # Logika serwera
│   │   └── ClientHandler.java       # Obsługa pojedynczego klienta
│   └── Client/
│       ├── ClientMain.java          # Punkt wejścia klienta
│       ├── Client.java              # Logika klienta
│       └── ServerHandler.java       # Obsługa komunikacji z serwerem
└── pom.xml                          # Konfiguracja Maven
```

## Technologie

- **Java 22** - Język programowania
- **Maven** - Zarządzanie zależnościami i budowanie projektu
- **Java Sockets** - Komunikacja sieciowa
- **Java Threads** - Obsługa wielowątkowości
- **Java I/O Streams** - Przesyłanie danych

## Funkcjonalności

### ✅ Zaimplementowane funkcje:

1. **Wielowątkowy serwer** - obsługa wielu klientów jednocześnie
2. **Identyfikacja użytkowników** - każdy klient podaje login przy połączeniu
3. **Wiadomości broadcast** - wysyłanie wiadomości do wszystkich użytkowników
4. **Wiadomości prywatne** - wysyłanie wiadomości do konkretnego użytkownika (składnia: `/login wiadomość`)
5. **Powiadomienia systemowe** - informowanie o dołączeniu/opuszczeniu czatu przez użytkowników
6. **Graceful disconnect** - poprawne zamykanie połączeń po wpisaniu "bye"

## Jak uruchomić

### Wymagania
- Java 22 lub wyższa
- Maven

### Uruchomienie serwera

```bash
# Skompiluj projekt
mvn clean compile

# Uruchom serwer
mvn exec:java -Dexec.mainClass="pl.G0bi74.Server.ServerMain"
```

Serwer uruchomi się na porcie **8020** i będzie oczekiwał na połączenia klientów.

### Uruchomienie klienta

W osobnym terminalu:

```bash
# Uruchom klienta
mvn exec:java -Dexec.mainClass="pl.G0bi74.Client.ClientMain"
```

Po uruchomieniu:
1. Podaj swój login
2. Możesz wysyłać wiadomości do wszystkich lub do konkretnego użytkownika
3. Aby wysłać prywatną wiadomość użyj: `/login_odbiorcy treść wiadomości`
4. Wpisz `bye` aby zakończyć połączenie

## Przykład użycia

**Terminal 1 (Serwer):**
```
[Serwer nasłuchuje na porcie 8020]
[user1, user2]
```

**Terminal 2 (Klient 1):**
```
user1
user1: Witam wszystkich!
user2: Cześć!
Private MSG from user1: Cześć prywatnie!
bye
```

**Terminal 3 (Klient 2):**
```
user2
user2: Cześć!
user1: Witam wszystkich!
/user1 Cześć prywatnie!
bye
```

## Cele edukacyjne

Ten projekt został stworzony w celu nauki i praktyki następujących koncepcji:

- **Programowanie sieciowe** - wykorzystanie Java Sockets do komunikacji TCP/IP
- **Wielowątkowość** - równoczesna obsługa wielu klientów i operacji I/O
- **Architektura klient-serwer** - projektowanie rozproszonych systemów
- **Obsługa strumieni I/O** - praca z BufferedReader, PrintWriter, Scanner
- **Zarządzanie stanem** - śledzenie połączonych klientów i ich sesji
- **Protokoły komunikacyjne** - implementacja prostego protokołu wiadomości

## Potencjalne rozszerzenia

Projekt może być rozwijany o:
- [ ] GUI dla klienta (Swing/JavaFX)
- [ ] Szyfrowanie komunikacji
- [ ] Pokoje czatowe
- [ ] Historia wiadomości
- [ ] Autoryzacja użytkowników
- [ ] Przesyłanie plików
- [ ] Emoji i formatowanie wiadomości

## Autor

G0bi74

## Licencja

Projekt edukacyjny - do użytku osobistego i nauki.
