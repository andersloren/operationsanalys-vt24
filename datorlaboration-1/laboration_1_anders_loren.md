# Laboration 1, Operationsanalys A188TG E75V4

Student: Anders Lorén<br>
Student-ID: S170512

## Information till lärare

<p>All text som står utanför kommentarer är på engelska. Det verkar som att LINGO har problem med å, ä och ö. </p>
<p>Om du föredrar att köra koderna så har jag laddat upp dem på GitHub: </p>
https://github.com/andersloren/operationsanalys-vt24

## Förberedelseuppgift 1

### Kod

```
Laboration 1, förberedande uppgift 1

!- Beslutsvariabler --

Xjt 	där,

	j : 1 = grossist 1, 2 = grossist 2
	t : månad 1,2,3;

!- Bivillkor --

! Det producerade fodret kan inte ha en negativ kvantitet;

[BASIC_FEED]		X1 >= 0;
[STANDARD_FEED]	X2 >= 0;
[SPECIAL_FEED]	X3 >= 0;

! Det ställs följande krav på näringsinnehållet i fodret;

[CARBS]		0.5*X1 + 0.7*X2 + 0.3*X3 >= 200;
[PROTEIN]		0.1*X1 + 0.2*X2 + 0.05*X3 >= 80;
[FAT]			0.02*X1 + 0.02*X2 + 0.08*X3 >= 30;
[MINERALS_MAX]	0.008*X1 + 0.001*X2 >= 0.4;
[MINERALS_MIN]	0.008*X1 + 0.001*X2 <= 1.6;

!- Målfunktion -- ;

[OBJECTIVE_FUNCTION] MIN = 6*X1 + 12*X2 + 4*X3;
```

### Lösningsrapport

| Variable | Value    | Reduced Cost |
| -------- | -------- | ------------ |
| X1       | 169.0265 | 0.000000     |
| X2       | 247.7876 | 0.000000     |
| X3       | 270.7965 | 0.000000     |

| Row                | Slack or Surplus | Dual Price |
| ------------------ | ---------------- | ---------- |
| BASIC_FEED         | 169.0265         | 0.000000   |
| STANDARD_FEED      | 247.7876         | 0.000000   |
| SPECIAL_FEED       | 270.7965         | 0.000000   |
| CARBS              | 139.2035         | 0.000000   |
| PROTEIN            | 0.000000         | -58.76106  |
| FAT                | 0.000000         | -13.27434  |
| MINERALS_MAX       | 1.200000         | 0.000000   |
| MINERALS_MIN       | 0.000000         | 17.69912   |
| OBJECTIVE_FUNCTION | 5070.796         | -1.000000  |

### Analys

#### Recuded Cost

Den optimala lösningen ger att följande mängd foder och fodertyp ska användas: ≈169 kg basfoder, ≈248 kg standardfoder och ≈271 kr specialfoder.

Lösningen ger ett större värde än 0 på samtliga variabler vilket innebär att reduced cost är 0 för samtliga variabler.

#### Slack or Suprplus samt Dual Price

<p>De variabler som har ett slack eller surplus på 0 är de variabler som direkt kan påverka målfunktionen om restriktionerna för dessa bivillkor ändras.</p>
<p>
Om kravet på protien eller fett minskar med 1 så sjunker värdet på målfunktionen med ≈59 respektive ≈13. Ökar man istället något av kraven med 1 så ökar målfunktionen med ≈59 respektive ≈13.
</p>
<p>
Vad gäller minimikravet för mineraler så gäller samma sak även här. Att reduced cost anges som ett positivt tal tror jag beror på att vi använder ett mindre-än-tecken i bivillkoret.
</p>

### Frågor

**Vilken foderblandning ska bonden välja?**

Svar: ≈169 kg basfoder, ≈248 kg standardfoder och ≈271 kr specialfoder

**Hur mycket kolhydrater ingår i blandningen?**

