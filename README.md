# QRReview - System Opinii Restauracji

## Opis projektu
QRReview to aplikacja webowa umożliwiająca użytkownikom wystawianie opinii o restauracjach poprzez skanowanie kodów QR. Po zeskanowaniu kodu QR użytkownik zostanie przekierowany na dedykowaną stronę internetową do wystawienia opinii. Użytkownicy mogą również przeglądać opinie innych osób. Administratorzy mają dostęp do panelu zarządzania opiniami, gdzie mogą akceptować lub usuwać opinie oraz konfigurować automatyczną akceptację.

## Wymagania funkcjonalne
### Dla użytkownika niezalogowanego:
1. Możliwość wystawienia opinii o restauracji.
2. Możliwość przeglądania opinii innych użytkowników.

### Dla administratora (zalogowanego użytkownika):
1. Możliwość akceptowania opinii.
2. Możliwość usuwania opinii.
3. Opcja włączenia automatycznej akceptacji dla nowych opinii.

## Wymagania niefunkcjonalne
1. **Bezpieczeństwo**: Szyfrowanie danych użytkownika i zabezpieczenie panelu administratora.
2. **Responsywność**: Aplikacja dostępna na urządzenia mobilne i desktopowe.

## Potencjalne ryzyka
1. Możliwe trudności w konfiguracji zabezpieczeń aplikacji.
2. Brak doświadczenia z generowaniem kodów QR.

## Lista zadań
1. **Utworzenie projektu w .NET z Reactem**:
   - Skonfigurowanie środowiska dla aplikacji .NET Core z interfejsem React.
   - Integracja Reacta z backendem .NET.

2. **Implementacja API w .NET**:
   - Stworzenie modeli danych dla opinii i użytkowników.
   - Opracowanie kontrolerów do zarządzania opiniami (dodawanie, przeglądanie, akceptacja/usuwanie).
   - Implementacja mechanizmów autoryzacji i uwierzytelniania dla administratora.

3. **Budowa interfejsu użytkownika w React**:
   - Opracowanie głównego panelu użytkownika z opcją przekierowania na stronę logowania.
   - Implementacja formularza do wystawiania opinii.
   - Stworzenie widoku do przeglądania opinii innych użytkowników.

4. **Integracja kodów QR**:
   - Implementacja funkcji przekierowania użytkownika po zeskanowaniu kodu QR.
   - Generowanie unikalnych kodów QR dla każdej restauracji.

5. **Budowa panelu administracyjnego w React**:
   - Implementacja strony logowania dla administratora.
   - Opracowanie interfejsu do akceptowania i usuwania opinii.
   - Dodanie opcji konfiguracji automatycznej akceptacji opinii.

6. **Konfiguracja zabezpieczeń aplikacji**:
   - Implementacja szyfrowania danych użytkownika.
   - Zabezpieczenie panelu administratora przed nieautoryzowanym dostępem.

7. **Wdrożenie aplikacji na hosting**:
   - Wybór odpowiedniego hostingu dla aplikacji .NET z Reactem.
   - Konfiguracja środowiska produkcyjnego i bazy danych.
   - Wdrożenie aplikacji i monitorowanie jej działania.

## Diagram architektury aplikacji

```mermaid
flowchart TD
    subgraph Użytkownik
        A[Panel główny]
        B[Formularz opinii]
        C[Lista opinii]
    end

    subgraph Administrator
        D[Strona logowania]
        E[Panel administracyjny]
    end

    subgraph Frontend[React]
        A
        B
        C
        D
        E
    end

    subgraph Backend[.NET API]
        F[Kontroler opinii]
        G[Kontroler autoryzacji]
    end

    subgraph "Baza Danych"
        H[Opinie]
        I[Użytkownicy]
    end

    A -->|Przekierowanie| B
    A --> C
    B -->|Dodaj opinię| F
    C -->|Pobierz opinie| F
    D -->|Logowanie| G
    E -->|Zarządzaj opiniami| F

    F --> H
    G --> I
    F <-->|Zapytania| H
    G <-->|Zapytania| I

