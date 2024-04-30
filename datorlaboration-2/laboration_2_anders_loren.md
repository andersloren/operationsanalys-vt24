# Inlämning 1 datorlaboration 2

<p><strong>Namn: </strong>Anders Lorén</p>
<p><strong>Personnummer: </strong>19840102-5534</p>
<p><strong>Laborationsgrupp: </strong>38</p>

## Uppgift 1

### Kod

```
X1 >= 0;
X2 >= 0;
X3 >= 0;
X4 >= 0;

[Supply_color_A] 4*X1 + 3*X2 + 2*X3 + 3*X4 <= 200;
[Supply_color_B] 2*X1 + 3*X2 + 3*X3 + 2*X4 <= 180;
[Machine_time_1] 20*X1 + 18*X2 + 19*X3 + 21*X4 <= 1300;
[Machine_time_2] 17*X1 + 15*X2 + 20*X3 + 18*X4 <= 1100;
[Production_demand] X3 >= 14;

[Objective_Function] MAX = 320*X1 + 290*X2 + 170*X3 + 260*X4;
```

### Känslighetsanalys

| Variable | Value    | Reduced Cost |
| -------- | -------- | ------------ |
| X1       | 10.00000 | 0.000000     |
| X2       | 36.66667 | 0.000000     |
| X3       | 10.00000 | 0.000000     |
| X4       | 10.00000 | 0.000000     |

| Row                | Slack or Surplus | Dual Price |
| ------------------ | ---------------- | ---------- |
| 1                  | 10.00000         | 0.000000   |
| 2                  | 36.66667         | 0.000000   |
| 3                  | 10.00000         | 0.000000   |
| 4                  | 10.00000         | 0.000000   |
| SUPPLY_COLOR_A     | 0.000000         | 60.74074   |
| SUPPLY_COLOR_B     | 0.000000         | 32.22222   |
| MACHINE_TIME_1     | 40.00000         | 0.000000   |
| MACHINE_TIME_2     | 0.000000         | 0.7407407  |
| PRODUCTION_DEMAND  | 0.000000         | -62.96296  |
| OBJECTIVE_FUNCTION | 18133.33         | 1.000000   |

### Ranges

#### Objective Coefficient Ranges:

| Variable | Current Coefficient | Allowable Increase | Allowable Decrease |
| -------- | ------------------- | ------------------ | ------------------ |
| X1       | 320.0000            | 6.666667           | 68.33333           |
| X2       | 290.0000            | 10.00000           | 41.42857           |
| X3       | 170.0000            | 62.96296           | INFINITY           |
| X4       | 260.0000            | 78.09524           | 3.333333           |

#### Righthand Side Ranges:

| Row               | Current RHS | Allowable Increase | Allowable Decrease |
| ----------------- | ----------- | ------------------ | ------------------ |
| 2                 | 0.000000    | 36.66667           | INFINITY           |
| 3                 | 0.000000    | 10.00000           | INFINITY           |
| 4                 | 0.000000    | 10.00000           | INFINITY           |
| SUPPLY_COLOR_A    | 200.0000    | 12.85714           | 11.25000           |
| SUPPLY_COLOR_B    | 180.0000    | 30.00000           | 47.14286           |
| MACHINE_TIME_1    | 1300.000    | INFINITY           | 40.00000           |
| MACHINE_TIME_2    | 1100.000    | 36.00000           | 45.00000           |
| PRODUCTION_DEMAND | 10.00000    | 5.294118           | 6.923077           |
| 1                 | 0.000000    | 10.00000           | INFINITY           |

### Frågor

#### <p>a)</p>

<em>Företaget får erbjudande om att köpa in mer färg. Två alternativ erbjuds:

- Alternativ 1: Maximalt 10 liter av färg A till priset 25 kronor/liter.
- Alternativ 2: Maximalt 10 liter av färg B till priset 10 kronor/liter.

Vilket alternativt är mest fördelaktigt?</em>

#### Svar:

Högsta tillåtna höjning av restriktionen för färg A är 11.25 utan att skuggpriset ändras.