Svar: ≈339 kg (bivillkor 200 kg + surplus ≈139 kg).

## Förberedelseuppgift 2

### Kod

```
Laboration 1, Förberedelseuppgift 2

!- Beslutsvariabler --

Xi 	där,

	i : 1 = indoor paint 1, 2 = outdoor paint, 3 = marine;

[OUTDOOR_PAINT]	X1>=0;
[INDOOR_PAINT]	X2>=0;
[MARINE]		X3>=0;

!- Bivillkor --

Färgerna måste innehålla olika mängder råmaterial;

[RAW_MATERIAL_1] 6*X1 + 4*X2 + 0.7*X3 >= 24;
[RAW_MATERIAL_2] 1*X1 + 2*X2 + 0.95*X3 >= 6;

! Förhållandet mellan inomhusfärg och utomhusfärg;

[OUTDOOR_PAINT_vs_INDOOR_PAINT] -1*X1 + X2 <= 1;

! Efterfrågan;

[OUTDOOR_PAINT_MAX]	X2 <= 2;
[MARINE_MIN]			X3 >= 0.4;
[MARINE_MAX]			X3 <= 2.1;

!- Målfunktion --

! Minimera kostnaden för att tillverka färgerna;

[OBJECTIVE_FUNCTION] MIN = 5*X1 + 4*X2 + 4.5*X3;
```

### Lösningsrapport

| Variable | Value     | Reduced Cost |
| -------- | --------- | ------------ |
| X1       | 3.120000  | 0.000000     |
| X2       | 1.250000  | 0.000000     |
| X3       | 0.4000000 | 0.000000     |

| Row                           | Slack or Surplus | Dual Price |
| ----------------------------- | ---------------- | ---------- |
| OUTDOOR_PAINT                 | 3.120000         | 0.000000   |
| INDOOR_PAINT                  | 1.250000         | 0.000000   |
| MARINE                        | 0.4000000        | 0.000000   |
| RAW_MATERIAL_1                | 0.000000         | -0.7500000 |
| RAW_MATERIAL_2                | 0.000000         | -0.5000000 |
| OUTDOOR_PAINT_VS_INDOOR_PAINT | 2.870000         | 0.000000   |
| OUTDOOR_PAINT_MAX             | 0.7500000        | 0.000000   |
| MARINE_MIN                    | 0.000000         | -3.500000  |
| MARINE_MAX                    | 1.700000         | 0.000000   |
| OBJECTIVE_FUNCTION            | 22.40000         | -1.000000  |

### Analys

Analysen är samma som i förra uppgiften. Värt att notera är att marine bara görs i sådan mängd att den tillfreddställer den lägsta dagliga efterfrågan.

**Den bästa mixen av färger är alltså:**

3.12 ton utomhusfärg, 1.25 ton inomhusfärg och 0.4 ton marine.

## Förberedelseuppgift 3

### Kod

