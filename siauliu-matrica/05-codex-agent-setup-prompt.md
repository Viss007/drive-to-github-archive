# CODING AGENT BRIEF — Live AI Camp / Remote Coding YouTube Experiment

> Šį dokumentą galima tiesiogiai perduoti Cursor arba Codex coding agentui.

## Objective

Paruošti techninį setup'ą YouTube eksperimentui, kuriame operatorius išvyksta į gamtą, o pagrindinis kompiuteris lieka namuose. Operatorius telefonu kalbasi su AI ir nori nuotoliniu būdu koordinuoti coding agentą, kuris realiai dirba su projektu.

Galutinis workflow:

**phone → AI conversation → coding-agent task → computer/project → verification → result**

Tikslas nėra sukurti naują AI platformą. Tikslas — saugiai ir patikimai paruošti egzistuojantį development workflow taip, kad jį būtų galima naudoti realiame YouTube filmavime.

## Context

Kūrybinė kryptis dokumentuota:

- `siauliu-matrica/01-psichodeline-komedija-archyvai.md`
- `siauliu-matrica/02-youtube-channel-plan-v2.md`
- `siauliu-matrica/03-youtube-channel-plan-v3.md`
- `siauliu-matrica/04-live-ai-camp-codex-youtube-format.md`

Pirmas video turėtų būti nedidelis, užbaigiamas per vieną sesiją ir turėti aiškų demonstracinį rezultatą.

## First task: inspect before changing

Pirmiausia nieko neperrašinėk.

1. Apžiūrėk repo struktūrą.
2. Nustatyk, kuris esamas projektas geriausiai tinka pirmajam saugiam eksperimentui.
3. Nustatyk dabartinį runtime / package manager / start commands.
4. Inventorizuok, kokios agento galimybės jau egzistuoja: terminalas, browser, local server, process management, remote access.
5. Patikrink, ar naudojamas IDE jau turi Codex arba kitą tinkamą coding-agent integraciją / extension.
6. Patikrink, ar tokia integracija gali suteikti reikalingą workflow: agento paleidimą, terminalo darbą, projekto failų keitimą, testavimą, browser verification ir nuotolinį operatoriaus valdymą.
7. Patikrink, ar projekte jau yra health-check, demo, testavimo ar preview mechanizmai.
8. Patikrink, ar yra jautrių credentials / secrets ir kaip juos izoliuoti.

## Installation principle: existing integration first

**Neskubėk diegti atskiros Codex aplikacijos.**

Pirmiausia nustatyk, ar dabartinis IDE jau turi oficialią arba tinkamą Codex integraciją / extension, kuri patenkina mūsų poreikius.

Prioritetas:

1. **Esamas IDE + Codex integracija** — pirmas pasirinkimas, jei funkcionalumas pakankamas.
2. **Esamas IDE + kita tinkama agento integracija** — tik jei ji geriau atitinka workflow.
3. **Atskira Codex aplikacija** — tik jeigu IDE integracija negali suteikti reikalingo remote/operator workflow.
4. **Remote desktop (RustDesk / AnyDesk)** — tik kaip fallback, o ne pagrindinė architektūra.

Nediek kelių agento klientų vienu metu vien tam, kad „gal prireiks“. Pirmiausia audituok, kas jau įdiegta ir ką realiai gali atlikti.

### Ką agentas turi patikrinti

- IDE pavadinimą ir versiją;
- įdiegtas AI / coding-agent extensions;
- ar Codex integracija jau prieinama;
- ar integracija leidžia dirbti su lokaliu projektu;
- ar galima paleisti terminalo komandas;
- ar galima paleisti dev serverį ir testus;
- ar galima atlikti browser/UI verification;
- ar yra patogus statuso / approval workflow;
- ar yra remote access / remote session galimybė;
- kokie papildomi komponentai būtų būtini;
- kokie komponentai būtų nereikalingi.

Jeigu dokumentacija ar konkreti funkcija nėra aiški, **neapsimesk, kad ji egzistuoja**. Pažymėk kaip `UNKNOWN` ir nurodyk, ką reikia praktiškai patikrinti.

## Required architecture

Prioritetinė architektūra:

**Phone**
→ AI conversation / operator interface
→ task sent to coding agent
→ coding agent operates on local project
→ tests / build / browser verification
→ concise status report
→ operator decides next task

Nenaudok remote desktop kaip pagrindinės architektūros, jei konkreti agento / IDE aplinka leidžia patogiai vykdyti projektą nuotoliniu būdu.

Remote desktop (RustDesk / AnyDesk ar panašus) laikomas tik fallback'u.

## Constraints

- Nenaudoti Git workflow kaip būtinos projekto dalies.
- Vietoj to naudoti manual checkpoint / backup / changed-file audit / manual revert.
- Nekeisti esamos projekto architektūros be priežasties.
- Neįdiegti nereikalingų SaaS servisų vien dėl demonstracijos.
- Neįdiegti atskiro Codex app, jeigu esama IDE integracija jau patenkina poreikius.
- Neįtraukti produkcinių API raktų ar privačių credentials į video workflow.
- Nerodyti secrets terminalo, browser ar ekrano capture'uose.
- Agentas turi turėti aiškias ribas, kokiame kataloge gali dirbti.
- Kiekvienas automatinis pakeitimas turi būti patikrinamas.
- Pirmas demo turi būti mažas ir deterministinis.

