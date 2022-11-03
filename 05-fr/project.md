# System aukcyjny

## Wprowadzenie

Specyfikacja wymagań funkcjonalnych w ramach informatyzacji procesu sprzedaży produktów w oparciu o mechanizm aukcyjny.

## Procesy biznesowe

---
<a id="bc1"></a>
### BC1: Sprzedaż aukcyjna

**Aktorzy:** [Sprzedający](#ac1), [Kupujący](#ac2)

**Opis:** Proces biznesowy opisujący sprzedaż za pomocą mechanizmu aukcyjnego. |

**Scenariusz główny:**
1. [Sprzedający](#ac1) wystawia produkt na aukcję. ([UC1](#uc1))
2. [Kupujący](#ac2) oferuje kwotę za produkt wyższą od aktualnie najwyższej oferty. ([BR1](#br1))
3. [Kupujący](#ac2) wygrywa aukcję ([BR2](#br2))
4. [Kupujący](#ac2) przekazuje należność Sprzedającemu.
5. [Sprzedający](#ac1) przekazuje produkt Kupującemu.

**Scenariusze alternatywne:**

2.A. Oferta Kupującego została przebita, a [Kupujący](#ac2) pragnie przebić aktualnie najwyższą ofertę.
* 2.A.1. Przejdź do kroku 2.

3.A. Czas aukcji upłynął i [Kupujący](#ac2) przegrał aukcję. ([BR2](#br2))
* 3.A.1. Koniec przypadku użycia.

---

## Aktorzy

<a id="ac1"></a>
### AC1: Sprzedający

Osoba oferująca towar na aukcji.

<a id="ac2"></a>
### AC2: Kupujący

Osoba chcąca zakupić produkt na aukcji.


## Przypadki użycia poziomu użytkownika

### Aktorzy i ich cele

[Sprzedający](#ac1):
* [UC1](#uc1): Wystawienie produktu na aukcję
* [UC2](#uc2): Sprawdzenie aktualnie najwyższej oferowanej kwoty za produkt
* [UC3](#uc3): Sprawdzenie historii oferowanych kwot za produkt
* [UC4](#uc4): Sprawdzenie informacji o czasie pozostałym do końca aukcji
* [UC5](#uc5): Sprawdzenie danych do wysyłki osoby, która wygrała aukcję

[Kupujący](#ac2)
* [UC1](#uc1): Sprawdzenie dostępnych aukcji
* [UC2](#uc2): Wybranie interesującej aukcji
* [UC3](#uc3): Sprawdzenie najwyższej oferowanej kwoty za daną aukcję
* [UC4](#uc4): Zaoferowanie kwoty wyżeszj od aktualnie najwyższej
* [UC5](#uc5): Sprawdzenie informacji o stanie aukcji
* [UC6](#uc6): Sprawdzenie informacji o czasie pozostałym do końca aukcji
* [UC7](#uc7): Przekazanie należności sprzedającemu po wygranej aukcji

---
<a id="uc1"></a>
### UC1: Wystawienie produktu na aukcję

**Aktorzy:** [Sprzedający](#ac1)

**Scenariusz główny:**
1. [Sprzedający](#ac1) zgłasza do systemu chęć wystawienia produktu na aukcję.
2. System prosi o podanie danych produktu i ceny wywoławczej.
3. [Sprzedający](#ac1) podaje dane produktu oraz cenę wywoławczą.
4. System weryfikuje poprawność danych.
5. System informuje o pomyślnym wystawieniu produktu na aukcję.

**Scenariusze alternatywne:**

4.A. Podano niepoprawne lub niekompletne dane produktu.
* 4.A.1. System informuje o błędnie podanych danych.
* 4.A.2. Przejdź do kroku 2.

---

<a id="uc2"></a>
### UC2: Sprawdzenie aktualnie najwyższej oferowanej kwoty za produkt

**Aktorzy:** [Sprzedający](#ac1), [Kupujący](#ac2)

**Scenariusz główny:**
1. Kupujący wybiera interesującą go aukcję
2. Kupujący oferuje kwotę wyższą od aktualnej
3. System weryfikuje podaną kwotę
4. Sprzedający zgłasza chęć otrzymania informacji o aktualnie najwyższej oferowanej kwocie
5. System informuje sprzedającego o aktualnie najwyższej oferowanej kwocie za produkt

**Scenariusze alternatywne:**

1.A. Kupujący zaoferował kwotę niższą od aktualnie najwyższej oferowanej
* 4.A.1. System informuje o błędnie wprowadzonej kwocie
* 4.A.2. Przejdź do kroku 2.

---


<a id="uc5"></a>
### UC5: Sprawdzenie danych do wysyłki osoby, która wygrała aukcję

**Aktorzy:** [Sprzedający](#ac1), [Kupujący](#ac2)

**Scenariusz główny:**
1. Kupujący oferuje kwotę wyższą od aktualnie najwyższej
2. Czas aukcji kończy się 
3. Kupujący podaje dane do wysyłki
4. Sprzedający zgłasza chęć otrzymania danych kupującego, który wygrał aukcję
5. System podaje sprzedającemu dane do wysyłki kupującego

**Scenariusze alternatywne:**

1.A. Kupujący podał nieprawidłowe dane do wysyłki
* 4.A.1. Sprzedający zgłasza nieprawidłowść danych
* 4.A.2. Przejdź do kroku 3.

## Obiewkty biznesowe (inaczje obiekty dziedzinowe lub informatycjne)

### BO1: Aukcja

Aukcja jest formą zawierania transakcji kupna-sprzedaży, w której Sprzedający określa cenę wywoławczą produktu, natomiast Kupujący mogą oferować własną ofertę zakupu każdorazowo proponując kwotę wyższą od aktualnie oferowanej kwoty. Aukcja kończy się po upływie określonego czasu. Jeśli złożona została co najmniej jedna oferta zakupy produkt nabywa ten Kupujący, który zaproponował najwyższą kwotę.

### BO2: Produkt

Fizyczny lub cyfrowy obiekt, który ma zostać sprzedany w ramach aukcji.

## Reguły biznesowe

<a id="br1"></a>
### BR1: Złożenie oferty

Złożenie oferty wymaga zaproponowania kwoty wyższej niż aktualnie oferowana o minimum 1,00 PLN.


<a id="br2"></a>
### BR2: Rozstrzygnięcie aukcji

Aukcję wygrywa ten z [Kupujący](#ac2)ch, który w momencie jej zakończenia (upłynięcia czasu) złożył najwyższą ofertę.

## Macierz CRUDL


| Przypadek użycia                                  | Aukcja | Produkt | ... |
| ------------------------------------------------- | ------ | ------- | --- |
| UC1: Wystawienia produktu na aukcję               |    C   |    C    | ... |
| ???                                               |  ...   |  ...    | ... |


