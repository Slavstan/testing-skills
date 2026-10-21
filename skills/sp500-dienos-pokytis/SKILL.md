---
name: sp500-dienos-pokytis
description: Patikrina naujausią S&P 500 indekso reikšmę ir apskaičiuoja pokytį, palyginti su ankstesnės prekybos sesijos uždarymo reikšme. Naudok visada, kai vartotojas prašo S&P 500, SPX, JAV akcijų rinkos indekso dabartinės ar paskutinės uždarymo reikšmės, dienos pokyčio, procentinio pokyčio arba trumpos dienos rinkos apžvalgos.
---

# S&P 500 dienos pokyčio tikrinimas

## Tikslas

Pateik patikimą, datuotą S&P 500 indekso reikšmę ir palygink ją su **ankstesnės prekybos sesijos uždarymo reikšme**. Tai informacinė rinkos suvestinė, ne investavimo rekomendacija.

## Darbo eiga

1. **Patikrink naujausius duomenis internete kiekvieną kartą.** Niekada nepasikliauk atmintyje esančiomis kainomis. Pirmenybę teik FRED S&P 500 serijai (simbolis `SP500`, https://fred.stlouisfed.org/series/SP500) naujausioms dienos uždarymo reikšmėms. Jei reikia šiandienos prekybos metu esančios reikšmės, papildomai tikrink patikimą rinkos duomenų šaltinį, pavyzdžiui, Yahoo Finance (https://finance.yahoo.com/quote/%5EGSPC/history/), ir pažymėk, jei kotiruotė vėluoja.
2. **Nustatyk palyginamus duomenų taškus:** naujausią galiojančią uždarymo reikšmę ir ankstesnės prekybos sesijos uždarymo reikšmę. „Praeita diena“ reiškia ankstesnę prekybos sesiją, o ne būtinai kalendorinę dieną. Savaitgaliais ir švenčių dienomis naudok paskutines dvi prekybos sesijas.
3. **Atskirk uždarymo duomenis nuo einamosios kotiruotės.** Jei JAV rinka dar atidaryta, pateik dabartinę reikšmę kaip intraday / real-time arba delayed quote (kaip nurodo šaltinis), o pokytį skaičiuok prieš paskutinį uždarymą. Jei naudotas tik uždarymo duomenų šaltinis, neskelbk jo kaip realaus laiko kainos.
4. **Apskaičiuok pokytį:**
   - Absoliutus pokytis = naujausia reikšmė − palyginimo reikšmė.
   - Procentinis pokytis = (absoliutus pokytis / palyginimo reikšmė) × 100.
   - Teigiamas pokytis reiškia kilimą, neigiamas – kritimą, nulis – nepakitusį lygį.
5. **Patikrink skaičiavimą ir datas.** Skaičiuok iš neapvalintų šaltinio skaičių; pateik indekso punktus ir procentą su 2 skaitmenimis po kablelio. Jei šaltiniai nesutampa, paaiškink, kuris matas pateiktas, ir nenaudok skirtingų matų viename skaičiavime.
6. **Jei duomenų nėra arba jie pasenę,** aiškiai pasakyk, ko nepavyko patikrinti. Neišgalvok reikšmių, datų, realaus laiko statuso ar šaltinių.

## Atsakymo formatas

Atsakyk lietuviškai, glaustai:

- **S&P 500:** [reikšmė] ([uždarymas / einamoji kotiruotė], [data ir laikas arba duomenų data])
- **Palyginimas:** [ankstesnės prekybos sesijos uždarymas] ([data])
- **Pokytis:** [+/- X.XX punkto] ([+/- X.XX %]) — [pakilo / nukrito / nepakito]
- **Šaltiniai:** [tiesioginės nuorodos į naudotus duomenis]
- **Pastaba:** nurodyk vėlavimą, jei šaltinis kotiruotę pateikia su vėlavimu; nepridėk investavimo patarimo.

Jei vartotojas prašo tik paskutinio uždarymo, pateik paskutinį uždarymą ir jo pokytį nuo ankstesnės prekybos sesijos. Jei prašo šiandienos judėjimo, atskirk einamąją kotiruotę nuo paskutinio uždarymo ir nurodyk atitinkamą laiką.
