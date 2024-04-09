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

#### recuded cost

Lösningen ger ett större värde än 0 på samtliga variabler vilket innebär att reduced cost är 0 för samtliga variabler.

#### Slack or Suprplus samt Dual Price

<p>Protein har ett dual price på ca -59. Det innebär att om värdet i högerled för detta bivillkor ökar med 1, så ökar målfunktionens värde med ca 59. Vi vill ju minimera målfunktionen, och om proteinet måste ökas i foderblandningen kommer detta innebära att fodret blir dyrare. På motsvarande sätt kommer fodret bli dyrare om vi ökar fettkravet med 1.</p>
<p>Det enda bivillkor, där vi justerar högerledet med 1, som kan ett lägre värde på målfunktionen är minimikravet på mineraler, som då skulle subtrahera cirka 18 från värdet på målfunktionen. </p>
