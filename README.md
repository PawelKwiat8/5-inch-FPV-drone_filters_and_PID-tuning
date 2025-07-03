
# Projekt: Filtrowanie i Strojenie PID drona FPV 5 cali (Betaflight 4.6, PIDToolbox)

## Opis Repozytorium

Niniejsze repozytorium stanowi techniczną dokumentację procesu strojenia 5-calowego drona FPV. Przedstawiona metodologia i analiza danych bazuje głównie na materiałach edukacyjnych oraz oprogramowaniu **PID toolbox, prowadzonych przez Briana White'a**. Repozytorium zawiera zbiór materiałów, logów i zrzutów konfiguracji, które krok po kroku przedstawiają proces optymalizacji ustawień w oprogramowaniu Betaflight 4.6

## Cele Tuningu

Głównym celem przeprowadzonych prac było osiągnięcie następujących rezultatów poprzez precyzyjne strojenie filtrów i pętli PID:

*   Poprawa responsywności i precyzji sterowania.
*   Maksymalna eliminacja zjawiska `propwash` (drgań w turbulentnym powietrzu).

Aby to osiągnąć, w trakcie tego procesu dążyłem do spełnienia następujących kryteriów technicznych:

Filtracja:
*  Redukcja szumów częstotliwościowych do poziomu poniżej **-10dB** na wykresie spektralnym.
*  Gyro delay w okolicach **1.5ms**.
  
Należy pamiętać, że powyższe wartości są orientacyjne. Kluczowe jest znalezienie balansu, ponieważ zbyt agresywne filtrowanie wprowadza opóźnienia (latency), natomiast zbyt słabe może prowadzić do przegrzewania się silników.
żródło: materiały 

PID tuning:


## Specyfikacja

*   **Rama:** Mark4 5" (225mm)
*   **Kontroler Lotu (FC):** YSIDO F4 V3S PLUS
*   **Regulatory (ESC):** YSIDO  45A 4-in-1 (wgrane Bluejay)
*   **Silniki:** YSIDO 2205 2300KV
*   **Śmigła:** iFlight Nazgul F5 (5140) 3-łopatowe
*   **Akumulator:** CNHL 4S 1500mAh 100C

## Metodologia Testów

Dane do analizy zbierałem przy użyciu dwóch kluczowych metod:
1. Wobble Test
   
Metoda ta  polega na wygenerowaniu przez nadajnik ciągłych, sinusoidalnych ruchów w osiach Roll i Pitch.
https://www.youtube.com/watch?v=NczSDkKn9pY&ab_channel=PIDtoolbox

Nalezy jej uzywac w trybe angle mode o okreśnych paramterach:



2.  Testy w full Throttle


