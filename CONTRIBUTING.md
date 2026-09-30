<!-- ============================================================
     SolXy · CONTRIBUTING.md
     Autors: QvarcY (https://github.com/QvarcY)
     Licence: MIT
     ============================================================ -->

# Kā piedalīties SolXy projektā

Paldies par interesi palīdzēt **SolXy** projektam.

Šis dokuments apraksta projekta darba principus, koda stilu, izmaiņu iesniegšanas kārtību un prasības jaunām lapām, dizaina elementiem un dokumentācijai.

SolXy ir veidots ar vienu būtisku ierobežojumu: **projekta kodā netiek izmantots JavaScript**. Interaktivitāte tiek realizēta ar semantisku HTML un CSS.

---

## Satura rādītājs

- [Kodekss](#kodekss)
- [Pirms sāc](#pirms-sāc)
- [Kā vari palīdzēt](#kā-vari-palīdzēt)
- [Projekta pamatprincipi](#projekta-pamatprincipi)
- [Koda stils](#koda-stils)
  - [HTML](#html)
  - [CSS](#css)
  - [Markdown](#markdown)
- [Kā pievienot jaunu planētas lapu](#kā-pievienot-jaunu-planētas-lapu)
- [Kā pievienot tēmu](#kā-pievienot-tēmu)
- [Piekļūstamība](#piekļūstamība)
- [Testēšana](#testēšana)
- [Git darba plūsma](#git-darba-plūsma)
- [Pull Request process](#pull-request-process)
- [Kļūdu ziņošana](#kļūdu-ziņošana)
- [Funkciju pieprasīšana](#funkciju-pieprasīšana)
- [Jautājumi](#jautājumi)

---

## Kodekss

Piedaloties projektā, jāievēro [`CODE_OF_CONDUCT.md`](CODE_OF_CONDUCT.md).

Pirms issue, diskusijas vai Pull Request izveides lūdzu iepazīsties ar projekta uzvedības kodeksu.

---

## Pirms sāc

Pirms veic izmaiņas:

1. Pārbaudi, vai līdzīgs issue vai Pull Request jau nepastāv.
2. Ja izmaiņas ir lielas, vispirms atver issue un apraksti ieceri.
3. Saglabā projekta pamatprincipus — HTML + CSS, bez JavaScript.
4. Neievies jaunas ārējās atkarības bez pamatota iemesla.
5. Pārliecinies, ka izmaiņas darbojas gan ar peli, gan tastatūru.
6. Pārbaudi izmaiņas vairākos ekrāna izmēros.

---

## Kā vari palīdzēt

### Kļūdu labošana

- Atrodi reproducējamu kļūdu.
- Pārbaudi, vai tā jau nav ziņota projekta Issues sadaļā.
- Ja nav, izveido jaunu issue, izmantojot `bug_report.md` veidni.
- Nelielu un acīmredzamu kļūdu vari labot arī tieši ar Pull Request.

### Jaunas funkcijas

- Mazas, skaidri izolētas funkcijas vari iesniegt kā Pull Request.
- Lielākām izmaiņām vispirms vēlams izveidot issue.
- Ja funkcija maina projekta arhitektūru vai pamatprincipus, pirms izstrādes nepieciešama apspriešana.

### Dokumentācija

Vari:

- labot drukas un gramatikas kļūdas;
- precizēt README vai CONTRIBUTING saturu;
- pievienot piemērus;
- uzlabot paskaidrojumus;
- papildināt tulkojumus;
- labot nederīgas vai novecojušas saites.

### Dizains

Vari palīdzēt ar:

- CSS efektiem;
- animācijām;
- responsīvo dizainu;
- tipogrāfiju;
- kontrastu;
- piekļūstamību;
- planētu un pavadoņu vizuālo noformējumu.

### Tulkošana

Ja tiek pievienota cita valoda:

- saglabā oriģinālā teksta nozīmi;
- nemaini tehniskos terminus bez nepieciešamības;
- pārbaudi visas iekšējās saites;
- izmanto skaidru faila nosaukumu, piemēram, `README.en.md`.

---

## Projekta pamatprincipi

Visām izmaiņām jāievēro šie noteikumi:

- **0 JavaScript** projekta kodā;
- semantisks HTML5;
- CSS Custom Properties;
- BEM nosaukumu konvencija;
- relatīvi failu ceļi;
- mobile-first pieeja;
- piekļūstama navigācija;
- redzami `:hover`, `:focus` un `:active` stāvokļi;
- `prefers-reduced-motion` atbalsts;
- saprātīgs kontrasts;
- bez CSS frameworkiem;
- bez build procesa;
- bez nevajadzīgām ārējām atkarībām.

Interaktivitātei izmanto HTML un CSS iespējas, piemēram:

- `<details>` un `<summary>`;
- radio pogas;
- checkbox elementus;
- `:target`;
- `:hover`;
- `:focus`;
- `:focus-visible`;
- `:checked`;
- CSS animācijas un pārejas.

---

## Koda stils

### HTML

Izmanto semantisku, skaidri strukturētu HTML.

```html
<!-- Pareizi -->
<section class="planet-card" aria-labelledby="mars-title">
  <h2 class="planet-card__title" id="mars-title">Marss</h2>
  <p class="planet-card__text">Sarkanā planēta</p>
</section>
```

Izvairies no nevajadzīgi vispārīgiem elementiem:

```html
<!-- Nepareizi -->
<div class="card">
  <div class="title">Marss</div>
  <div>Teksts</div>
</div>
```

HTML prasības:

- izmanto `<!doctype html>`;
- uz `<html>` norādi `lang="lv"`;
- pievieno `charset` un `viewport`;
- katrai lapai pievieno aprakstošu `meta description`;
- pievieno autora meta informāciju;
- lapas virsrakstam izmanto formātu `Lapas nosaukums · SolXy`;
- izmanto semantiskos elementus:
  - `<header>`;
  - `<nav>`;
  - `<main>`;
  - `<section>`;
  - `<article>`;
  - `<aside>`;
  - `<figure>`;
  - `<footer>`;
- pievieno skip link uz galveno saturu;
- ARIA atribūtus izmanto tur, kur semantiskais HTML viens pats nav pietiekams;
- attēliem un informatīvām SVG grafikām nodrošini pieejamu tekstu;
- nedrīkst pievienot `<script>` elementus vai JavaScript event handlerus.

Piemērs autora meta informācijai:

```html
<meta name="author" content="QvarcY">
<meta name="generator" content="SolXy · Pure HTML & CSS">
<link rel="author" href="https://github.com/QvarcY">
```

### CSS

Katram CSS failam jāsākas ar projekta galveni:

```css
/* ============================================================
   SolXy · faila-nosaukums.css
   Autors: QvarcY (https://github.com/QvarcY)
   Licence: MIT
   ============================================================ */
```

Sekcijas atdali ar skaidriem komentāriem:

```css
/* === PLANĒTU KARTĪTES === */
```

Izmanto projekta mainīgos:

```css
.planet-card {
  display: grid;
  gap: var(--space-md);
  padding: var(--space-lg);
  border: 1px solid var(--c-border);
  border-radius: var(--radius-lg);
  background: var(--c-bg-glass);
  backdrop-filter: blur(12px);
}

.planet-card__title {
  font-family: var(--font-display);
  font-size: clamp(1.5rem, 3vw, 2.5rem);
  color: var(--c-text-primary);
}

.planet-card--featured {
  border-color: var(--c-accent-teal);
}
```

Izvairies no nevajadzīgi hardkodētām vērtībām, ja tām jau ir dizaina sistēmas mainīgais:

```css
/* Nevēlami */
.card {
  padding: 20px;
  background: #0d1428;
}

.card .title {
  color: white;
}
```

CSS prasības:

- izmanto mainīgos no `css/variables.css`;
- ievēro BEM nosaukumu konvenciju;
- izmanto 2 atstarpes indentācijai;
- saglabā mobile-first pieeju;
- fluid tipogrāfijai izmanto `clamp()`, kur tas ir piemēroti;
- izvairies no pārmērīgi specifiskiem selektoriem;
- neizmanto inline stilus, ja stilu var ievietot atbilstošā CSS failā;
- neizmanto `!important`, izņemot retos, dokumentētos gadījumos, kur tam ir pamatots iemesls;
- animācijām jārespektē `prefers-reduced-motion`;
- jaunām krāsām jābūt saskaņotām ar dizaina sistēmu.

### Markdown

Markdown dokumentācijā:

- virsrakstiem izmanto `#`, `##`, `###`;
- sarakstiem izmanto `-`;
- komandām izmanto atbilstošus koda blokus;
- koda blokiem norādi valodu;
- failu nosaukumus un komandas raksti ar backticks;
- saitēm izmanto Markdown sintaksi;
- tabulām izmanto standarta Markdown tabulu sintaksi;
- neatstāj nepabeigtus koda blokus vai liekus backticks faila beigās.

---

## Kā pievienot jaunu planētas lapu

SolXy pamatā attēlo astoņas Saules sistēmas planētas. Šī sadaļa apraksta tehnisko procesu gadījumam, ja projekta paplašinājumā nepieciešama jauna tāda paša tipa lapa.

Piemērā izmantosim nosaukumu `planet-x`.

### 1. Izveido HTML lapu

Izveido:

```text
planets/planet-x.html
```

Par pamatu vari izmantot vienu no esošajām planētu lapām.

Pielāgo:

- `<title>`;
- `meta description`;
- virsrakstus;
- faktus un statistiku;
- iekšējās saites;
- CSS saites;
- piekļūstamības atribūtus.

### 2. Izveido planētas CSS failu

Izveido:

```text
css/planet-planet-x.css
```

Piemērs:

```css
/* ============================================================
   SolXy · planet-planet-x.css
   Autors: QvarcY (https://github.com/QvarcY)
   Licence: MIT
   ============================================================ */

/* === PLANET X MAINĪGIE === */

:root {
  --planet-x-color-primary: #c4a582;
  --planet-x-color-secondary: #8b7355;
  --planet-x-color-accent: #e8d5b7;
  --planet-x-color-glow: rgb(196 165 130 / 40%);
}

/* === PLANET X VIRSMA === */

.planet--planet-x {
  background:
    radial-gradient(
      circle at 30% 30%,
      var(--planet-x-color-accent),
      var(--planet-x-color-primary) 40%,
      var(--planet-x-color-secondary) 100%
    );
}
```

Ja mainīgie ir nepieciešami visā projektā, pārvieto tos uz `css/variables.css`.

### 3. Pievieno CSS saiti

Planētas HTML lapā pievieno atbilstošo CSS failu:

```html
<link rel="stylesheet" href="../css/planet-planet-x.css">
```

Ja stils nepieciešams arī sākumlapā, pievieno saiti ar pareizo relatīvo ceļu:

```html
<link rel="stylesheet" href="css/planet-planet-x.css">
```

### 4. Pievieno kartīti katalogam

Piemērs:

```html
<article class="planet-card planet-card--planet-x">
  <a href="planets/planet-x.html" class="planet-card__link">
    <div
      class="planet-card__preview planet-card__preview--planet-x"
      aria-hidden="true"
    ></div>

    <h3 class="planet-card__title">Planet X</h3>
    <p class="planet-card__text">Papildu debess ķermenis</p>
  </a>
</article>
```

### 5. Atjaunini navigāciju

Ja lapa kļūst par oficiālu projekta sadaļu, pārbaudi visas vietas, kur tiek uzskaitītas planētas vai saistītās lapas.

### 6. Atjaunini dokumentāciju

Ja izmaiņas maina projekta struktūru:

- atjaunini `README.md`;
- atjaunini `CHANGELOG.md`;
- vajadzības gadījumā papildini šo failu.

### 7. Pārbaudi rezultātu

Pirms Pull Request:

- lapa atveras bez kļūdām;
- relatīvie ceļi darbojas;
- CSS tiek ielādēts;
- nav JavaScript;
- fokusa stāvokļi ir redzami;
- saturs darbojas ar tastatūru;
- kontrasts ir pietiekams;
- animācijas respektē reduced-motion iestatījumu;
- HTML un CSS nav acīmredzamu validācijas kļūdu.

---

## Kā pievienot tēmu

Tēmas tiek definētas `css/themes.css`.

Ja nepieciešams jauns variants, izmanto projekta CSS mainīgos.

Piemērs:

```css
/* === NORD TĒMA === */

[data-theme="nord"] {
  --c-bg-primary: #2e3440;
  --c-bg-secondary: #3b4252;
  --c-text-primary: #eceff4;
  --c-accent-teal: #88c0d0;
  --c-accent-violet: #b48ead;
  --c-accent-pink: #bf616a;
}
```

Ja tēmas izvēlei tiek izmantots CSS-only pārslēgs, HTML var izmantot radio pogas:

```html
<input
  class="theme-switch__input"
  type="radio"
  name="theme"
  id="theme-nord"
  value="nord"
>

<label class="theme-switch__option" for="theme-nord">
  Nord
</label>
```

Pārbaudi:

- teksta kontrastu;
- fokusa stāvokļus;
- hover stāvokļus;
- izvēlētā stāvokļa vizuālo atšķirību;
- salasāmību gaišajā un tumšajā vidē.

---

## Piekļūstamība

Piekļūstamība nav papildu funkcija — tā ir daļa no projekta kvalitātes prasībām.

Pārbaudi:

- vai lapu iespējams lietot tikai ar tastatūru;
- vai fokusa secība ir loģiska;
- vai fokusa indikators ir skaidri redzams;
- vai semantiskais HTML korekti apraksta struktūru;
- vai pogām un saitēm ir saprotams nosaukums;
- vai dekoratīvie elementi netraucē ekrānlasītājiem;
- vai kustība tiek samazināta ar `prefers-reduced-motion`;
- vai tekstam ir pietiekams kontrasts;
- vai lapa saglabājas lietojama pie palielināta teksta izmēra;
- vai interaktīvie elementi nav atkarīgi tikai no krāsas.

---

## Testēšana

SolXy nav build procesa, tāpēc galvenā pārbaude notiek pārlūkā.

Pirms Pull Request pārbaudi vismaz:

1. `index.html`;
2. izmainītās lapas;
3. navigāciju;
4. iekšējās saites;
5. relatīvos resursu ceļus;
6. desktop izkārtojumu;
7. mobilā izmēra izkārtojumu;
8. tastatūras navigāciju;
9. `prefers-reduced-motion`, ja izmaiņas skar animācijas;
10. pārlūka konsoli, lai pārliecinātos, ka nav resursu ielādes kļūdu.

Ja izmaiņas skar HTML vai CSS struktūru, ieteicams izmantot arī W3C validatorus.

---

## Git darba plūsma

Kad publiskais repozitorijs ir pieejams, izveido savu fork un klonē to:

```bash
git clone https://github.com/TAVS-LIETOTAJVARDS/SolXy.git
cd SolXy
```

Pievieno oriģinālo repozitoriju kā `upstream`:

```bash
git remote add upstream https://github.com/QvarcY/SolXy.git
```

Pirms darba sākšanas atjaunini `main`:

```bash
git checkout main
git fetch upstream
git pull --ff-only upstream main
```

Izveido atsevišķu zaru:

```bash
git checkout -b feature/jauna-funkcija
```

Ieteicamie zaru prefiksi:

| Prefikss | Lietojums |
| --- | --- |
| `feature/` | Jauna funkcija |
| `fix/` | Kļūdas labojums |
| `docs/` | Dokumentācija |
| `style/` | Vizuālas/CSS izmaiņas |
| `refactor/` | Pārstrukturēšana bez funkcionalitātes maiņas |
| `chore/` | Uzturēšanas darbi |

---

## Pull Request process

### 1. Veic izmaiņas

Ievēro šajā dokumentā aprakstīto koda stilu un projekta pamatprincipus.

### 2. Pārbaudi statusu

```bash
git status
```

### 3. Pārbaudi diff

```bash
git diff
```

### 4. Pievieno nepieciešamos failus

```bash
git add .
```

### 5. Izveido commit

Projektā ieteicami īsi, saprotami commit ziņojumi angļu valodā.

Piemēri:

```bash
git commit -m "feat: add planet comparison card"
```

```bash
git commit -m "fix: improve mobile navigation focus"
```

```bash
git commit -m "docs: update contribution guide"
```

Commit ziņojumam vēlams būt:

- īsam;
- konkrētam;
- imperatīvam;
- bez punkta beigās;
- saistītam ar vienu loģisku izmaiņu kopu.

### 6. Push

```bash
git push origin feature/jauna-funkcija
```

### 7. Atver Pull Request

Pull Request aprakstā norādi:

- ko izmainīji;
- kāpēc izmaiņa nepieciešama;
- kā to pārbaudīji;
- saistīto issue, ja tāds ir;
- ekrānuzņēmumus, ja izmaiņas skar dizainu.

### 8. Reaģē uz atsauksmēm

Ja review laikā nepieciešamas izmaiņas, veic tās tajā pašā zarā un push vēlreiz.

Nav nepieciešams atvērt jaunu Pull Request katram labojumam.

---

## Kļūdu ziņošana

Kļūdas ziņojumā iekļauj:

- īsu un konkrētu virsrakstu;
- problēmas aprakstu;
- reproducēšanas soļus;
- gaidīto rezultātu;
- faktisko rezultātu;
- pārlūku un tā versiju;
- operētājsistēmu;
- ekrānuzņēmumu, ja tas palīdz;
- saiti uz konkrēto lapu vai failu, ja piemērojams.

Pirms jauna issue izveides pārbaudi, vai tāds jau nepastāv.

---

## Funkciju pieprasīšana

Funkcijas pieprasījumā apraksti:

- problēmu, kuru vēlies atrisināt;
- piedāvāto risinājumu;
- kā tas iederas SolXy mērķī;
- iespējamās alternatīvas;
- piekļūstamības ietekmi;
- vai risinājumu iespējams realizēt bez JavaScript.

Funkcija, kas obligāti prasa JavaScript, var nebūt piemērota šim projektam, jo **0 JavaScript** ir viens no SolXy pamatprincipiem.

---

## Jautājumi

Ja neesi pārliecināts par izmaiņu virzienu, labāk vispirms izveido issue vai diskusiju, nevis uzreiz veido lielu Pull Request.

---

<div align="center">

**Paldies, ka palīdzi SolXy projektam!**

[QvarcY](https://github.com/QvarcY)

© 2026 · QvarcY · MIT Licence

</div>
