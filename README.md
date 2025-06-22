# Analiza Sistemului de Control

Acest document detaliază analiza comportamentului dinamic al unui sistem de control, incluzând determinarea funcțiilor de transfer, analiza stabilității (internă și externă) și simulări ale răspunsului sistemului cu diferite tipuri de controlere (P, PI, PID și Fuzzy Logic).

---

## Exercițiul 1: Analiza Diagramelor Bode și Funcțiilor de Transfer

Diagramele Bode (magnitudine și fază în funcție de frecvență) sunt utilizate pentru a determina caracteristicile de frecvență ale sistemului și pentru a deduce funcțiile de transfer asociate.

Diagrame Bode Exemplu 1 (Funcția hee)
- Graficul Magnitudine-Frecvență: Se observă o variație a amplitudinii în funcție de frecvență, cu o pantă inițială de 0 dB/decadă (P1) până la o frecvență de colț ω1​, după care panta devine -20 dB/decadă (P2).
- Funcția de Transfer hee:
  hee = 1/ (1.53s + 1)
Aceasta este o funcție de transfer a unui sistem de ordinul întâi.

Diagrame Bode Exemplu 2 (Funcția hp)
- Graficul Magnitudine-Frecvență: Prezintă mai multe segmente:
P1: 0 dB/decadă, până la ω1 (aproximativ 10^0 rad/s).
P2: -20 dB/decadă, între ω1​ și ω2 (aproximativ 10^1 rad/s).
P3: 0 dB/decadă, între ω2​ și ω3 (aproximativ 10^2 rad/s).
P4: -20 dB/decadă, după ω3.