Vi kan därför ta DUAL PRICE för SUPPLY_COLOR_A minus med kostnaden per liter av extrafärgen och sedan multiplicera differensen med antal liter extrafärg. Med svaret avrundat till en decimal ger detta:

`(60.74074 - 25) * 10 = 357.4`

Högsta tillåtna höjning av restriktionen för färg B är 47.14286 utan att skuggpriset ändras.

Motsvarande uträkning för andra alternativet blir:

`(32.22222 - 10) * 10 = 222.2`

Alternativ 1 är alltså det bästa alternativet.

#### <p>b)</p>

<em>Finns det tid över i någon av maskinerna?</em>

#### Svar:

Ja! Maskin 1 har 40 minuter SLACK efter att produktionen är klar.

#### <p>c)</p>

<em>Tolka skuggpriset i produktionskravvillkoret. Vad kan du dra för slutsatser om
produktionskravet på produkt 3 ökar med 4 respektive 8 enheter?</em>

#### Svar:

PRODUCTION_DEMAND har en tillåten höjning med 5.294118. Alltså kan vi öka restriktionen med 4 utan att DUAL PRICE ändras, vilket är -62.96296.

Från målfunktionens värde subtraherar vi produkten av DUAL PRICE och 4:

`18133.33 - 4 * (-62.96296) = 17881.48`

Produktionskravets ökning med 8 går utanför den högsta tillåtna ökningen. Vi vet alltså inte säkert hur mycket ökningen kommer att påverka målfunktionens värde.

Min tolkning av övningsboken är att skuggpriset bara kan röra sig mot 0 ju högre produktionskravet ökar. Alltså hamnar den totala reducerade vinsten någonstans mellan högsta tillåtna ökning multiplicerat med DUAL PRICE och 8 multiplicerat med DUAL PRICE:

`5.294118 * (-62.96296) = -333.33`

`8 * -62.96296 = -503.7`

#### <p>d)</p>

<em>Antag att täckningsbidraget för produkt 3 ändras från 170 till 100 kronor. Hur
förändras optimallösningen?</em>

#### Svar:

Eftersom REDUCED COST för produkt 3 är oändlig så kan täckningsbidraget sänkas oändligt lågt utan att optimallösningen ändras.

<p>Anledningen till att 10 enheter av produkt 3 trots allt tillverkas är för att det femte bivillkoret kräver så.</p>

#### <p>e)</p>

<em>Hur mycket tjänar företaget på att öka maskinkapaciteten i maskin 1 med 100
minuter?</em>

#### Svar:

Företaget tjänar ingenting på detta då det redan finns 40 minuter SLACK på maskin 1.

## Uppgift 2

### Kod

