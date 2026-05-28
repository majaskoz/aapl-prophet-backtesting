# Algorytmiczna Strategia Inwestycyjna: Apple Inc. (AAPL)

Projekt swingowej strategii inwestycyjnej dla spółki **Apple (AAPL)** łączący prognozowanie szeregów czasowych (**Meta Prophet**) z technicznymi filtrami momentum i zmienności (RSI, SMA, ATR).

## Wyniki Backtestu (Okres Testowy: 2024)
Strategia wyraźnie pokonała rynek (regresja out-of-sample) przy niskim poziomie ryzyka:

*   **Wynik strategii:** `+8.88%`
*   **Wynik Kup i Trzymaj (Buy & Hold):** `-2.44%`
*   **Alfa:** `+9.04 pp.`
*   **Profit Factor:** `2.23`
*   **Max Drawdown (Maksymalne obsunięcie):** `-3.47%`
*   **Sharpe Ratio:** `1.64`

---

## Interaktywny Wykres i Prezentacja
**[ZOBACZ INTERAKTYWNY WYKRES TRANSAKCJI](TUTAJ_WKLEJ_LINK_DO_GITHUB_PAGES)**  
*(Pełna wizualizacja krzywej kapitału, historii pozycji oraz dynamicznych poziomów SL/TP).*

---

## Jak to działa w skrócie?
1.  **Feature Engineering:** Pobranie danych przez `yfinance` (2020–2024) i wyliczenie wskaźników technicznych (RSI, SMA_20, ATR).
2.  **Modelowanie (Prophet):** Trening modelu na latach 2020–2023 z użyciem wskaźników jako zewnętrznych regresorów. Hiperparametry dobrano za pomocą Grid Search (optymalizacja MAE).
3.  **Egzekucja:** Pozycja długa (Long) otwierana jest tylko przy prognozowanym wzroście, gdy cena jest nad SMA_20, a rynek nie jest wykupiony (RSI < 70). Dodatkowy filtr ATR odrzuca sygnały przy niskiej zmienności.

## Tech Stack
*   Python (Prophet, Backtesting.py, ta, yfinance, Pandas, NumPy, Scikit-learn)

## Szybki start
```bash
git clone [https://github.com/majaskoz/aapl-prophet-backtesting.git](https://github.com/majaskoz/aapl-prophet-backtesting.git)
pip install prophet backtesting ta yfinance pandas numpy scikit-learn
