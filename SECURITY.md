<!-- ============================================================
     SolXy · SECURITY.md
     Autors: QvarcY (https://github.com/QvarcY)
     Licence: MIT
     ============================================================ -->

# Drošības politika

Šis dokuments apraksta, kā ziņot par iespējamām drošības problēmām **SolXy** projektā un kādi drošības apsvērumi attiecas uz projektu.

SolXy ir statiska HTML un CSS vietne bez JavaScript, servera puses koda un datu bāzes. Tas būtiski samazina uzbrukuma virsmu, taču nenozīmē, ka projekts automātiski ir pasargāts no visiem tīmekļa drošības riskiem.

---

## Atbalstītās versijas

Kamēr projekts vēl tiek aktīvi izstrādāts un nav publicēta stabila versija, drošības labojumi tiek veikti aktuālajā `main` zarā.

Pēc stabilu relīžu publicēšanas šī sadaļa tiks papildināta ar konkrētu atbalsta politiku.

| Versija | Drošības atbalsts |
| --- | --- |
| `main` / aktuālā izstrādes versija | Jā |
| Novecojušas vai modificētas kopijas | Netiek garantēts |

---

## Drošības risku ziņošana

### Neziņo par ievainojamībām publiski

Ja atrodi iespējamu drošības ievainojamību, lūdzu, **nepublicē detalizētu ekspluatācijas aprakstu GitHub Issues, Discussions, sociālajos tīklos vai citā publiskā vietā**, kamēr problēma nav izvērtēta un novērsta.

Tas dod projekta uzturētājam iespēju pārbaudīt problēmu un sagatavot labojumu, pirms tehniskā informācija kļūst publiski izmantojama.

### Kā ziņot privāti

Kad SolXy publiskais GitHub repozitorijs būs pieejams un tajā būs iespējoti **GitHub Private Vulnerability Reporting / Security Advisories**, tas būs ieteicamais ziņošanas kanāls.

Plānotā repozitorija adrese:

```text
https://github.com/QvarcY/SolXy
```

Drošības sadaļa:

```text
https://github.com/QvarcY/SolXy/security
```

Ja privātā drošības ziņošana vēl nav pieejama, izmanto drošu kontaktkanālu, kas norādīts autora GitHub profilā:

```text
https://github.com/QvarcY
```

Publiskā issue neievieto paroles, piekļuves atslēgas, personas datus, ekspluatācijas kodu vai citu sensitīvu informāciju.

---

## Ko iekļaut ziņojumā

Lai problēmu varētu pārbaudīt pēc iespējas ātrāk, ziņojumā iekļauj:

- īsu ievainojamības aprakstu;
- skarto failu vai lapu;
- reproducēšanas soļus;
- iespējamo ietekmi;
- pārlūku un operētājsistēmu, ja tie ir būtiski;
- minimālu demonstrācijas piemēru, ja tas nepieciešams;
- ieteikto labojumu, ja tāds ir zināms.

Ja ziņojums satur sensitīvu informāciju, nesūti to publiskā issue.

---

## Reakcija uz ziņojumiem

Drošības ziņojumi tiks izskatīti pēc iespējas ātrāk.

Mērķis ir:

1. apstiprināt, ka ziņojums ir saņemts;
2. pārbaudīt, vai problēmu iespējams reproducēt;
3. novērtēt tās ietekmi;
4. sagatavot labojumu;
5. pēc nepieciešamības publicēt drošības paziņojumu vai relīzi.

Konkrēts reakcijas vai labošanas termiņš netiek garantēts, jo tas ir atkarīgs no problēmas sarežģītības un projekta uzturēšanas pieejamības.

---

## SolXy drošības modelis

SolXy arhitektūra pēc noklusējuma ir vienkārša:

- statiski HTML faili;
- statiski CSS faili;
- SVG resursi;
- nav JavaScript;
- nav servera puses lietojumprogrammas koda;
- nav datu bāzes;
- nav autentifikācijas;
- nav lietotāju kontu;
- nav projekta pārvaldītu sīkdatņu;
- nav lietotāja datu glabāšanas.

Šāda arhitektūra samazina daudzu tradicionālu tīmekļa lietojumprogrammu risku iespējamību, piemēram:

- SQL injekcijas;
- servera puses komandu injekcijas;
- autentifikācijas apiešanu;
- sesiju zādzību;
- servera API ievainojamības;
- JavaScript DOM manipulāciju izraisītas ievainojamības.

Tomēr statiska vietne joprojām var saturēt drošības un privātuma problēmas.

---

## Iespējamie riski

### 1. Ārējās saites

Ārēja saite var novest lietotāju uz nedrošu vai vēlāk kompromitētu vietni.

Ārējām saitēm, kas tiek atvērtas jaunā cilnē ar `target="_blank"`, jāizmanto:

```html
rel="noopener noreferrer"
```

Pirms jaunas ārējās saites pievienošanas pārbaudi tās domēnu un nepieciešamību.

---

### 2. Ārējie fonti un citi resursi

Ja fonts vai cits resurss tiek ielādēts no trešās puses servera, pārlūks izveido tīkla pieprasījumu šim pakalpojuma sniedzējam.

Tas var radīt:

- privātuma apsvērumus;
- pieejamības atkarību no ārēja servisa;
- piegādes ķēdes risku;
- CSP konfigurācijas sarežģījumus.

Ja SolXy izmanto Google Fonts, privātumam draudzīgāks variants ir fontus pašmitināt `assets/fonts/` direktorijā.

---

### 3. CSS `url()` un ārējie resursi

CSS var ielādēt ārējus resursus ar `url()`.

Pull Request pārskatīšanas laikā jāpārbauda jaunas vai mainītas atsauces uz:

```css
url(...)
```

Nepamatoti ārēji URL projektā nav pieļaujami.

---

### 4. SVG saturs

SVG ir aktīvāks formāts nekā parasts rastra attēls, tāpēc ārēji vai lietotāju iesniegti SVG faili jāpārskata pirms iekļaušanas projektā.

Pārbaudi, vai SVG nesatur:

- nevajadzīgas ārējo resursu atsauces;
- skriptus;
- event handlerus;
- svešu vai neskaidru iegultu saturu.

SolXy projekta SVG resursiem jābūt vienkāršiem un pārskatāmiem.

---

### 5. HTML injekcijas izmaiņās

Lai gan pašreizējais projekts neapstrādā lietotāju ievadi servera pusē, trešās puses ieguldījums var pievienot nevēlamu HTML.

Pull Request pārskatīšanā jāpievērš uzmanība:

- `<script>` elementiem;
- `javascript:` URL;
- inline event handleriem, piemēram, `onclick`;
- iframe elementiem;
- ārējiem resursiem;
- nevajadzīgiem formu endpointiem;
- sensitīvas informācijas pievienošanai repozitorijā.

---

### 6. Trešo pušu ieguldījumi

Pull Request saturs nav automātiski uzticams.

Pirms apvienošanas:

- pārskati diff;
- pārbaudi jaunus ārējos URL;
- pārbaudi SVG un HTML;
- pārbaudi GitHub Actions izmaiņas īpaši rūpīgi;
- nepieņem slepenus tokenus vai paroles repozitorijā;
- pārliecinies, ka projekts joprojām neizmanto JavaScript.

---

### 7. GitHub Actions

`.github/workflows/` saturs var izpildīt komandas GitHub infrastruktūrā, tāpēc workflow izmaiņas ir drošības ziņā nozīmīgas.

Pārskatot workflow izmaiņas:

- izmanto tikai nepieciešamās `permissions`;
- nepiešķir `write` tiesības, ja pietiek ar `read`;
- nepieļauj noslēpumu izdrukāšanu logā;
- izvairies no nepamatotām trešo pušu Actions;
- trešo pušu Actions vēlams piesaistīt konkrētai versijai vai commit SHA;
- uzmanīgi pārbaudi PR, kas maina `.github/workflows/`.

---

## Drošības galvenes hostinga vidē

Ja SolXy tiek mitināts serverī, drošības galvenes ir jāiestata hostinga vai reverse proxy līmenī.

Piemērs konservatīvai konfigurācijai, ja visi resursi tiek pašmitināti:

```text
Content-Security-Policy: default-src 'self'; img-src 'self' data:; style-src 'self'; font-src 'self'; object-src 'none'; base-uri 'self'; frame-ancestors 'none'
X-Content-Type-Options: nosniff
Referrer-Policy: strict-origin-when-cross-origin
Permissions-Policy: geolocation=(), microphone=(), camera=()
```

Ja tiek izmantoti Google Fonts vai citi ārēji resursi, `Content-Security-Policy` jāpielāgo tikai konkrēti nepieciešamajiem domēniem.

Piemēram:

```text
Content-Security-Policy: default-src 'self'; style-src 'self' https://fonts.googleapis.com; font-src 'self' https://fonts.gstatic.com; img-src 'self' data:; object-src 'none'; base-uri 'self'; frame-ancestors 'none'
```

Nevajadzētu pievienot plašus avotus, piemēram, `*`, tikai tāpēc, lai novērstu CSP kļūdas.

---

## HTTPS

Publiskā SolXy versija jāapkalpo tikai ar HTTPS.

HTTPS:

- aizsargā datu integritāti pārraides laikā;
- samazina satura pārtveršanas un modificēšanas risku;
- ir nepieciešams daudziem moderniem pārlūku drošības mehānismiem.

GitHub Pages publiskai vietnei HTTPS jābūt iespējotam.

---

## Slepenas vērtības

SolXy pašreizējai arhitektūrai nav nepieciešamas API atslēgas vai citi noslēpumi.

Repozitorijā nekad nedrīkst commitot:

- paroles;
- privātās atslēgas;
- API tokenus;
- GitHub Personal Access Token;
- `.env` failus ar sensitīvu saturu;
- autentifikācijas sīkdatnes;
- personas datus.

Ja noslēpums kļūdaini ir nonācis Git vēsturē, ar faila izdzēšanu jaunā commit nepietiek. Attiecīgais noslēpums jāatsauc vai jārotē.

---

## Atkarības

SolXy mērķis ir saglabāt minimālu ārējo atkarību skaitu.

Ja tiek piedāvāta jauna ārēja atkarība, Pull Request aprakstā jānorāda:

- kāpēc tā nepieciešama;
- kāds ir tās uzturētājs;
- kādu ārēju tīkla pieprasījumu tā pievieno;
- kā tā ietekmē privātumu;
- vai iespējams līdzvērtīgs lokāls risinājums.

---

## Privātums

SolXy pamatversijā nav paredzēta:

- analītika;
- reklāmu izsekošana;
- lietotāju konti;
- personas datu iesniegšana;
- projekta pārvaldītas sīkdatnes.

Ja kāda nākotnes izmaiņa ievieš šādu funkcionalitāti, pirms tās apvienošanas jāizvērtē gan drošības, gan privātuma sekas un jāatjaunina šī politika.

---

## Labākās prakses pašmitināšanai

Ja mitini SolXy savā serverī:

1. izmanto HTTPS;
2. iestati drošības galvenes;
3. mitini fontus lokāli, ja vēlies samazināt trešo pušu pieprasījumus;
4. regulāri pārskati izmantoto SolXy versiju;
5. neuzstādi nezināmas modificētas kopijas bez koda pārbaudes;
6. pārbaudi servera konfigurāciju neatkarīgi no SolXy koda;
7. neveido direktoriju listing, ja tas nav nepieciešams;
8. neglabā sensitīvus failus publiski pieejamajā dokumentu saknē.

---

## Kas netiek uzskatīts par drošības ievainojamību

Par drošības ievainojamību parasti netiek uzskatīti:

- vizuāli izkārtojuma defekti;
- responsīvā dizaina kļūdas bez drošības ietekmes;
- drukas kļūdas;
- pārlūku savietojamības atšķirības bez drošības ietekmes;
- informācija, kas jau paredzēta publiskai apskatei.

Šādos gadījumos izmanto parasto bug report veidni.

---

## Drošības atzinība

Ja ziņosi par derīgu drošības problēmu un vēlēsies tikt pieminēts, pēc problēmas novēršanas tavs GitHub lietotājvārds var tikt pievienots projekta pateicību sadaļai.

Publiska atzinība tiek veikta tikai ar ziņotāja piekrišanu.

---

## Kontakti

- **Autors:** [QvarcY](https://github.com/QvarcY)
- **Plānotais repozitorijs:** `https://github.com/QvarcY/SolXy`
- **Drošības sadaļa pēc repozitorija publicēšanas:** `https://github.com/QvarcY/SolXy/security`

---

<div align="center">

**© 2026 · QvarcY · MIT Licence**

**SolXy · Static by design**

</div>