```
! Laboration 2, Förberedande uppgift 2

Xij = antal ton från i till j

i = A, B, C, D, E
j = D, E, F, G, H

! Beslutsvariabler;

[CITY_A_FACILITY_D] XAD >= 0;
[CITY_A_FACILITY_E] XAE >= 0;
[CITY_B_FACILITY_D] XBD >= 0;
[CITY_B_FACILITY_E] XBE >= 0;
[CITY_C_FACILITY_D] XCD >= 0;
[CITY_C_FACILITY_E] XCE >= 0;

[FACILITY_D_STATION_F] XDF >= 0;
[FACILITY_D_STATION_G] XDG >= 0;
[FACILITY_D_STATION_H] XDH >= 0;
[FACILITY_E_STATION_F] XEF >= 0;
[FACILITY_E_STATION_G] XEG >= 0;
[FACILITY_E_STATION_H] XEH >= 0;

! Bivillkor;

[CITY_A_WASTE] XAD + XAE = 500;
[CITY_B_WASTE] XBD + XBE = 400;
[CITY_C_WASTE] XCD + XCE = 300;

[FACILITY_D_CAPACITY] XAD + XBD + XCD <= 700;
[FACILITY_E_CAPACITY] XAE + XBE + XCE <= 700;

[FACILITY_D_TOTAL_WASTE_TO_DROSS] 0.2*(XAD + XBD + XCD) = XDF + XDG + XDH;
[FACILITY_E_TOTAL_WASTE_TO_DROSS] 0.2*(XAE + XBE + XCE) = XEF + XEG + XEH;

[STATION_F_CAPACITY] XDF + XEF <= 100;
[STATION_G_CAPACITY] XDG + XEG <= 100;
[STATION_H_CAPACITY] XDH + XEH <= 150;

! Målfunktion;

Z1 >= 0;
Z2 >= 0;
Z3 >= 0;
Z4 >= 0;
Z5 >= 0;
Z6 >= 0;

[TRANSPORT_COST_CITY_A_FACILITY_D_E] Z1 = 150*(7*XAD + 1*XAE);
[TRANSPORT_COST_CITY_B_FACILITY_D_E] Z2 = 150*(8*XBD + 9*XBE);
[TRANSPORT_COST_CITY_C_FACILITY_D_E] Z3 = 150*(10*XCD + 11*XCE);

[TRANSPORT_COST_FACILITY_D_STATION_F_G_H] Z4 = 160*(1*XDF + 2*XDG + 3*XDH);
[TRANSPORT_COST_FACILITY_E_STATION_F_G_H] Z5 = 160*(4*XEF + 8*XEG + 2*XEH);

[COMBUSTION_COSTS_FACILITY_D] Z6 = 320*(XAD + XBD + XCD);
[COMBUSTION_COSTS_FACILITY_E] Z7 = 240*(XAD + XBD + XCD);

MIN = Z1 + Z2 + Z3 + Z4 + Z5 + Z6;
```

### Känslighetsanalys

| Variable | Value    | Reduced Cost |
| -------- | -------- | ------------ |
| XAD      | 0.000000 | 1050.000     |
| XAE      | 500.0000 | 0.000000     |
| XBD      | 400.0000 | 0.000000     |
| XBE      | 0.000000 | 0.000000     |
| XCD      | 100.0000 | 0.000000     |
| XCE      | 200.0000 | 0.000000     |
| XDF      | 100.0000 | 0.000000     |
| XDG      | 0.000000 | 160.0000     |
| XDH      | 0.000000 | 320.0000     |
| XEF      | 0.000000 | 320.0000     |
| XEG      | 0.000000 | 960.0000     |
| XEH      | 140.0000 | 0.000000     |
| Z1       | 75000.00 | 0.000000     |
| Z2       | 480000.0 | 0.000000     |
| Z3       | 480000.0 | 0.000000     |
| Z4       | 16000.00 | 0.000000     |
| Z5       | 44800.00 | 0.000000     |
| Z6       | 160000.0 | 0.000000     |
| Z7       | 120000.0 | 0.000000     |

### Ranges

