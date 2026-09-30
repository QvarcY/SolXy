# SolXy

<div align="center">

**Interaktīva Saules sistēmas izpētes platforma, kas veidota tikai ar HTML un CSS.**

Bez JavaScript · Bez frameworkiem · Bez build rīkiem

[![License: MIT](https://img.shields.io/badge/License-MIT-a78bfa.svg)](LICENSE)
[![HTML5](https://img.shields.io/badge/HTML5-semantic-5eead4.svg)](#tehnoloģijas)
[![CSS3](https://img.shields.io/badge/CSS3-pure-5eead4.svg)](#tehnoloģijas)
[![JavaScript](https://img.shields.io/badge/JavaScript-0%20lines-f472b6.svg)](#tehnoloģijas)

</div>

---

## Par projektu

**SolXy** ir statiska Saules sistēmas izpētes vietne un CSS eksperiments. Projekta mērķis ir parādīt, cik daudz var izveidot ar semantisku HTML un modernu CSS bez JavaScript runtime, frameworkiem vai build procesa.

Publiskā projekta sākuma versija ietver:

- animētu Saules sistēmas skatu sākumlapā;
- astoņu planētu vizuālo sistēmu;
- kopīgu dizaina sistēmu un responsīvus izkārtojumus;
- zvaigžņu fonu, Sauli, orbītas un CSS animācijas;
- navigāciju uz ieplānotajām planētu, pavadoņu un datu sadaļām;
- pagaidu sadaļu lapas, kamēr detalizētais saturs tiek publicēts pakāpeniski;
- projekta dokumentāciju, MIT licenci un GitHub Pages konfigurāciju.

## Satura statuss

| Sadaļa | Day 0 statuss |
| --- | --- |
| Sākumlapa | Pieejama |
| Par projektu | Pieejama |
| 8 planētu maršruti | Sagatavoti, detalizētais saturs sekos |
| 6 pavadoņu maršruti | Sagatavoti, detalizētais saturs sekos |
| Datu sadaļas | Sagatavotas, detalizētais saturs sekos |

## Kā palaist

Projektam nav build soļa.

1. Klonē repozitoriju.
2. Atver `index.html` pārlūkā.

Vai palaid vienkāršu lokālu serveri:

```bash
python -m http.server 8000
```

un atver `http://localhost:8000`.

## Tehnoloģijas

- **HTML5** — semantisks marķējums;
- **CSS3** — Grid, Flexbox, Custom Properties, gradients, transitions un keyframe animācijas;
- **SVG** — logo, favicon un Open Graph vizuāļi;
- **Google Fonts** — Space Grotesk, Inter un JetBrains Mono;
- **GitHub Pages** — statiskās vietnes publicēšanai.

Projektā nav JavaScript, CSS frameworku vai runtime atkarību.

## Struktūra

```text
SolXy/
├── index.html
├── about.html
├── 404.html
├── planets/        # sagatavoti planētu maršruti
├── moons/          # sagatavoti pavadoņu maršruti
├── data/           # sagatavotas datu sadaļas
├── css/            # sākumlapas un kopīgā dizaina sistēma
├── assets/
└── .github/
```

## Attīstība

SolXy saturs tiek publicēts pa loģiskiem komponentiem. Nākamie papildinājumi paplašinās planētu, pavadoņu un datu sadaļas, saglabājot to pašu bez-JavaScript pieeju.

## Licence

MIT — skatīt [LICENSE](LICENSE).

---

<div align="center">

**QvarcY · SolXy**

</div>
