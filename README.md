<div align="center">

<img src="LibrusApp/Resources/Assets.xcassets/AppIcon.appiconset/icon.png" height="128px" alt="Ikona aplikacji">

# Dziennik

**Nieoficjalny klient Librus Synergia na iOS — port aplikacji [Szkolny.eu](https://github.com/szkolny-eu/szkolny-android)**

![Wersja iOS](https://img.shields.io/badge/iOS-17%2B-orange?style=for-the-badge&logo=apple&logoColor=white)
![Swift](https://img.shields.io/badge/Swift-5-F05138?style=for-the-badge&logo=swift&logoColor=white)
![SwiftUI](https://img.shields.io/badge/UI-SwiftUI-0A84FF?style=for-the-badge&logo=swift&logoColor=white)
![E-dziennik](https://img.shields.io/badge/e--dziennik-Librus-2EA44F?style=for-the-badge)
![Licencja](https://img.shields.io/badge/licencja-GPL--3.0-blue?style=for-the-badge&logo=gnu&logoColor=white)
![Status](https://img.shields.io/badge/status-beta-yellowgreen?style=for-the-badge)

</div>

## Ważna informacja

Ta aplikacja **nie jest oficjalną aplikacją Librus** i nie jest powiązana z Librus Sp. z o.o. ani z autorami Szkolny.eu.
To port części kodu otwartoźródłowej aplikacji [Szkolny.eu dla Androida](https://github.com/szkolny-eu/szkolny-android)
na iOS, ograniczony do dziennika **Librus® Synergia**.

Twórcy Szkolny.eu opisują w swoim repozytorium, że **firma Librus zabroniła im** publikowania aplikacji z obsługą Librusa
w sklepie Google Play. Dlatego **ta wersja nie jest i nie będzie publikowana w App Store**. Jest przeznaczona
do instalacji na własnych urządzeniach, do prywatnego użytku.

Aplikacja korzysta z tych samych mechanizmów co oryginał. **Może przestać działać** po zmianach po stronie Librusa.
Kod źródłowy oryginału pochodzi z lutego 2025 r.

Inne wersje: [CarPlay](https://github.com/wadamczewski/szkolny.eu-carplay), [Android Auto](https://github.com/wadamczewski/szkolny.eu-androidauto),
[LG webOS](https://github.com/wadamczewski/szkolny.eu-webos), [Android TV](https://github.com/wadamczewski/szkolny.eu-androidtv).

> [!NOTE]
> **Stan weryfikacji.** Sprawdzone na prawdziwym koncie (symulator, Xcode 27.1): logowanie loginem Synergii, ekran Start,
> oceny, plan lekcji, wiadomości i zakładka Więcej (terminarz, frekwencja, uwagi, ogłoszenia). **Nie sprawdzone:**
> logowanie Kontem Librus do końca, wysyłanie wiadomości, instalacja na fizycznym urządzeniu.

## O aplikacji

Dziennik to natywna aplikacja na iPhone'a i iPada, napisana w SwiftUI. Daje rodzicom i uczniom dostęp do danych z e-dziennika
Librus Synergia. Jedno Konto Librus może mieć kilka kont uczniowskich i łatwo się między nimi przełącza.

### Funkcje aplikacji

- **logowanie przez Konto Librus** (e-mail) na stronie portal.librus.pl. Aplikacja nie widzi hasła, a 2FA i CAPTCHA
  obsługuje sama strona Librusa.
- logowanie **loginem i hasłem Synergii** (np. `1234567u`) przez formularz synergia.librus.pl. Dane pobierane są
  przez `synergia.librus.pl/gateway/api`. Hasło jest zapisywane w pęku kluczy, bo bez niego nie da się odnowić sesji.
- **oceny** ze **średnimi ważonymi**, ocenami przewidywanymi i końcowymi, poprawami, kategoriami i komentarzami
- **plan lekcji** z nawigacją po tygodniach, odwołanymi lekcjami, zastępstwami i przeniesieniami
- **terminarz**: sprawdziany, kartkówki i inne wydarzenia
- **frekwencja** ze statystyką obecności
- uwagi, ogłoszenia szkolne, **szczęśliwy numerek**
- **wiadomości**: odebrane i wysłane, czytanie, **pobieranie załączników**, odpowiadanie i **wysyłanie** z wyborem odbiorców
- awaryjne otwarcie prawdziwej strony Synergii w aplikacji, gdyby wiadomości przestały się wczytywać
- **obsługa wielu profili** uczniów i wielu kont
- działanie **offline**: ostatnio pobrane dane są dostępne bez internetu
- tokeny logowania przechowywane w **pęku kluczy iOS**, tylko na tym urządzeniu

Czego (jeszcze) nie ma, a jest w oryginale: powiadomienia, widgety, synchronizacja w tle, zadania domowe, oceny
zachowania, opisowe i punktowe, własne wydarzenia, załączniki w wysyłanych wiadomościach, inne e-dzienniki niż Librus.

### Zrzuty ekranu

> Zrzuty przedstawiają **fikcyjne, wygenerowane dane** z wbudowanego trybu demo. Nie pokazują żadnego prawdziwego
> ucznia, nauczyciela ani szkoły.

<p align="center">
  <img src="docs/screenshots/01-start.png" width="240" alt="Ekran Start: szczęśliwy numerek i plan na dziś">
  <img src="docs/screenshots/02-oceny.png" width="240" alt="Oceny ze średnimi">
  <img src="docs/screenshots/03-przedmiot.png" width="240" alt="Szczegóły ocen z przedmiotu z poprawą">
</p>
<p align="center">
  <img src="docs/screenshots/04-plan.png" width="240" alt="Plan lekcji z nawigacją po tygodniach">
  <img src="docs/screenshots/05-wiadomosci.png" width="240" alt="Lista wiadomości">
  <img src="docs/screenshots/06-wiadomosc.png" width="240" alt="Wiadomość z załącznikiem">
</p>
<p align="center">
  <img src="docs/screenshots/07-wiecej.png" width="240" alt="Zakładka Więcej">
  <img src="docs/screenshots/08-frekwencja.png" width="240" alt="Frekwencja ze statystyką">
  <img src="docs/screenshots/09-start-ciemny.png" width="240" alt="Ekran Start w trybie ciemnym">
</p>

### Pobieranie

Gotowych plików do pobrania **nie ma**. Aplikację budujesz sam i instalujesz na swoich urządzeniach jednym z trzech sposobów:

| Sposób | Konto Apple | Ważność podpisu | Dla kogo |
|---|---|---|---|
| [Xcode + kabel](#sposób-1-xcode--kabel) | darmowe Apple ID | 7 dni | najprościej, na jedno urządzenie |
| [Apple Developer Program](#sposób-2-apple-developer-program) | płatne (99 USD/rok) | 1 rok | kilka urządzeń, bez cotygodniowego odświeżania |
| [AltStore / SideStore](#sposób-3-altstore--sidestore) | darmowe Apple ID | 7 dni, odświeżane automatycznie | bez Maca na co dzień |

Darmowe Apple ID pozwala mieć najwyżej 3 takie aplikacje na urządzeniu.

### Kompilacja

Do zbudowania aplikacji potrzebny jest **Mac z Xcode 16 lub nowszym** (darmowy, z App Store) i urządzenie z **iOS 17+**.
Po instalacji Xcode wykonaj jednorazowo:

```bash
sudo xcode-select -s /Applications/Xcode.app
sudo xcodebuild -license accept
xcodebuild -downloadPlatform iOS
```

Następnie skonfiguruj podpis:

1. Xcode → **Settings → Accounts → +** → zaloguj swoje Apple ID. Powstanie zespół „Personal Team”.
2. W pliku `Config/Signing.xcconfig` ustaw:
   - `DEVELOPMENT_TEAM`: Team ID (10 znaków). Jest widoczny w Xcode → Settings → Accounts albo w targecie
     **Dziennik → Signing & Capabilities → Team**.
   - `BUNDLE_ID_PREFIX`: unikalny identyfikator, np. `pl.twojenazwisko.dziennik`. Jeśli Xcode zgłosi, że jest zajęty, zmień go.

Projekt `Dziennik.xcodeproj` jest wygenerowany z pliku `project.yml` narzędziem [XcodeGen](https://github.com/yonaskolb/XcodeGen).
Po zmianach w `project.yml` wygeneruj go ponownie:

```bash
xcodegen generate
```

Wersję testową uruchomisz w symulatorze: otwórz `Dziennik.xcodeproj`, wybierz np. „iPhone 16” i naciśnij **▶ Run** (⌘R).

#### Sposób 1: Xcode + kabel

1. Podłącz iPhone'a kablem i na telefonie zaufaj komputerowi.
2. Na iPhonie włącz **Ustawienia → Prywatność i ochrona → Tryb dewelopera** (telefon się zrestartuje).
3. W Xcode wybierz swój telefon jako cel i naciśnij **▶ Run**.
4. Przy pierwszym uruchomieniu: **Ustawienia → Ogólne → VPN i zarządzanie urządzeniem →** Twój Apple ID → **Ufaj**.

Po 7 dniach aplikacja przestanie się uruchamiać, ale dane zostaną. Wtedy uruchom ją ponownie z Xcode.
W Xcode → Window → Devices and Simulators możesz włączyć „Connect via network”, żeby odświeżać przez Wi-Fi.

#### Sposób 2: Apple Developer Program

Zarejestruj urządzenia (UDID) na [developer.apple.com](https://developer.apple.com/account/resources/devices/list).
Xcode robi to sam dla podłączonych urządzeń. Potem wybierz **Product → Archive → Distribute App → Release Testing / Ad Hoc**.
Powstały `.ipa` zainstalujesz przez Finder (przeciągnij na urządzenie), Apple Configurator albo Xcode → Devices and Simulators → „+”.

#### Sposób 3: AltStore / SideStore

[AltStore](https://altstore.io) i [SideStore](https://sidestore.io) podpisują aplikację Twoim Apple ID i co tydzień
odświeżają ją w tle. Zbuduj niepodpisany plik `.ipa`:

```bash
./scripts/build-ipa.sh
```

Prześlij `build/Dziennik.ipa` na telefon (AirDrop albo aplikacja Pliki) i otwórz go w AltStore/SideStore → **My Apps → +**.

#### Testy

Logika aplikacji (logowanie, API, parsery wiadomości) jest w pakiecie `Packages/LibrusKit` i kompiluje się także na macOS.
Testy działają na **fikcyjnych, wygenerowanych danych**:

```bash
cd Packages/LibrusKit && swift run LibrusKitCheck
```

Tryb demo z fikcyjnymi danymi (do zrzutów ekranu i pracy nad wyglądem, tylko w wersji Debug): w Xcode
Product → Scheme → Edit Scheme → Run → Arguments dodaj `-DemoData`. Albo uruchom w symulatorze:

```bash
xcrun simctl launch booted pl.prywatny.dziennik.app -DemoData
```

<details>
<summary>Struktura projektu</summary>

```
project.yml                 specyfikacja projektu dla XcodeGen
Config/Signing.xcconfig     Team ID i prefiks bundle ID (do uzupełnienia)
LibrusApp/                  aplikacja SwiftUI
  App/                      punkt wejścia, zakładki
  Auth/                     logowanie (WebView portalu, login Synergii)
  State/                    AppModel, Keychain, cache
  Views/                    ekrany: Start, Oceny, Plan, Wiadomości, Więcej
Packages/LibrusKit/         logika niezależna od UI
  Auth/                     OAuth portalu i API, odświeżanie tokenów
  API/                      klient API 2.0 i parsery (port LibrusApi*.kt)
  Synergia/                 sesja Synergii i wiadomości (scraping HTML)
scripts/build-ipa.sh        niepodpisany .ipa dla AltStore/SideStore
```

</details>

## Prywatność

- Logując się przez Konto Librus, wpisujesz dane na stronie portal.librus.pl. Aplikacja odbiera tylko kod autoryzacyjny
  `app://librus?code=…`, tak jak oficjalna aplikacja.
- Hasło Synergii trafia tylko do api.librus.pl / synergia.librus.pl. Jest zapisywane w pęku kluczy (tylko to urządzenie),
  bo sesja Synergii wygasa i trzeba się logować ponownie. Librus wyłączył logowanie tokenem
  (`OAuth/Token` zwraca `unsupported_grant_type`), więc nie da się tego uniknąć. Konto Librus (e-mail) hasła nie zapisuje.
- Tokeny są w pęku kluczy (Keychain), tylko na tym urządzeniu. Pobrane dane są zapisywane z ochroną plików iOS.
- Kod aplikacji łączy się wyłącznie z `*.librus.pl`, nie z serwerami Szkolny.eu. Strona logowania w WebView może ładować
  zasoby zewnętrzne, np. Google reCAPTCHA. Przy budowaniu Xcode pobiera z GitHuba bibliotekę SwiftSoup.
- Opcja **Wyloguj** w zakładce Więcej usuwa tokeny i dane ucznia z telefonu.

## Gdy coś nie działa

- **Logowanie przez Konto Librus**: odśwież stronę przyciskiem ⟳. Komunikat „rejected_client” oznacza, że Librus
  zmienił identyfikator aplikacji. Porównaj wtedy stałe z `Constants.kt` w repozytorium szkolny-android
  z plikiem `LibrusConstants.swift`.
- **Wiadomości**: jeśli lista się nie wczytuje, użyj **⋯ → Otwórz w Synergii**. Selektory HTML są w `SynergiaWeb.swift`.
- Część sekcji (np. szczęśliwy numerek) może być wyłączona w szkole. Wtedy jest pusta.

## Współpraca

Poprawki i zgłoszenia błędów są mile widziane. Do zgłoszenia dołącz komunikat błędu z aplikacji.
**Nie wklejaj w zgłoszeniach danych logowania ani prawdziwych danych uczniów.**

Za oryginalną aplikację i opracowanie komunikacji z Librusem odpowiadają autorzy
[Szkolny.eu](https://github.com/szkolny-eu/szkolny-android). Pytania dotyczące oryginału kieruj do nich.

## Licencja

Dziennik, tak jak Szkolny.eu, jest publikowany na licencji [GNU GPLv3](LICENSE). W szczególności:
- Możesz modyfikować i usprawniać kod aplikacji.
- Możesz dystrybuować zbudowane wersje, ale wraz z kodem źródłowym.
- Musisz opublikować wszelkie wprowadzone zmiany.
- Nie możesz zmieniać licencji ani informacji o prawach autorskich oryginału.

Nazwa Librus® jest znakiem towarowym jej właściciela. Używamy jej wyłącznie w celu wskazania, z jakim e-dziennikiem
współpracuje aplikacja.

*Kod został przygotowany z pomocą AI. Przejrzyj go przed użyciem.*