```
!

Laboration 1, Uppgift 3

!- Beslutsvariabler --

Xjt , antal hyllor där

	j : 1 = hyllmodell s , 2 = hyllmodell l , 3 = hyllmodell p
	t : månad 1,2,3

Ijt , antal lagerhållna hyllor där

	j : 1 = hyllmodell s , 2 = hyllmodell l , 3 = hyllmodell p
	t : månad 0,1,2,3;

!- Bivillkor --

! Producerade kvantiteter av de olika hyllmodeller per månad kan inte vara negativa;

[PRODUCTION_S1] Xs1 >= 0;
[PRODUCTION_L1] Xl1 >= 0;
[PRODUCTION_P1] Xp1 >= 0;

[PRODUCTION_S2] Xs2 >= 0;
[PRODUCTION_L2] Xl2 >= 0;
[PRODUCTION_P2] Xp2 >= 0;

[PRODUCTION_S3] Xs3 >= 0;
[PRODUCTION_L3] Xl3 >= 0;
[PRODUCTION_P3] Xp3 >= 0;

! Lagerhållnina kvantiteter av de olika hyllmodellerna per månad kan inte vara negativa. Ij0 startvärden enligt föreläsningsanteckningar. ;

[INV_S0] Is0 = 800;
[INV_S1] Is1 >= 0;
[INV_S2] Is2 >= 0;
[INV_S3] Is3 >= 0;

[INV_I0] Il0 = 500;
[INV_I1] Il1 >= 0;
[INV_I2] Il2 >= 0;
[INV_I3] Il3 >= 0;

[INV_P0] Ip0 = 150;
[INV_P1] Ip1 >= 0;
[INV_P2] Ip2 >= 0;
[INV_P3] Ip3 >= 0;

! Lagerbalansvillkor : (Ingående lager + införskaffade enheter - utgående lager = efterfrågan);

[BALANCE_S_MONTH_1] Is0 + Xs1 - Is1 = 700;
[BALANCE_S_MONTH_2] Is1 + Xs2 - Is2 = 800;
[BALANCE_S_MONTH_3] Is2 + Xs3 - Is3 = 600;

[BALANCE_L_MONTH_1] Il0 + Xl1 - Il1 = 400;
[BALANCE_L_MONTH_2] Il1 + Xl2 - Il2 = 500;
[BALANCE_L_MONTH_3] Il2 + Xl3 - Il3 = 700;

[BALANCE_P_MONTH_1] Ip0 + Xp1 - Ip1 = 100;
[BALANCE_P_MONTH_2] Ip1 + Xp2 - Ip2 = 300;
[BALANCE_P_MONTH_3] Ip2 + Xp3 - Ip3 = 400;

! Respektive bearbetningsfas har sina respektive resursbegränsningar;

[PUNCHING_MONTH_1] 0.3*Xs1 + 0.3*Xl1 + 0.3*Xp1 <= 600;
[PUNCHING_MONTH_2] 0.3*Xs2 + 0.3*Xl2 + 0.3*Xp2 <= 500;
[PUNCHING_MONTH_3] 0.3*Xs3 + 0.3*Xl3 + 0.3*Xp3 <= 400;

[FORMING_MONTH_1] 0.25*Xs1 + 0.5*Xl1 + 0.45*Xp1 <= 600;
[FORMING_MONTH_2] 0.25*Xs2 + 0.5*Xl2 + 0.45*Xp2 <= 500;
[FORMING_MONTH_3] 0.25*Xs3 + 0.5*Xl3 + 0.45*Xp3 <= 400;

[ASSEMBLING_S_MONTH_1] 0.3*Xs1 <= 540;
[ASSEMBLING_S_MONTH_2] 0.3*Xs2 <= 500;
[ASSEMBLING_S_MONTH_3] 0.3*Xs3 <= 450;

[ASSEMBLING_P_MONTH_1] 0.6*Xll + 0.3*Xp1 <= 440;
[ASSEMBLING_P_MONTH_2] 0.6*Xl2 + 0.5*Xp2 <= 400;
[ASSEMBLING_P_MONTH_3] 0.6*Xl3 + 0.5*Xp3 <= 400;

!- Målfunktion -- ;

[OBJECT_FUNCTION] MAX = 100*Is3 + 170*Il3 + 160*Ip3 - 20*(Is1 + Il1 + Ip1) - 35*(Is2 + Il2 + Ip2);
```

### Känslighetsrapport

