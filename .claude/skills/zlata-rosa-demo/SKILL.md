---
name: zlata-rosa-demo
description: Ključni podatki za gradnjo in urejanje demo strani Sobe Zlata Rosa (oddajanje sob v Bohinju; statični generator v Pythonu, vsebina v Markdownu + HTML blokih, objava na GitHub Pages). Uporabi pred vsakim dodajanjem ali urejanjem strani, menija, cen, slik, obrazca, videza ali generatorja v tem projektu.
---

# Sobe Zlata Rosa (demo) – kako graditi ta projekt

**Demo stran izmišljenega gostišča.** Pasica (`site.demo_note`), `noindex` in obrazec brez
pošiljanja (`data-demo`) morajo ostati. Jezik: **slovenščina**, vikanje, topel ton.
Večina obiskovalcev je na **telefonu**: vsako spremembo preveri pri širini 320–390 px,
tudi da stran ne gre v širino (`document.documentElement.scrollWidth`).

## Zgradba

- `content/**/index.md`: `/`, `/sobe`, `/cenik`, `/okolica`, `/kontakt`. Vsaka ima `# naslov`
  in `<!-- opis: ... -->` (meta opis, do ~155 znakov).
- `site.json`: podatki **in besedila vmesnika** (`ui_menu`, `ui_quick`, `ui_call`, `ui_inquiry`,
  `ui_check_availability`, `demo_note`). Predloga nima trdo zapisanega besedila, da se doda angleščina.
- `{{ site.kljuc }}` deluje v predlogi in vsebini; neznan ključ ustavi gradnjo.
- HTML bloki: brez praznih vrstic znotraj bloka. Notranje povezave in slike z začetnim `/`.

## Videz

- Tema v `:root` (`static/index.css`): `--accent` #1d4e57 (jezero), `--pine` (noga, pasica),
  `--wood` (poudarki, oznake), `--radius` 4px. Pisavi DM Serif Display (naslovi) in Work Sans.
- Gumbi so pravokotni, VELIKE ČRKE. Na temni podlagi `.btn-light` / `.btn-outline-light`.
- Gradniki: glej tabelo v README.
- Mobile-first: `@media (min-width: 560px)` in `(min-width: 860px)`. V `.form-row` ostane
  `minmax(0, 1fr)`, sicer polja za datum na telefonu prelijejo stran.

## Slike

Ilustracije SVG iz skripte (ni v repozitoriju): naslovna 1200×700, hisa 600×700, sobe in izleti 800×600.
`deljenje.png` je zaslonska slika `deljenje.svg` pri 1200×630 (Playwright).

## Ukazi

- `./test.sh` (po vsaki spremembi v `src/`), `./main.sh` (lokalno na :8888), `./build.sh` (`docs/`).
- Push na `main` → GitHub Actions objavi na https://milinkovicluka.github.io/sobe-zlata-rosa/