- Funcția de Transfer hp:
hp = (0.468s+7.5)/ (0.043s^4 + 4.45s^3 + 8.15s^2 + 4.968s + 1​
 
Aceasta este o funcție de transfer de ordinul patru.

---

## Exercițiul 2: Analiza Stabilității Sistemului

Acest exercițiu se concentrează pe determinarea stabilității interne și externe a sistemului prin calculul rădăcinilor și al determinanților.

Funcții Componente
Funcția ht:
ht= 
2s+1
0.5
​
 

Funcția he: Aceeași cu hp de la Exercițiul 1.
he= 
0.043s 
4
 +4.45s 
3
 +8.15s 
2
 +4.968s+1
0.468s+7.5
​
Rădăcinile Funcțiilor (he)
Rădăcinile funcției sunt utilizate pentru repartiția polilor și zerourilor.

Rădăcinile numărătorului (zerouri): roots([0.468 7.5]) dă ans = -16.0256.
Rădăcinile numitorului (poli): roots([0.043 4.45 8.15 4.968 1]) dă ans = [-101.6347; -0.6966; -0.6576; -0.4995].
Funcția ho pentru Stabilitate
Funcția ho este definită ca ho = 1 + hp, și este utilizată pentru determinarea stabilității sistemului.
ho= 
0.043s 
4
 +4.45s 
3
 +8.15s 
2
 +4.968s+1
0.043s 
4
 +4.45s 
3
 +8.15s 
2
 +5.436s+8.5
​
Determinarea Stabilității Externe
Stabilitatea externă este evaluată prin calculul determinanților, iar valorile pozitive indică un sistem extern stabil.

d1 = 4.45 , det(d1) = 4.4500.
d2 = [4.45 5.436; 0.043 8.15] , det(d2) = 36.0338.
d3 = [4.45 5.436 0; 0.043 8.15 8.5; 0 4.45 5.436] , det(d3) = 27.5582.
d4 = [4.45 5.436 0 0; 0.043 8.15 8.5 0; 0 4.45 5.436 0; 0 0.043 8.15 8.5] , det(d4) = 234.2449. Deoarece toți determinanții sunt pozitivi, sistemul este extern stabil.

Determinarea Stabilității Interne
Stabilitatea internă este determinată de rădăcinile sistemului; dacă acestea sunt strict negative, sistemul este intern stabil.

roots([1 4450/43 8150/43 4968/43 1000/43]) dă ans = [-101.6347; -0.6966; -0.6576; -0.4995]. Toate rădăcinile sunt negative, indicând un sistem intern stabil.

---

## Exercițiul 3: Diagrama Nyquist

Diagrama Nyquist reprezintă grafic partea reală și imaginară a funcției de transfer în planul complex, în funcție de pulsație.

Funcția he:
he= 
0.043s 
4
 +4.45s 
3
 +8.15s 
2
 +4.968s+1
0.468s+7.5
​
Analiza Stabilității: Sistemul este stabil, deoarece punctul -1 nu este înconjurat de diagrama Nyquist.
Măsurători Cursor: Pe graficul de răspuns în timp (Scope), se pot evidenția valorile maxime și timpul tranzitoriu. De exemplu, un vârf este la Time = 3.515 cu Value = 2.342e+02, iar o altă valoare este la Time = 81.591 cu Value = 1.385e+02.

---

## Exercițiul 4: Răspunsul Sistemului cu Controlere P, PI, PID

Acest exercițiu ilustrează răspunsul sistemului la utilizarea diferitelor tipuri de controlere (Proporțional, Proporțional-Integral, Proporțional-Integral-Derivativ).

Răspunsul cu Controller P
Configurație Controller P: Proporțional (P): 0.5.
Răspunsul Sistemului: Se observă un răspuns cu oscilații. Măsurătorile cursor arată un vârf la Time = 4.413 cu Value = 1.754e+02 și o valoare de regim la Time = 16.935 cu Value = 1.121e+02.

Răspunsul cu Controller PI
Configurație Controller PI: Proporțional (P): 0.5, Integral (I): 0.04.
Răspunsul Sistemului: Răspunsul arată o îmbunătățire a amortizării comparativ cu controllerul P. Măsurătorile cursor indică un vârf la Time = 4.413 cu Value = 1.967e+02 și o valoare de regim la Time = 25.181 cu Value = 1.425e+02.

Răspunsul cu Controller PID (cu și fără perturbație)
Configurație Controller PID: Proporțional (P): 0.5, Integral (I): 0.04, Derivativ (D): 0.03, Coeficient filtru (N): 100.

Răspuns cu Perturbație: Sistemul răspunde la o perturbație (reprezentată de "Signal Builder").

Răspuns fără Perturbație: Sistemul are un răspuns stabil fără influența perturbației.

---

## Exercițiul 5: Adăugarea Controller-ului Fuzzy

Acest exercițiu demonstrează integrarea și impactul unui controller Fuzzy Logic asupra răspunsului sistemului.

Definirea Funcțiilor de Membru Fuzzy (Intrare)
Sunt definite trei funcții de membru pentru intrare (input1), notate E1, E2, E3. Acestea au forme triunghiulare cu parametri specifici (e.g., E1 are parametri [-50 -25 0], E2 are [-25 0 25], E3 are [0 75 150]). Domeniul de intrare (Range) este [-50 150].

Definirea Funcțiilor de Membru Fuzzy (Ieșire)
Sunt definite trei funcții de membru pentru ieșire (output1), notate Cmin, Ck, Cmax. Acestea au, de asemenea, forme triunghiulare cu parametri specifici (e.g., Cmin are [0 10 20], Ck are [10 20 30], Cmax are [20 30 50]). Domeniul de ieșire (Range) este [0 50].

Vizualizarea Modificărilor Răspunsului cu Controller Fuzzy
Răspunsul Sistemului: Adăugarea controllerului Fuzzy Logic modifică răspunsul sistemului. Măsurătorile cursor arată un vârf la Time = 0.234 cu Value = 1.810e+02 și o valoare de regim la Time = 15.070 cu Value = 1.579e+02. Alte măsurători indică Time = 4.480 cu Value = 2.103e+02 și Time = 142.133 cu Value = 1.425e+02.
