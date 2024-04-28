# Inlämning 1 datorlaboration 2

<p><strong>Namn: </strong>Anders Lorén</p>
<p><strong>Personnummer: </strong>19840102-5534</p>
<p><strong>Laborationsgrupp: </strong>38</p>

## Uppgift 1

### Kod

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

Företaget får erbjudande om att köpa in mer färg. Två alternativ erbjuds:

- Alternativ 1: Maximalt 10 liter av färg A till priset 25 kronor/liter.
- Alternativ 2: Maximalt 10 liter av färg B till priset 10 kronor/liter.

Vilket alternativt är mest fördelaktigt?

#### Svar:

Högsta tillåtna höjning av restriktionen för färg A är 11.25 utan att skuggpriset ändras.

Vi kan därför ta DUAL PRICE för SUPPLY_COLOR_A minus med kostnaden per liter av extrafärgen och sedan multiplicera differensen med antal liter extrafärg. Med svaret avrundat till en decimal ger detta:

`(60.74074 - 25) * 10 = 357.4 kr`

Högsta tillåtna höjning av restriktionen för färg B är 11.25 utan att skuggpriset ändras.

Motsvarande uträkning för andra alternativet blir:

`(32.22222 - 10) * 10 = 222.2 kr`

Alternativ 1 är alltså det bästa alternativet.

#### <p>b)</p>

Finns det tid över i någon av maskinerna?

#### Svar:

Maskin 1 har 40 minuter SLACK efter att produktionen är klar.

#### <p>c)</p>

Tolka skuggpriset i produktionskravvillkoret. Vad kan du dra för slutsatser om
produktionskravet på produkt 3 ökar med 4 respektive 8 enheter?

#### Svar:

PRODUCTION_DEMAND har en tillåten höjning med 5.294118. Alltså kan vi öka restriktionen med 4 utan att DUAL PRICE ändras, vilket är -62.96296.

Från målfunktionens värde subtraherar vi produkten av DUAL PRICE och 4:

`18133.33 - 4 * (-62.96296) = 17881.48`

Produktionskravets ökning med 8 går utanför den högsta tillåtna ökningen. Vi vet alltså inte säkert hur mycket ökningen kommer att påverka målfunktionens värde. Men min tolkning av övningsboken är att vi kan uppskatta den högsta och lägsta förändringen genom följande beräkning:
