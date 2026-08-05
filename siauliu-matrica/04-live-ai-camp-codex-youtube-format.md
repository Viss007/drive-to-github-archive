# Live AI Camp — YouTube formato koncepcija

**Statusas:** Nauja kryptis / setup planas
**Atnaujinta:** 2026-08-06
**Tikslas:** Išbandyti YouTube formatą, kuriame du žmonės išvažiuoja į gamtą, palieka pagrindinį kompiuterį namuose ir telefonu kalbasi su AI, o AI + coding agentas nuotoliniu būdu koordinuoja realų darbą kompiuteryje.

## 1. Pagrindinė idėja

Mes išvažiuojame į gamtą su telefonu. Kompiuteris lieka namuose.

Telefonas tampa valdymo tašku:

**Žmogus → balsas / telefonas → AI → coding agentas → kompiuteris → realus rezultatas**

Tai nėra paprastas „AI parašė kodą“ video. Esmė yra parodyti visą darbo procesą kaip eksperimentą: ar žmogus, būdamas ne prie kompiuterio, gali telefonu koordinuoti realaus projekto kūrimą.

Galimas pirmojo epizodo hook'as:

> „Mes išvažiavom į mišką ir palikom kompiuterį namuose. Dabar pabandysim telefonu sukurti realų dalyką.“

## 2. Kodėl tai įdomu žiūrovui

- Fizinis kontrastas: gamta vs. namuose dirbantis kompiuteris.
- Aiškus eksperimentas su pradžia, rizika ir rezultatu.
- AI nėra vien kalbantis personažas — jis tampa darbo koordinavimo sluoksniu.
- Žiūrovas gali matyti realius veiksmus ir klaidas.
- Formatą galima kartoti su skirtingais projektais.

## 3. Svarbi architektūrinė pastaba

Šiame dokumente sąmoningai nenurodoma, kad dabartinė ChatGPT sesija automatiškai gali valdyti konkretų vartotojo kompiuterį. Prieš įrašymą reikia praktiškai patikrinti konkrečią Codex / agent aplinką, jos remote-control galimybes, autentikaciją, terminalo prieigą ir leidimų modelį.

Jeigu tiesioginis telefono → agento → kompiuterio workflow nėra prieinamas, turi būti paruoštas fallback variantas. RustDesk / AnyDesk gali būti naudojamas kaip techninis atsarginis kelias, tačiau jis nėra pagrindinė kūrybinė patirtis, nes desktop IDE UI nėra patogus telefono ekranui.

## 4. Pageidaujamas workflow

### A. Prieš išvykstant

1. Kompiuteris paliekamas įjungtas ir prijungtas prie interneto.
2. Projekte paruošiama aiški working directory.
3. Coding agentas patikrinamas su maža saugia užduotimi.
4. Paruošiamas būdas stebėti agento darbą ir rezultatus.
5. Sukuriamas backup / manual checkpoint prieš filmavimą.
6. Patikrinama, kad jautrūs raktai, slaptažodžiai ir privatūs duomenys nepatektų į video.

### B. Gamtoje

1. Telefonas naudojamas kaip pagrindinis operatoriaus įrenginys.
2. Žmogus balsu paaiškina tikslą AI.
3. AI suskaido tikslą į konkrečius veiksmus.
4. Coding agentas vykdo techninius pakeitimus.
5. Žmogus periodiškai patikrina rezultatą.
6. Jei kažkas sugenda, problema sprendžiama realiu laiku.
7. Pabaigoje parodomas realus sukurtas rezultatas.

### C. Video struktūra

**0:00–0:20 — Hook**

„Kompiuteris liko namuose. Mes esam miške. Šiandien pabandysim sukurti realų projektą telefonu.“

**0:20–1:00 — Taisyklės**

Paaiškinti, ką leidžiama daryti AI, kas lieka žmogaus sprendimu ir koks turi būti galutinis rezultatas.

**1:00–3:00 — Pirmas bandymas**

Duodama pirma užduotis agentui. Rodomos pirmos reakcijos, klaidos arba netikėti rezultatai.

**3:00–8:00 — Build loop**

Trumpi ciklai: užduotis → agentas → rezultatas → žmogaus sprendimas → kita užduotis.

**8:00–10:00 — Crisis / surprise**

Specialiai neperdėti: reali klaida, neaiškus rezultatas arba netikėtas agento pasirinkimas.

