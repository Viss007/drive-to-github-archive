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
4. Patikrink, kokios agento galimybės jau egzistuoja: terminalas, browser, local server, process management, remote access.
5. Patikrink, ar projekte jau yra health-check, demo, testavimo ar preview mechanizmai.
6. Patikrink, ar yra jautrių credentials / secrets ir kaip juos izoliuoti.

## Required architecture

Prioritetinė architektūra:

**Phone**
→ AI conversation / operator interface
→ task sent to coding agent
→ coding agent operates on local project
→ tests / build / browser verification
→ concise status report
→ operator decides next task

Nenaudok remote desktop kaip pagrindinės architektūros, jei konkreti agento aplinka leidžia patogiai vykdyti projektą nuotoliniu būdu.

Remote desktop (RustDesk / AnyDesk ar panašus) laikomas tik fallback'u.

## Constraints

- Nenaudoti Git workflow kaip būtinos projekto dalies.
- Vietoj to naudoti manual checkpoint / backup / changed-file audit / manual revert.
- Nekeisti esamos projekto architektūros be priežasties.
- Neįdiegti nereikalingų SaaS servisų vien dėl demonstracijos.
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
- production deployment vien dėl pirmo video.

Pirmas tikslas yra **patikimas demonstracinis remote coding loop**.

## Verification checklist

Prieš laikant setup'ą paruoštu:

- [ ] Repo / projektas identifikuotas.
- [ ] Working directory aiški.
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
- start command:
- health check:
- existing agent capabilities:
- blockers:

### Recommended setup
- pasirinkta architektūra:
- kodėl:
- reikalingi pakeitimai:

### Files to change
- `path` — reason

### Safety / recovery
- checkpoint:
- backup:
- manual revert:

### Verification
- commands:
- browser checks:
- expected result:

### YouTube demo
- ką operatorius pasako telefonu:
- ką agentas daro:
- ką žiūrovas mato:
- final reveal:

### STOP
Po audito ir plano **nestartuok didelio build'o automatiškai**, jei yra architektūrinis neaiškumas. Pirmiausia aiškiai parodyk planą ir rizikas.
