# Bankas

Sukurti API naudojantis Express.js, kuris leistų susikurti banko sąskaitas, į jas įsinešti pinigų ir vykdyti pinigų pervedimus tarp sąskaitų.

Vienas asmuo gali turėti tik vieną saskaitą.

Visi pinigai yra ta pačia valiuta.

Visi duomenų mainai vyksta JSON formatu.

Visi pinigų mainai vyksta centais.

Visi pinigų "spausdinimai" vykdomi formatuojant teksta, pvz: `123,45 Eur`.

Užklausų adresai neturi būti jautrūs didžiosioms/mažosioms raidėms, t.y.

```
/api/account/{vardas}-{pavardė}
/api/account/john-doe
/api/account/John-doe
/api/account/John-Doe
/api/account/JOHN-DOE
```

## Reikalingi API endpoint'ai

### /api/account

> POST

```
/api/account
```

Perduodami duomenys:

-   vardas
-   pavardė
-   gimimo data (yyyy-mm-dd)

Reikalavimai:

-   saskaitą gali susikurti tik pilnameciai (18m)
-   vardo ir pavardės kombinacija turi būti unikali

> GET:

```
/api/account/john-doe
```

Grąžina paskyros savininko varda, pavardę ir gimimo datą

> DELETE:

```
/api/account/john-doe
```

Reikalavimai:

-   ištrinti galima tik jei sąskaitoje nėra pinigų

> PUT

```
/api/account/john-doe
```

Perduodami duomenys:

-   vardas
-   pavardė
-   gimimo data (yyyy-mm-dd)

Jei atnaujiname paskyros duomenis, tai siunčiama visa informacija, t.y. nepakitusi ir pakitusi kartu.

### /api/account/name

> GET

```
/api/account/john-doe/name
```

Grąžina vardą

> PUT

```
/api/account/john-doe/name
```

Perduodami duomenys:

-   vardas

Atnaujina vardą

### /api/account/surname

> GET

```
/api/account/john-doe/surname
```

Grąžina pavardę

> PUT

```
/api/account/john-doe/surname
```

Perduodami duomenys:

-   pavardė

Atnaujina pavardę

### /api/account/dob

> GET

```
/api/account/john-doe/dob
```

Grąžina gimimo datą

> PUT

```
/api/account/john-doe/dob
```

Perduodami duomenys:

-   gimimo data (yyyy-mm-dd)

Atnaujina gimimo datą

### /api/withdrawal

> POST

Perduodami duomenys:

-   pinigų kiekis
-   sąskaitos savininko vardas
-   sąskaitos savininko pavardė

Iš sąskaitos išimami pinigai

### /api/deposit

> POST

Perduodami duomenys:

-   pinigų kiekis
-   sąskaitos savininko vardas
-   sąskaitos savininko pavardė

Į saskaitą inešami pinigai

### /api/transfer

> POST

Perduodami duomenys:

-   iš kurios sąskaitos: vardas
-   iš kurios sąskaitos: pavardė
-   į kurią saskaitą: vardas
-   į kurią saskaitą: pavardė
-   pinigų kiekis

Iš vienos sąskaitos išskaitomi pinigai ir įskaitomi į kitą saskaitą

## Papildomai

Norintys papildomai gauti balų, kurių surinkimas vis vien negali viršyti maksimalios leistinos ribos (žiūrėti žemiau), gali papildomai atlikti šiuos veiksmus:

-   susikurti individualias užduotis per Github Issues (max 3 balai)
-   darbus organizuotis per Github Projects (max 3 balai)
-   individualius darbus atlikti atskiruose branch'uose ir juos atlikus - sulieti į pagrindinį branch'ą (max 4 balai)

Galimų gauti balų kiekis iš šios dalies bus apytikriai proporcingas užduočių kiekiui, kuris turėtų būti turbūt ties minimum 15.

## Vertinimas

-   Atskira repozitorija (1 balas)
-   README (2 balai):
    -   projekto aprašas
    -   kaip jį paleisti
    -   aprašyti visus viekiančius endpoint'us ir kaip jais naudotis
-   git istorija:
    -   0..10 - 0 balų
    -   11..20 - 1 balas
    -   20+ - 2 balai
-   Kiekvienas endpoint'as ir jo HTTP metodai yra verti po 5 balus:
    -   1 balas už teisingai grąžinta rezultatą
    -   2 balai už tinkamas validacijas (visas)
    -   1 balas už URL
    -   1 balas už gerai aprašyta dokumentaciją README faile:
        -   naudotina nuoroda
        -   http metodas
        -   perduodamų (jei reikia) duomenų formatas su jų tipais ir kitais apribojimais (jei taikoma)
        -   pavyzdinė nuoroda
        -   pavyzdiniai teisingi duomenys (jei taikoma)

Viso galima surinkti 70 balų.

```js
const availablePoints = 80;
const maxPoints = 70;
const maxMark = 10;
let collectedPoints = 0;
// calculating points...

const studentPoints = collectedPoints > maxPoints ? maxPoints : collectedPoints;
const divider = maxPoints / maxMark;
const studentMark = Math.floor(studentPoints / divider);

console.log('Your result:', studentMark);
```
