# Testovací scénáře k týmové stránce

Poslední spuštění: **1. 9. 2026**, přes rozšíření Claude in Chrome, na stránce otevřené z disku.
Prohlížeč: Chrome, okno vysoké 589 px.

## Scénáře

**1. Tlačítko nahoru**
Když jsem na začátku stránky, tlačítko nahoru není vidět. Když odscrolluju přesně o jednu obrazovku,
objeví se. Když na něj kliknu, stránka vyjede na začátek a tlačítko zmizí.
→ **prošel**

**2. Filtr oddělení společně s hledáním**
Když si vyfiltruju oddělení ML Tým a pak napíšu do hledání „jana", zůstane vidět jen Jana Nováková
a filtr dál platí.
→ **prošel**

**3. Prázdný stav a cesta zpátky**
Když nemám vybrané žádné oddělení a napíšu do hledání nesmysl, nezobrazí se nikdo a objeví se hláška
„Nikoho jsem nenašel". Když text smažu, vrátí se všech pět lidí a hláška zmizí.
→ **prošel**

**Konzole prohlížeče:** čistá, žádné červené chyby, ani po načtení, ani během průchodu.

## Co se při testování našlo a opravilo

**Tlačítko nahoru se objevovalo o jeden pixel později, než mělo.** V podmínce bylo
`scrollY > innerHeight` místo `>=`, takže při odscrollování přesně o jednu obrazovku bylo tlačítko
ještě skryté. Opraveno 1. 9. 2026 změnou `>` na `>=`.

Poznámka k tomu, ať to někoho nezmate: v prvním kole scénář 1 neprošel, ve druhém prošel.
Rozšíření k tomu nabídlo vysvětlení, že si kód pamatuje výšku okna z načtení stránky.
**To vysvětlení není pravdivé**, `window.innerHeight` se čte při každém scrollu. Skutečný důvod je,
že se mezi oběma koly opravil kód. Tester o té opravě nevěděl.

## Známé problémy, které zůstávají

* na stránce jsou pořád **zástupná data**, tedy jména typu Jana Nováková a e maily na `@firma.cz`
* stránka se otevírá **jako soubor z disku**, není nikde nasazená. Aby na ni vidělo rozšíření
  Claude in Chrome, musí se mu v `chrome://extensions` povolit přístup k adresám URL souborů
* hledání prohledává i roli, oddělení a e mail, nejen jméno. Chová se to konzistentně,
  ale nebylo to výslovně zadané

## Co otestovat, až se bude něco měnit

Tři scénáře výše plus tyhle, na které dnes nebyl čas:

* stránka na mobilu nepřetéká do strany a tlačítko nahoru nepřekrývá odkazy v patičce
* celá stránka se dá obsloužit klávesou Tab a je vždy vidět, co je vybrané
* fotky mají smysluplné alt texty
* odkazy v menu skáčou na správné sekce i při aktivním filtru a hledání