| Row                                     | Slack or Surplus | Dual Price |
| --------------------------------------- | ---------------- | ---------- |
| CITY_A_FACILITY_D                       | 0.000000         | 0.000000   |
| CITY_A_FACILITY_E                       | 500.0000         | 0.000000   |
| CITY_B_FACILITY_D                       | 400.0000         | 0.000000   |
| CITY_B_FACILITY_E                       | 0.000000         | 0.000000   |
| CITY_C_FACILITY_D                       | 100.0000         | 0.000000   |
| CITY_C_FACILITY_E                       | 200.0000         | 0.000000   |
| FACILITY_D_STATION_F                    | 100.0000         | 0.000000   |
| FACILITY_D_STATION_G                    | 0.000000         | 0.000000   |
| FACILITY_D_STATION_H                    | 0.000000         | 0.000000   |
| FACILITY_E_STATION_F                    | 0.000000         | 0.000000   |
| FACILITY_E_STATION_G                    | 0.000000         | 0.000000   |
| FACILITY_E_STATION_H                    | 140.0000         | 0.000000   |
| CITY_A_WASTE                            | 0.000000         | -352.0000  |
| CITY_B_WASTE                            | 0.000000         | -1552.000  |
| CITY_C_WASTE                            | 0.000000         | -1852.000  |
| FACILITY_D_CAPACITY                     | 200.0000         | 0.000000   |
| FACILITY_E_CAPACITY                     | 0.000000         | 138.0000   |
| FACILITY_D_TOTAL_WASTE_TO_DROSS         | 0.000000         | 160.0000   |
| FACILITY_E_TOTAL_WASTE_TO_DROSS         | 0.000000         | 320.0000   |
| STATION_F_CAPACITY                      | 0.000000         | 0.000000   |
| STATION_G_CAPACITY                      | 100.0000         | 0.000000   |
| STATION_H_CAPACITY                      | 10.00000         | 0.000000   |
| 23                                      | 75000.00         | 0.000000   |
| 24                                      | 480000.0         | 0.000000   |
| 25                                      | 480000.0         | 0.000000   |
| 26                                      | 16000.00         | 0.000000   |
| 27                                      | 44800.00         | 0.000000   |
| 28                                      | 160000.0         | 0.000000   |
| TRANSPORT_COST_CITY_A_FACILITY_D_E      | 0.000000         | -1.000000  |
| TRANSPORT_COST_CITY_B_FACILITY_D_E      | 0.000000         | -1.000000  |
| TRANSPORT_COST_CITY_C_FACILITY_D_E      | 0.000000         | -1.000000  |
| TRANSPORT_COST_FACILITY_D_STATION_F_G_H | 0.000000         | -1.000000  |
| TRANSPORT_COST_FACILITY_E_STATION_F_G_H | 0.000000         | -1.000000  |
| COMBUSTION_COSTS_FACILITY_D             | 0.000000         | -1.000000  |
| COMBUSTION_COSTS_FACILITY_E             | 0.000000         | 0.000000   |
| 36                                      | 1255800.         | -1.000000  |

| Variable | Current Coefficient | Allowable Increase | Allowable Decrease |
| -------- | ------------------- | ------------------ | ------------------ |
| XAD      | 0.000000            | INFINITY           | 1050.000           |
| XAE      | 0.000000            | 1050.000           | INFINITY           |
| XBD      | 0.000000            | 0.000000           | INFINITY           |
| XBE      | 0.000000            | INFINITY           | 0.000000           |
| XCD      | 0.000000            | 1050.000           | 0.000000           |
| XCE      | 0.000000            | 0.000000           | 1050.000           |
| XDF      | 0.000000            | 160.0000           | 690.0000           |
| XDG      | 0.000000            | INFINITY           | 160.0000           |
| XDH      | 0.000000            | INFINITY           | 320.0000           |
| XEF      | 0.000000            | INFINITY           | 320.0000           |
| XEG      | 0.000000            | INFINITY           | 960.0000           |
| XEH      | 0.000000            | 320.0000           | INFINITY           |
| Z1       | 1.000000            | INFINITY           | 1.166667           |
| Z2       | 1.000000            | INFINITY           | 0.000000           |
| Z3       | 1.000000            | 0.000000           | 7.000000           |
| Z4       | 1.000000            | INFINITY           | 1.000000           |
| Z5       | 1.000000            | 2.156250           | 1.000000           |
| Z6       | 1.000000            | INFINITY           | 0.4312500          |
| Z7       | 0.000000            | INFINITY           | 0.5750000          |

#### Righthand Side Ranges:

