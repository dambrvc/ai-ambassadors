---
name: nova-brand
description: Vizuální brand pravidla TV Nova (barvy, font Organica, logo, „loop" prvek a jejich použití na webu). Použij vždy při tvorbě nebo úpravě jakékoli webovky / landing page / týmové stránky, aby výsledek byl on-brand. Slouží jako podklad pro style.css.
---

# Nova Brand

Vizuální pravidla pro web s přehledem týmu. Vychází z logo manuálu Nova (2024).
Slouží jako podklad pro `style.css` — barvy, font, prvky a jejich použití.

## Font

**Organica** — jediný firemní font, použij ho na všechny texty (jména, role,
nadpisy, ovládací prvky).

- Font není systémový ani Google font — nahraj ho přes `@font-face` z vlastních
  souborů ve složce `assets/Organica 2/` (řezy Thin → Bold + kurzívy, `.otf`).
  Pozn.: `.otf` v prohlížeči funguje; pro rychlejší web je ideál převést na `.woff2`.
- Fallback v `font-family`: `"Organica", "Helvetica Neue", Arial, sans-serif`.

  ```css
  @font-face {
    font-family: "Organica";
    src: url("assets/Organica 2/Organica Regular.otf") format("opentype");
    font-weight: 400;
  }
  @font-face {
    font-family: "Organica";
    src: url("assets/Organica 2/Organica Bold.otf") format("opentype");
    font-weight: 700;
  }
  ```
- Tón typografie: bezpatkové, geometrické, vzdušné. Nadpisy klidně výrazně větší
  a tučnější než běžný text.

## Barvy

Základní paleta:

| Název | HEX | Použití |
|---|---|---|
| Tmavě modrá (primární) | `#0D1767` | hlavní barva, pozadí, texty na světlém |
| Červená (akcent) | `#F03B3B` | zvýraznění, hover, aktivní stavy, akcenty |
| Světle šedá | `#E3E3E3` | světlé plochy, karty, oddělovače |
| Tyrkysová | `#50C8DF` | doplňkový akcent (používat střídmě) |
| Černá | `#000000` | text, tmavé pozadí |
| Bílá | `#FFFFFF` | text na tmavém, plochy |

Doporučení pro web: tmavě modrá `#0D1767` jako hlavní/pozadí, červená `#F03B3B`
jako akcent (hover na kartách, aktivní filtr, odkazy). Tyrkysovou drž jako
výjimečný doplněk, ať paleta nezačne být pestrá.

## Barevné gradienty

Z manuálu (1.4). Hodí se na pozadí sekcí, hlavičku nebo „loop" prvek.

- **Modrý:** `#0A134D` → `#0D1767` → `#143DD5`
- **Červený:** `#CF121D` → `#F03B3B` → `#EE6255`
- **Červený (jemný přechod):** `#FF7F6B` → `#FD4944` → `#F03B3B` → `#EB3437` → `#DF222D` → `#D00B21`
- **Tyrkysový:** `#7EE2EA` → `#50C8DF` → `#57A7D7`
- **Šedý:** `#F2F2F2` → `#E3E3E3` → `#C5D0FC`

Příklad (CSS):

```css
background: linear-gradient(135deg, #0A134D, #0D1767, #143DD5);
```

## Logo a symbol

- Logo je slovní značka **„nova"**, kde písmeno „o" tvoří symbol „loop"
  (dvojitý kruh).
- Existuje i samostatný **symbol** (jen „loop") — vhodný jako favicon nebo malá
  ikona v patičce.
- **Používej oficiální soubory loga** z brand manuálu (vektor SVG/PNG) — logo
  nepřekresluj a needituj. Na webu ho umísti do hlavičky a/nebo patičky.
- Vyber správnou barevnou verzi podle podkladu (soubory jsou v `assets/`):

  | Soubor | Podklad | Kdy použít |
  |---|---|---|
  | `assets/nova-logo-navy.png` | světlý (bílá / `#E3E3E3`) | logo v tmavě modré |
  | `assets/nova-logo-white-red.png` | modrý / tmavý (`#0D1767`) | bílo-červená verze |
  | `assets/nova-logo-white.png` | černý / velmi tmavý | monochromatická bílá |

- Symbol samotného „loopu" se hodí jako favicon nebo malá ikona v patičce.

> Poznámka: reálné soubory loga a fontu Organica vlož do složky `assets/`
> (názvy viz `assets/README.txt`). Bez nich `@font-face` a vložení loga
> nebudou fungovat.

## Grafický prvek „Loop"

Charakteristický prvek značky: **dva překrývající se kroužky různé velikosti**
(větší nahoře, menší posunutý dolů a doleva) s **tenkou linkou** a **lineárním
gradientem** červená ↔ tmavě modrá. NENÍ to dva soustředné kruhy. Na webu se
hodí jako dekorace v hlavičce, na pozadí nebo jako jemný akcent.

- Hotové assety: `assets/nova-loop-blue.svg` (gradient navy→červená, na světlé
  a tmavé pozadí) a `assets/nova-loop-red.svg` (gradient červená→navy).
- Gradient jde svisle z `#F03B3B` do `#0D1767` (u modré verze opačně).
- Základní barevné verze: **červená** a **modrá**.
- Pro „brand in brand" prezentace existuje varianta s bílou
  (červená+bílá, modrá+bílá).
- **Důležité:** intenzita méně výrazné barvy se přizpůsobuje podkladu tak, aby
  loop na pozadí úplně nezmizel. Tzn. na tmavém pozadí drž loop dostatečně
  kontrastní.
- Loop drž decentní — je to akcent, ne dominanta. Ať nepřebije fotky týmu.

## Aplikace na web s týmem (doporučení)

- **Pozadí:** tmavě modré (`#0D1767`) nebo modrý gradient; loop jako jemná
  dekorace v rohu hlavičky.
- **Karty lidí:** světlý podklad (`#E3E3E3` / bílá) pro dobrou čitelnost fotek
  a jmen, nebo tmavé karty s bílým textem — drž jednotně.
- **Hover na kartě:** zvýraznění červenou `#F03B3B` (rámeček, podtržení jména
  nebo jemný posun/stín).
- **Aktivní filtr (oddělení):** vybrané tlačítko červené `#F03B3B`, neaktivní
  neutrální (šedá/modrá).
- **Odkazy (e-mail):** červená `#F03B3B`.
- **Texty:** jména a nadpisy v Organice, tučně; role/oddělení lehčí a menší.

## Co nedělat

- Neměnit barvy loga ani loop prvku mimo schválené varianty.
- Nepřekreslovat logo — vždy použít oficiální soubory.
- Nepřehánět to s tyrkysovou ani s počtem gradientů na jedné stránce.
- Nenechat loop „splynout" s pozadím (hlídat kontrast).