## What to build / prepare

Jei repo jau turi tinkamą projektą, paruošk jį eksperimentui.

Reikia turėti:

### 1. One-command start

Aiškus command, kuriuo galima paleisti demo.

### 2. One-command health check

Patikrinimas, kuris pasako:

- ar serveris veikia;
- ar reikalingi portai pasiekiami;
- ar pagrindinis endpoint / page atsako;
- ar nėra akivaizdžių runtime errors.

### 3. Verification workflow

Po agento pakeitimų turi būti galima atlikti:

- build / typecheck, jei taikoma;
- testus, jei jie egzistuoja;
- browser verification, jei UI projektas;
- basic smoke test.

### 4. Changed-file audit

Agentas kiekvieno task pabaigoje turi pateikti:

- pakeistus failus;
- ką kiekviename pakeitė;
- kokius testus / checks paleido;
- ar rezultatas patvirtintas;
- kas liko nepatikrinta.

### 5. Recovery procedure

Paruošk paprastą manual recovery procedūrą:

1. sustabdyti agento darbą;
2. nustatyti paskutinį gerą checkpoint;
3. atstatyti pakeistus failus iš manual backup / snapshot;
4. paleisti health check;
5. tik tada tęsti.

## Operator experience

Operatorius neturi būti programuotojas, kad galėtų atlikti demonstraciją.

Operatoriui reikia tik:

1. Pasakyti AI, ką nori pasiekti.
2. Gauti aiškų task planą.
3. Patvirtinti rizikingus veiksmus.
4. Stebėti progress.
5. Gauti rezultatą.

Techninė agento kalba neturi būti naudojama kaip pagrindinis operatoriaus UI.

## YouTube requirements

Setup turi būti filmuojamas.

Todėl:

- statusai turi būti trumpi ir suprantami;
- terminalo output neturi būti chaotiškas be reikalo;
- svarbūs momentai turi būti lengvai parodyti ekrane;
- klaidos turi būti išsaugomos, jei jos įdomios istorijai;
- negalima dėl video sukurti netikrų „success“ rezultatų.

## Recommended first demo

Pasirink vieną nedidelį rezultatą, pvz.:

- landing page pakeitimas;
- mažas interaktyvus web tool;
- nedidelis VissAI demo feature;
- esamo UI feature;
- maža API + UI funkcija.

Venk didelio produkto kūrimo pirmame bandyme.

## Do not do yet

Nedaryk:

- pilno autonominio orchestratoriaus;
- multi-agent sistemos;
- naujos SaaS infrastruktūros;
- sudėtingo remote-control produkto;
- nereikalingo auth sluoksnio;
- production deployment vien dėl pirmo video;
- atskiros Codex aplikacijos, kol nepatikrinta esama IDE integracija.

Pirmas tikslas yra **patikimas demonstracinis remote coding loop**.

## Verification checklist

Prieš laikant setup'ą paruoštu:

- [ ] Repo / projektas identifikuotas.
- [ ] Working directory aiški.
- [ ] Naudojamas IDE identifikuotas.
- [ ] Esamos Codex / coding-agent integracijos identifikuotos.
- [ ] Patikrinta, ar IDE integracija patenkina remote workflow poreikius.
- [ ] Tik jeigu reikia, pasirinkta atskira Codex aplikacija.
- [ ] Start command veikia.
- [ ] Health check veikia.
- [ ] Agentas gali atlikti mažą pakeitimą.
- [ ] Pakeitimas patikrinamas.
- [ ] Browser/UI patikrinamas, jei taikoma.
- [ ] Manual checkpoint sukurtas.
- [ ] Recovery procedūra išbandyta bent kartą.
- [ ] Secrets neatsidengia workflow metu.
- [ ] Operatorius gali suprasti agento statusą nežiūrėdamas į visą terminalo output.
- [ ] Yra aiškus „done“ kriterijus pirmajam video.

## Expected report format

Baigęs auditą, pirmiausia pateik:

### Current state
- repo / projektas:
- runtime:
- IDE + versija:
- įdiegtos AI / coding-agent integracijos:
- Codex integracijos statusas:
- ar reikia atskiros Codex aplikacijos: YES / NO / UNKNOWN
- start command:
- health check:
- existing agent capabilities:
- blockers:

### Recommended setup
- pasirinkta architektūra:
- kodėl:
- existing IDE integration pakanka: YES / NO / UNKNOWN
- jei nepakanka, ko konkrečiai trūksta:
- reikalingi pakeitimai:

### Files to change
- `path` — reason

### Installation decision
- naudoti esamą IDE integraciją: YES / NO
- diegti atskirą Codex app: YES / NO
- naudoti remote desktop fallback: YES / NO
- reason:

### Safety / recovery
- checkpoint:
- backup:
- manual revert:

### Verification
- commands:
- browser checks:
- remote workflow checks:
- expected result:

### YouTube demo
- ką operatorius pasako telefonu:
- ką agentas daro:
- ką žiūrovas mato:
- final reveal:

### STOP
Po audito ir plano **nestartuok didelio build'o automatiškai**, jei yra architektūrinis neaiškumas. Pirmiausia aiškiai parodyk planą, dabartines galimybes, diegimo pasirinkimą ir rizikas.
