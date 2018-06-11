# Komandos

## Registrų ir atminties valdymo komandos

* LDN R 000012FF - Į registrą patalpinamas skaičius. Vietoje R turi būti raidė A arba B, kuri nurodo, su kuriuo registru dirbama; vietoje 000012FF skaičius kurį įkeliame. Atmintyje saugoma komanda: [ ‘L’ | ‘D’ | ‘N’ | ‘R’ ] [ 00 | 00 | 12 | FF ]

* LDM R PA - Į registrą įkeliamas žodis iš atminties. R - registras; P - puslapis (0-F), A - a-tasis žodis puslapyje (0-F). Atmintyje saugoma komanda: [ ‘L’ | ‘D’ | ‘M’ | ‘R’ ] [ 00 | 00 | 0P | 0A ]

* SA 000012FF PA - Į atmintį patalpina skaičių. Atmintyje saugoma komanda: [ ‘S’ | ‘A’ | 00 | 00 ] [ 12 | FF | 0P | 0A ]

* SVR R PA - Į atmintį patalpina registro reikšmę. Atmintyje saugoma komanda: [ ‘S’ | ‘V’ | ‘R’ | ‘R’ ] [ 00 | 00 | 0P | 0A ]

* CP R R - Nukopijuoja pirmojo registro reikšmę į antrąjį.

## Aritmetinės komandos:

* AD R R - Sudeda dviejų registrų reikšmes ir rezultatą patalpiną į pirmąjį registrą.

* SB R R - Iš pirmojo registro atima antrojo registro reikšmę ir rezultatą patalpina į pirmą.

* ML R R - Pirmąjį registrą padaugina iš antrojo ir rezultatą patalpina per abu registrus: pirmajame žemesnės eilės dalis antrajame aukštesnės eilės dalis.

* DV R R - Pirmąjį registrą padalina iš antrojo ir rezultatą patalpina pirmame, o liekaną antrajame.

* CM R R - Palyginimas. Iš pirmojo registro atimamas antrasis ir pakeičiamos požymio registro reikšmės, bet atimties rezultatas neišsaugomas (A ir B registrų reikšmės nepasikeičia).

## Loginės komandos:

* XR R R - XOR. Rezultatas išsaugomas pirmajame.

* AN R R - AND

* OR R R - OR

* NOT R - Registro reikšmės neigimas.

* SR R R - Pirmojo registro postūmis į dešinę per vieną bitą, tiek kartų kokia reikšmė yra antrajame.

* SL R R - Postūmis i kairę.

## Valdymo perdavimo komandos:

* JUMP PA - Besąlyginis valdymo perdavimas. Komandų skaitliuko reikšmė tampa PA. Atmintyje saugoma komanda: [ ‘J’ | ‘U’ | ‘M’ | ‘P’ ] [ 00 | 00 | 0P | 0A ]

* JMPG PA - Jei carry požymis yra 0, tai IC reikšmė tampa PA.

* JMPL PA - Jei carry požymis yra 1, tai IC reikšmė tampa PA.

* JMPZ PA - Jei zero požymis yra 1, tai IC reikšmė tampa PA.

* JPNZ PA - Jei zero požymis yra 0, tai IC reikšmė tampa PA.

* LOOP PA - sumažina A registro reikšmę vienetu ir jei A nėra lygus nuliui, tai IC reikšmė tampa PA.

* HALT - Programa baigia darbą. Komanda pakeičia SI reikšmę į 8 

## Darbo su ekranu ir klaviatūra komandos:

* PRNT - A Registre laikomas adresas, iš kurios vietos atmintyje norima spausdinti seką į ekraną. B registre - kelis simbolius norima išspausdinti. Komanda pakeičia SI reikšmę į 1.

* PNUM - A Registre laikomas adresas, iš kurios vietos atmintyje norima spausdinti žodį į ekraną. Komanda pakeičia SI reikšmę į 9.

* SCAN - A registre adresas į kurią vietą atmintyje bus rašoma. B - kiek simbolių. Komanda pakeičia SI reikšmę į 2.

## Darbo su failais komandos:

* OPEN - A Registre laikomas adresas, iš kurios vietos atmintyje bus paimtas failo pavadinimas, kuris pasibaigia tuščiu baitu. Įvykdžius komandą registre A atsiranda reikšmė (“handle”), kurią bus pasiekiamas tas failas arba 0000 jei nepavyko atidaryti. B registre 1, jei norima į failą rašyti, 2, jei norima iš failo skaityti. Komanda pakeičia SI reikšmę į 3.

* CLOS- A registre skaičius identifikuojantis failą, kurį norima uždaryti. Įvykdžius komandą registre A atsiranda reikšmė 0000, jei pavyko uždaryti. Komanda pakeičia SI reikšmę į 4.

* DELT - A Registre laikomas adresas, iš kurios vietos atmintyje bus paimtas failo pavadinimas,kurį norima ištrinti. Įvykdžius komandą registre A atsiranda reikšmė, 0000 jei pavyko ištrinti. Komanda pakeičia SI reikšmę į 5.

* READ - A registre failo handle. B registre adresas į vietą atmintyje kur norima rašyti simbolius iš failo. Pirmas žodis nurodo kiek simbolių norima skaityti. Įvykdžius komandą pirmas žodis atmintyje reiškia kiek buvo nuskaityta simbolių iš failo, o sekantys simboliai yra tekstas iš failo. Komanda pakeičia SI reikšmę į 6.

* WRIT - A registre failo handle. B registre adresas į vietą atmintyje, iš kurios norima perkelti žodžius į failą. Pirmas žodis nurodo kiek simbolių norima rašyti. Įvykdžius komandą pirmas žodis atmintyje reiškia kiek buvo parašyta simbolių į failą. Komanda pakeičia SI reikšmę į 7.

## Požymių komandos:

* SVF R - Į flag registrą patalpina darbinio registro reikšmę.

* LDF R - Į darbinį registrą patalpina flag registro reikšmę.

## Prietaisų instrukcijos

* POWR - a registre prietaiso numeris, b: 1 - įjungti; 0 - išjungti; 2 - jei įjungta išjungti ir atvirkščiai; 3 pakeisti b registro reikšmę į būseną (1 - ON; 0 - OFF) (SI = 10)

* SVAL - a registre prietaiso numeris, b - reikšmė kurią nustatyti (SI = 11)

* GVAL - a registre prietaiso numeris. Pakeičia b reikšmę į prietaiso reikšmę. (SI = 12)

* TYPE - a registre prietaiso numeris, gražina prietaiso tipą į b registrą arba 0 jei nėra prietaiso su numeriu a.(SI = 13)

Pastaba: jeigu nėra prietaiso su nurodytu numeriu, tai nieko nedaro tik paleidžia toliau vm.