| Row                          | Current RHS | Allowable Increase | Allowable Decrease |
| ---------------------------- | ----------- | ------------------ | ------------------ |
| CITY_A_FACILITY_E            | 0.000000    | 500.0000           | INFINITY           |
| CITY_B_FACILITY_D            | 0.000000    | 400.0000           | INFINITY           |
| CITY_B_FACILITY_E            | 0.000000    | 0.000000           | INFINITY           |
| CITY_C_FACILITY_D            | 0.000000    | 100.0000           | INFINITY           |
| CITY_C_FACILITY_E            | 0.000000    | 200.0000           | INFINITY           |
| FACILITY_D_STATION_F         | 0.000000    | 100.0000           | INFINITY           |
| FACILITY_D_STATION_G         | 0.000000    | 0.000000           | INFINITY           |
| FACILITY_D_STATION_H         | 0.000000    | 0.000000           | INFINITY           |
| FACILITY_E_STATION_F         | 0.000000    | 0.000000           | INFINITY           |
| FACILITY_E_STATION_G         | 0.000000    | 0.000000           | INFINITY           |
| FACILITY_E_STATION_H         | 0.000000    | 140.0000           | INFINITY           |
| CITY_A_WASTE                 | 500.0000    | 0.000000           | 100.0000           |
| CITY_B_WASTE                 | 400.0000    | 0.000000           | 400.0000           |
| CITY_C_WASTE                 | 300.0000    | 0.000000           | 100.0000           |
| FACILITY_D_CAPACITY          | 700.0000    | INFINITY           | 200.0000           |
| FACILITY_E_CAPACITY          | 700.0000    | 50.00000           | 0.000000           |
| FACILITY_D_TOTAL_WASTE_TO_DR | 0.000000    | 100.0000           | 0.000000           |
| FACILITY_E_TOTAL_WASTE_TO_DR | 0.000000    | 140.0000           | 10.00000           |
| STATION_F_CAPACITY           | 100.0000    | INFINITY           | 0.000000           |
| STATION_G_CAPACITY           | 100.0000    | INFINITY           | 100.0000           |
| STATION_H_CAPACITY           | 150.0000    | INFINITY           | 10.00000           |
| 23                           | 0.000000    | 75000.00           | INFINITY           |
| 24                           | 0.000000    | 480000.0           | INFINITY           |
| 25                           | 0.000000    | 480000.0           | INFINITY           |
| 26                           | 0.000000    | 16000.00           | INFINITY           |
| 27                           | 0.000000    | 44800.00           | INFINITY           |
| 28                           | 0.000000    | 160000.0           | INFINITY           |
| TRANSPORT_COST_CITY_A_FACILI | 0.000000    | INFINITY           | 75000.00           |
| TRANSPORT_COST_CITY_B_FACILI | 0.000000    | INFINITY           | 480000.0           |
| TRANSPORT_COST_CITY_C_FACILI | 0.000000    | INFINITY           | 480000.0           |
| TRANSPORT_COST_FACILITY_D_ST | 0.000000    | INFINITY           | 16000.00           |
| TRANSPORT_COST_FACILITY_E_ST | 0.000000    | INFINITY           | 44800.00           |
| COMBUSTION_COSTS_FACILITY_D  | 0.000000    | INFINITY           | 160000.0           |
| COMBUSTION_COSTS_FACILITY_E  | 0.000000    | INFINITY           | 120000.0           |
| CITY_A_FACILITY_D            | 0.000000    | 0.000000           | INFINITY           |

### Kommentar

Några slutsatser man kan dra av analysen är följande:

- CITY_C_WASTE har ett DUAL PRICE på -1852. Detta innebär att 1 ton mindre avfall från Stad C ger en total kostnadsminskning på 1852, vilket är den största minskningen om avfallet minskar med 1 ton från någon av städerna. Detta är sant för upp till 100 ton minskat avfall, eftersom CITY_C_WASTE har en ALLOWED DECREASE på just 100.

- FACILITY_E_CAPACITY har ett DUAL PRICE på 138. Om kapaciteten för Anläggning E ökar med 1 så minskar den totala kostnaden med 138. Detta är sant för upp till 50 ton ökad kapacitet, vilket framgår av ALLOWED INCREASE för FACILITY_E_CAPACITY som är just 50.

- Ingen av stationerna har ett DUAL PRICE skiljt från 0. Detta känns lite konstigt eftersom det är olika dyrt att köra till olika stationer från anläggningarna. Min gissning är att LINGO inte kan räkna ut detta då kostnadsbiten för körningarna till de olika stationerna utgörs av ekvationerna som saknar konstanter i högerled.
