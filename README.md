
# Projekt: Filtrowanie i Strojenie PID drona FPV 5 cali (Betaflight 4.6, PIDToolbox)

## Opis Repozytorium

Niniejsze repozytorium stanowi techniczną dokumentację procesu strojenia 5-calowego drona FPV. Przedstawiona metodologia i analiza danych bazuje głównie na materiałach edukacyjnych oraz oprogramowaniu **PID toolbox, prowadzonych przez Briana White'a**. Repozytorium zawiera zbiór materiałów, logów i zrzutów konfiguracji, które krok po kroku przedstawiają proces optymalizacji ustawień w oprogramowaniu Betaflight 4.6

## Cele Tuningu

Głównym celem przeprowadzonych prac było osiągnięcie następujących rezultatów poprzez precyzyjne strojenie filtrów i pętli PID:

*   Poprawa responsywności i precyzji sterowania.
*   Maksymalna eliminacja zjawiska **propwash** 

### Kryteria techniczne:

#### Filtracja:
*  Redukcja szumów częstotliwościowych do poziomu poniżej **-10dB** na wykresie spektralnym.
*  Gyro delay w okolicach **1.5ms**.
  
Należy pamiętać, że powyższe wartości są orientacyjne. Kluczowe jest znalezienie balansu, ponieważ zbyt agresywne filtrowanie wprowadza opóźnienia , natomiast zbyt słabe może prowadzić do przegrzewania się silników.

#### PID tuning:

## Specyfikacja

*   **Rama:** Mark4 5" (225mm)
*   **Kontroler Lotu (FC):** YSIDO F4 V3S PLUS
*   **Regulatory (ESC):** YSIDO  45A 4-in-1 (wgrane Bluejay)
*   **Silniki:** YSIDO 2205 2300KV
*   **Śmigła:** iFlight Nazgul F5 (5140) 3-łopatowe
*   **Akumulator:** CNHL 4S 1500mAh 100C

## Rodzaje Lotów testowych 

Dane do analizy zbierałem przy użyciu dwóch kluczowych metod:
### 1. Podstawowy  Wobble Test

Procedura Wykonania Testu:
Wystartuj i ustabilizuj drona w zawisie (hover).
Uruchom skrypt Wobble Test na nadajniku.
Podczas gdy test jest aktywny (~30 sekund), płynnie i powoli zmieniaj położenie przepustnicy (throttle).
Reguluj przepustnicę w takim zakresie, aby dron wznosił się i opadał o około 2-3 metry. Celem jest zapisanie w czarnej skrzynce danych z całego zakresu pracy silników.

#### Konfiuracja 
Metoda ta  polega na wygenerowaniu przez nadajnik ciągłych, sinusoidalnych ruchów w osiach Roll i Pitch.

żródło:

https://www.youtube.com/watch?v=NczSDkKn9pY&ab_channel=PIDtoolbox

Nalezy użyć wraz z trybem angle mode o okreśnych paramterach:

<img src="./angle_mode.PNG" alt="Ustawienia trybu Angle Mode w Betaflight" width="30%">


#### 2. Lot Weryfikacyjny 

1.  Wykonaj standardowy, swobodny lot w trybie Acro, unikając gwałtownych manewrów.
2.  Po wylądowaniu **natychmiast sprawdź temperaturę silników**. Powinny być co najwyżej lekko ciepłe.
    *   **Uwaga:** Jeśli silniki są gorące, nie przechodź do kolejnego etapu. Oznacza to problem ze zbut niskim filtrowaniem, który należy rozwiązać w pierwszej kolejności.

#### 3. Test Obciążeniowy full Throttle 

1.  Wykonaj **2-3 pełne przyspieszenia** , utrzymując przepustnicę wysokim poziomie przez kilka sekund.
2.  Podczas lotu na wysokiej przepustnicy wykonaj **serię szybkich obrotów**  w każdej osi:
   







