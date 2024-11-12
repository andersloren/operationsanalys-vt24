# Datorlaboration 2

<p>Namn: Anders Lorén</p>
<p>Grupp: 38</p>

## Uppgift 1

### Kod

```
[BAG_3] X1 >= 0;
[BAG_4] X2 >= 0;
[BAG_2] X3 >= 0;

[Green] XG <= 500;
[Red] XR <= 700;

[Green_Total] 3*X1+4*X2 = XG;
[Red_Total] 3*X1+4*X2+2*X3 = XR;

MAX = 5*X1 + 7*X2 + 2*X3;
```

### Svar

<p>a)</p>
<strong>Optimallösning:</strong>

| Variabel                 | Antal |
| ------------------------ | ----- |
| Påse med 3 gröna, 3 röda | 0     |
| Påse med 4 gröna, 4 röda | 125   |
| Påse med 2 röda          | 100   |

<strong>Total förtjänst:</strong>

`1075 tkr`

<p>b)</p>

| Row          | Dual Price |
| ------------ | ---------- |
| Grön paprika | 0.7500000  |
| Röd paprika  | 1.000000   |

Röd paprika har DUAL PRICE på 1, vilket innebär att man tjänar 1 kr per extra röd paprika. Detta är det bättre alternativet än Grön paprika som man bara tjänar 0.75 kr per extra grön paprika.

<p>c)</p>

| Variable | Value    | Reduced Cost |
| -------- | -------- | ------------ |
| X1       | 0.000000 | 0.2500000    |

Vi måste öka förjänsten med mer än 0.25 kr för att den påsen ska vara lönsam.

## Uppgift 2

### Kod

```
5*A1 + 7*A2 <= 170;
2*B1 + 3*B2 <= 260;
4*C1 + 6*C2 <= 135;
7*D1 + 9*D2 <= 155;
4*E1 + 5*E2 <= 190;

5*A1 + 2*B1 + 4*C1 + 7*D1 + 4*E1 = 360;
7*A2 + 3*B2 + 6*C2 + 9*D2 + 5*E2 = 540;

MIN = 5*A1 + 2*B1 + 4*C1 + 7*D1 + 4*E1 + 7*A2 + 3*B2 + 6*C2 + 9*D2 + 5*E2;
```

### Svar

<p>a)</p>

Transportlösning:

| Underleverantör | antal    |
| --------------- | -------- |
| A1              | 80.00000 |
| A2              | 90.00000 |
| B2              | 260.0000 |
| C1              | 135.0000 |
| D1              | 145.0000 |
| E2              | 190.0000 |

<p>c)</p>

| Underleverantör | Slack or surplus | Dual Price |
| --------------- | ---------------- | ---------- | 
| Row             | Slack            | or         | Surplus | Dual | Price |
| SUPPLIER_1      | 0.000000         | 2.000000   |
| SUPPLIER_2      | 0.000000         | 6.000000   |
| SUPPLIER_3      | 0.000000         | 3.000000   |
| SUPPLIER_4      | 10.00000         | 0.000000   |
| SUPPLIER_5      | 0.000000         | 4.000000   |

Om vi kunde öka kapaciteten med 1 hos underleveranför 2 skulle vi minska kostnaden med 6 tkr, vilket är den största minskningen vi kan göra jämfört med övriga underleverantörer.