**10:00–12:00 — Final reveal**

Parodomas kompiuteryje veikiantis rezultatas.

**12:00+ — Verdict**

Ar galima realiai dirbti taip, nebūnant prie kompiuterio?

## 5. Pirmojo eksperimento pasirinkimas

Pirmam video nereikia bandyti sukurti didelės SaaS platformos. Reikia užduoties, kurią galima užbaigti per vieną filmavimo sesiją.

Geri kandidatai:

- mažas web tool'as;
- landing page;
- mini interaktyvus puslapis;
- mažas VissAI demo;
- paprastas API + UI projektas;
- esamo projekto konkretus feature'as.

Pirmas eksperimentas turi turėti aiškų „done“ kriterijų.

## 6. AI vaidmuo

AI turėtų būti rodomas ne kaip magiškas robotas, kuris viską padaro pats, o kaip **operatoriaus partneris / koordinavimo sluoksnis**.

Žmogus:
- nustato tikslą;
- priima svarbius sprendimus;
- vertina rezultatą;
- patvirtina rizikingus veiksmus.

AI:
- analizuoja;
- planuoja;
- formuluoja užduotis;
- koordinuoja agentą;
- padeda diagnozuoti klaidas.

Coding agentas:
- skaito projektą;
- keičia failus;
- paleidžia testus;
- tikrina rezultatą;
- raportuoja atliktus veiksmus.

## 7. Operatorinis saugumas

Prieš realų filmavimą būtina:

- nenaudoti produkcinių kredencialų, kurių nereikia eksperimentui;
- apriboti agento prieigą iki konkretaus projekto;
- turėti manual checkpoint / backup;
- nefilmuoti API raktų, cookies, SSH raktų ar asmeninių duomenų;
- aiškiai atskirti demonstracinę aplinką nuo produkcijos;
- turėti manual revert planą, jei agentas padaro netinkamus pakeitimus.

## 8. Techninio setupo klausimai, kuriuos turi išspręsti coding agentas

Prieš pradedant build'ą Cursor / Codex agentui reikia liepti:

1. Apžiūrėti esamą repo ir nustatyti, kokį projektą pirmam eksperimentui saugiausia naudoti.
2. Patikrinti, kokia remote-agent / terminalo / browser prieiga jau prieinama.
3. Nekeisti architektūros vien dėl video.
4. Paruošti saugų demo workflow.
5. Sukurti aiškius start / stop / health-check veiksmus.
6. Paruošti žmogui suprantamą statuso raportą.
7. Dokumentuoti viską `05-codex-agent-setup-prompt.md` ir susijusiuose failuose.

## 9. Fallback architektūra

Jei telefono → Codex → kompiuterio tiesioginis workflow neveikia:

**Variantas B:** telefonas → remote desktop → kompiuteris → agentas.

RustDesk / AnyDesk yra tik techninis fallback. Video istorijoje nereikia akcentuoti remote-desktop įrankio kaip produkto; svarbiausia išlieka eksperimentas ir realus rezultatas.

## 10. Sėkmės kriterijai

Pirmas eksperimentas laikomas sėkmingu, jei:

- žmogus gali pradėti ir tęsti darbą telefonu;
- agentas gali savarankiškai atlikti didžiąją dalį mechaninio darbo;
- klaidas galima diagnozuoti ir išspręsti nuotoliniu būdu;
- galutinis rezultatas realiai veikia kompiuteryje;
- nereikia viso laiko būti prisijungus prie desktop IDE;
- workflow pakankamai stabilus, kad jį būtų galima filmuoti dar kartą.

## 11. Kūrybinė taisyklė

**Nefalsifikuoti rezultato.**

Jeigu agentas sugenda — tai yra video dalis.
Jeigu reikia grįžti prie kompiuterio — tai yra video dalis.
Jeigu AI priima blogą sprendimą — tai yra video dalis.

Šio formato vertė yra tikras eksperimentas, o ne tariamai tobula AI demonstracija.

---

Šis dokumentas papildo ankstesnę „Šiaulių Matricos“ / AI psichodelinės komedijos kūrybinę kryptį nauju **live AI camp / remote coding** formatu. Ankstesni dokumentai lieka kaip kūrybinis archyvas; šis dokumentas aprašo atskirą realaus darbo + YouTube eksperimento formatą.