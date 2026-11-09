# Sobe Zlata Rosa – demo stran za sobe in apartmaje

**Demo / referenca.** Gostišče Sobe Zlata Rosa, cene in kontakti so izmišljeni. Stran je označena
z demo pasico, ima `noindex` (ne pojavi se v Googlu), obrazec za povpraševanje pa ne pošilja
(pokaže demo sporočilo).

Predstavitvena stran za oddajanje sob in apartmaja v Bohinju: sobe z opremo in cenami,
cenik po sezonah, izleti v okolici in obrazec za povpraševanje (prihod, odhod, število oseb).
Zgradi jo preprost generator statičnih strani v Pythonu (nastal v okviru tečaja
[Build a Static Site Generator](https://www.boot.dev/courses/build-static-site-generator-python)
na Boot.dev).

Objavljena stran: https://milinkovicluka.github.io/sobe-zlata-rosa/

## Zahteve

- Python 3.10 ali novejši (brez dodatnih knjižnic)
- Bash (na Windows: Git Bash)

## Uporaba

```bash
./test.sh    # požene teste
./main.sh    # zgradi stran v public/ in jo postreže na http://localhost:8888
./build.sh   # produkcijska gradnja v docs/
```

Push na `main` sproži GitHub Actions: testi, gradnja in objava na GitHub Pages.

## Zgradba

| Pot | Vsebina |
| --- | --- |
| `content/` | strani: Domov, `sobe/`, `cenik/`, `okolica/`, `kontakt/` |
| `site.json` | ime, kontakt, meni **in vsa besedila vmesnika** (`ui_*`, `demo_note`) |
| `template.html` | glava, noga, spodnja vrstica za telefon, meta oznake |
| `static/index.css` | videz; barve in pisave v bloku `TEMA` na vrhu |
| `static/images/` | ilustracije (SVG) in slika za deljenje `deljenje.png` (1200 × 630) |
| `static/fonts/` | DM Serif Display in Work Sans (SIL OFL 1.1), lokalno |

## Gradniki

| Razred | Uporaba |
| --- | --- |
| `.hero` > `img` + `.hero-text` | naslovna slika z besedilom v okvirju |
| `.facts` > `.fact` | hitra dejstva pod naslovno sliko (`<strong>` številka, `<span>` opis) |
| `.eyebrow` | majhna oznaka nad naslovom razdelka |
| `.features` > `.feature` | tri prednosti v stolpcih |
| `.gallery` (`.two` = 2 stolpca) > `figure.card` | sobe in izleti; `ul.amenities` za opremo |
| `.price-table` > `.price-row` (`.head`) | cenik po sezonah |
| `.about`, `.cta`, `.lead` | slika + besedilo, temen poziv k dejanju, uvodni odstavek |
| `.btn`, `.btn-ghost`, `.btn-light`, `.btn-outline-light`, `.btn-whatsapp` | gumbi |
| `form.inquiry-form`, `.form-row`, `.contact-layout` | povpraševanje |

## Dva jezika (SLO / EN) – načrt

Besedila vmesnika (gumbi, meni, pasica) so že v `site.json`, ne v predlogi. Za angleško
različico bo dovolj: vsebina v `content/en/`, drugi nabor vrednosti `site.*` za angleščino
in preklopnik jezika v glavi. To zahteva manjšo razširitev generatorja (en `site.json` na jezik).

## Če iz demo strani nastane prava stran

- [ ] Odstrani demo pasico v `template.html` in `noindex` iz glave
- [ ] Pravi kontakti in naslov v `site.json`
- [ ] Obrazec: ključ Web3Forms, odstrani `data-demo` in demo skripto, dodaj soglasje in politiko zasebnosti
- [ ] Prave fotografije v WebP s `srcset` (sobe 800 × 600, naslovna 1200 × 700)
- [ ] Prave cene, sezone, turistična taksa in pogoji odpovedi
- [ ] Lastna domena
