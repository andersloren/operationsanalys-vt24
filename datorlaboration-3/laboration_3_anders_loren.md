# Inlämning 1 datorlaboration 3

<p><strong>Namn: </strong>Anders Lorén</p>
<p><strong>Personnummer: </strong>19840102-5534</p>
<p><strong>Laborationsgrupp: </strong>38</p>
<p><strong>GitHub: </strong>https://github.com/andersloren/operationsanalys-vt24/tree/master/datorlaboration-2</p>

## Uppft 1 (jämnt nummer)

### Tabell

| Moment | Aktivitet                | Föregångare | Tid     |
| ------ | ------------------------ | ----------- | ------- |
| 1      | dränering och markarbete | -           | 22 (20) |
| 2      | gruda grund              | 1           | 10      |
| 3      | avlopp, vatten (yttre)   | 1           | 8       |
| 4      | väggar                   | 2           | 6       |
| 5      | tak                      | 4           | 4       |
| 6      | elinstallation           | 4           | 6       |
| 7      | avlopp, vatten (inre)    | 4           | 6       |
| 8      | markarbeten              | 3           | 9 (5)   |
| 9      | fönster                  | 4           | 4       |
| 10     | målning                  | 6, 9        | 6       |
| 11     | tapetsering              | 6, 9, 10    | 8       |
| 12     | staket, grindar          | 8           | 3       |
| 13     | installation av vitvaror | 11, 10      | 4       |
| 14     | kontroll                 | 13, 12, 8   | 3       |

### Kod

```
! Laboration 3, Uppgift 1;

! Beslutsvariabler;

t1>=0;
t2>=0;
t3>=0;
t4>=0;
t5>=0;
t6>=0;
t7>=0;
t8>=0;
t9>=0;
t10>=0;
t11>=0;
t12>=0;
t13>=0;
t14>=0;
t15>=0;

! Bivillkor;

t2-t1>=22;
t3-t1>=22;
t4-t2>=10;
t8-t3>=8;
t5-t4>=6;
t6-t4>=6;
t7-t4>=6;
t9-t4>=6;
t10-t6>=6;
t12-t8>=9;
t14-t8>=9;
t10-t9>=4;
t11-t10>=6;
t13-t11>=8;
t14-t13>=4;
t15-t14>=3;

! Målfunktion;

min = t15-t1;
```

### Svar:

Målfunktionens värde = 65 timmar

| Kritiska moment |
| --------------- |
| 1               |
| 2               |
| 4               |
| 6               |
| 10              |
| 11              |
| 13              |
| 14              |

Moment 12 måste inledas senast målfunktionens värde - A12(tid) vilket är:

65 - 3 = 62 timmar efter att projektet startats.

## Uppgift 2

### Kod

```
! Datorlaboration 3, Uppgift 2

! Beslutsvariabler;

!xj = { 1, om investering j väljs, j = A, B, C, ... , I
      { 0, annars

! bivillkor;

@BIN( xa);
@BIN( xb);
@BIN( xc);
@BIN( xd);
@BIN( xe);
@BIN( xf);
@BIN( xg);
@BIN( xh);
@BIN( xi);

xa + xf - xb <= 1;
xd + xh <= 1;
xa + xc + xd + xf + xg + xi >= 4;
xb + xe + xh  <= 2;
xb + xe + xh  >= 1;

[budget] 9*xa + 7*xb + 12*xc + 20*xd + 8*xe + 15*xf + 9*xg + 16*xh + 13*xi <= 80;

! Målfunktion;

max = 18*xa + 21*Xb + 18*xc + 30*xd + 24*xe + 20*xf + 20*xg + 30*xh + 23*xi;
```

Optimallösning

| Investeringar |
| ------------- |
| A             |
| B             |
| C             |
| D             |
| E             |
| G             |
| I             |