| Variable | Value    | Reduced Cost |
| -------- | -------- | ------------ |
| XS1      | 0.000000 | 8.888889     |
| XL1      | 1100.000 | 0.000000     |
| XP1      | 111.1111 | 0.000000     |
| XS2      | 700.0000 | 0.000000     |
| XL2      | 0.000000 | 2.222222     |
| XP2      | 722.2222 | 0.000000     |
| XS3      | 1000.000 | 0.000000     |
| XL3      | 0.000000 | 3.333333     |
| XP3      | 333.3333 | 0.000000     |
| IS0      | 800.0000 | 0.000000     |
| IS1      | 100.0000 | 0.000000     |
| IS2      | 0.000000 | 4.444444     |
| IS3      | 400.0000 | 0.000000     |
| IL0      | 500.0000 | 0.000000     |
| IL1      | 1200.000 | 0.000000     |
| IL2      | 700.0000 | 0.000000     |
| IL3      | 0.000000 | 1.666667     |
| IP0      | 150.0000 | 0.000000     |
| IP1      | 161.1111 | 0.000000     |
| IP2      | 583.3333 | 0.000000     |
| IP3      | 516.6667 | 0.000000     |
| XLL      | 0.000000 | 0.000000     |

| Row                  | Slack or Surplus | Dual Price |
| -------------------- | ---------------- | ---------- |
| PRODUCTION_S1        | 0.000000         | 0.000000   |
| PRODUCTION_L1        | 1100.000         | 0.000000   |
| PRODUCTION_P1        | 111.1111         | 0.000000   |
| PRODUCTION_S2        | 700.0000         | 0.000000   |
| PRODUCTION_L2        | 0.000000         | 0.000000   |
| PRODUCTION_P2        | 722.2222         | 0.000000   |
| PRODUCTION_S3        | 1000.000         | 0.000000   |
| PRODUCTION_L3        | 0.000000         | 0.000000   |
| PRODUCTION_P3        | 333.3333         | 0.000000   |
| INV_S0               | 0.000000         | 49.44444   |
| INV_S1               | 100.0000         | 0.000000   |
| INV_S2               | 0.000000         | 0.000000   |
| INV_S3               | 400.0000         | 0.000000   |
| INV_I0               | 0.000000         | 116.6667   |
| INV_I1               | 1200.000         | 0.000000   |
| INV_I2               | 700.0000         | 0.000000   |
| INV_I3               | 0.000000         | 0.000000   |
| INV_P0               | 0.000000         | 105.0000   |
| INV_P1               | 161.1111         | 0.000000   |
| INV_P2               | 583.3333         | 0.000000   |
| INV_P3               | 516.6667         | 0.000000   |
| BALANCE_S_MONTH_1    | 0.000000         | -49.44444  |
| BALANCE_S_MONTH_2    | 0.000000         | -69.44444  |
| BALANCE_S_MONTH_3    | 0.000000         | -100.0000  |
| BALANCE_L_MONTH_1    | 0.000000         | -116.6667  |
| BALANCE_L_MONTH_2    | 0.000000         | -136.6667  |
| BALANCE_L_MONTH_3    | 0.000000         | -171.6667  |
| BALANCE_P_MONTH_1    | 0.000000         | -105.0000  |
| BALANCE_P_MONTH_2    | 0.000000         | -125.0000  |
| BALANCE_P_MONTH_3    | 0.000000         | -160.0000  |
| PUNCHING_MONTH_1     | 236.6667         | 0.000000   |
| PUNCHING_MONTH_2     | 73.33333         | 0.000000   |
| PUNCHING_MONTH_3     | 0.000000         | 83.33333   |
| FORMING_MONTH_1      | 0.000000         | 233.3333   |
| FORMING_MONTH_2      | 0.000000         | 277.7778   |
| FORMING_MONTH_3      | 0.000000         | 300.0000   |
| ASSEMBLING_S_MONTH_1 | 540.0000         | 0.000000   |
| ASSEMBLING_S_MONTH_2 | 290.0000         | 0.000000   |
| ASSEMBLING_S_MONTH_3 | 150.0000         | 0.000000   |
| ASSEMBLING_P_MONTH_1 | 406.6667         | 0.000000   |
| ASSEMBLING_P_MONTH_2 | 38.88889         | 0.000000   |
| ASSEMBLING_P_MONTH_3 | 233.3333         | 0.000000   |
| OBJECT_FUNCTION      | 48527.78         | 1.000000   |
