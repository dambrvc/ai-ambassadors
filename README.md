# Týmová stránka „Lidé za naší prací"

Jednostránkový web o týmu, postavený v rámci programu AI Ambasadors (TV Nova).
On-brand statická stránka: hero, představení lidí s filtrem a hledáním, galerie ze zákulisí, kontakt.

## Pro koho to je

Pro lidi, kteří o týmu potřebují rychle zjistit, kdo v něm je, co dělá a jak se s ním spojit.
Interní použití, není to marketingový web.

## Jak to rozjet

Stránka je statická, není potřeba žádná instalace, žádný build a žádný server.

**Kde projekt vezmeš.** Projekt zatím není nikde nasazený ani ve verzovacím systému. Předává se
jako **celá složka zabalená do zipu, poslaná přes Teams**, a v tom zipu je všechno potřebné.
Napiš si o něj na kontakt na konci tohohle souboru. Od října 2026 bude projekt v Gitu na GitHubu
a tady bude odkaz na repozitář.

**Kroky:**

1. rozbal zip a nech složku pohromadě, nepřesouvej z ní jednotlivé soubory
2. dvakrát klikni na `index.html`
3. hotovo, stránka se otevře v prohlížeči

**Ověřeno v Chromu**, verze ze září 2026, na macOS. V jiných prohlížečích by fungovat měla,
ale nebylo to zkoušené.

**K podsložce `nova-brand`:** **je součástí toho zipu**, nikde se neobstarává zvlášť.
Jsou v ní fotky, logo a font Organica. To varování níž znamená jen tolik, že se nesmí při kopírování
zapomenout, protože bez ní se stránka otevře, ale bude bez obrázků a v systémovém fontu.

Na mém počítači stačil dvojklik, nic se neinstalovalo. Jedinou výjimkou je testování:
aby rozšíření Claude in Chrome na stránku otevřenou z disku vůbec vidělo, muselo se mu
v `chrome://extensions` u Claude v Podrobnostech zapnout **Povolit přístup k adresám URL souborů**.
Bez toho stránku nepřečte a hlásí, že na ni nemá přístup.

## Z čeho se to skládá

| Soubor | Co v něm je |
|---|---|
| `index.html` | celá stránka, obsah i JavaScript na konci v jednom `<script>` |
| `style.css` | veškerý vzhled, brandové barvy jako proměnné na začátku souboru |
| `nova-brand/assets/` | logo, font Organica, dekorativní loop prvky, fotky lidí a galerie |
| `testy.md` | testovací scénáře a výsledek posledního testovacího kola |
| `index-zaloha.html`, `style-zaloha.css` | záloha před úpravami z 2. setkání |

JavaScript na stránce dělá pět věcí: filtr oddělení u karet lidí, hledání v týmu,
zúžení hlavičky při scrollu, zvýrazňování aktivní položky v menu, a tlačítko zpět nahoru.

## Co je hotové

* hero sekce s brandovými prvky
* karty lidí, filtr podle oddělení, hledání ve jméně, roli i oddělení, hláška při nulovém výsledku
* galerie, devět dlaždic
* kontaktní patička
* tlačítko zpět nahoru, které se objeví po odscrollování o obrazovku

## Co hotové není

* **na stránce jsou zástupná data.** Jména typu Jana Nováková a e maily na `@firma.cz`
  je potřeba nahradit reálným týmem. **Fotky lidí i fotky v galerii jsou volně dostupné stock fotky
  z Unsplashe**, nejsou to fotky nikoho z týmu. Při nahrazení reálnými lidmi je nutné je vyměnit
  všechny, včetně náhledů v hero sekci
* **stránka nikde neběží.** Není nasazená, otevírá se jen jako soubor z disku
* galerie nemá zvětšování fotek, dlaždice nejsou klikací
* stránka je jen v češtině, jazyková mutace není

## Známé problémy

* hledání prohledává i roli, oddělení a e mail, nejen jméno. Chová se to konzistentně,
  ale nebylo to výslovně zadané, takže to někomu může přijít jako nechtěné
* aby stránku otevřenou z disku uvidělo rozšíření Claude in Chrome, musí se mu v `chrome://extensions`
  povolit přístup k adresám URL souborů

**Vědomé kompromisy, ať je nikdo neopravuje jako chyby:**

* **Duotone efekt na fotkách lidí je záměr**, plyne z brandových pravidel Nova. Není to nedoladěný filtr.
* **Zástupná jména a e maily jsou schválně.** Stránka slouží jako ukázka pro program AI Ambasadors,
  reálná data se doplní až při skutečném použití v týmu.
* **Kruhy v hero sekci jsou dekorativní brandový prvek**, ne obsah. Můžou se odstranit,
  ale stránka pak ztratí brandový podpis.
* **Jazykový přepínač jsme zkoušeli a odložili.** Šel by udělat přes slovníček v JS a atributy
  `data-i18n`, ale je to práce na dvacet minut a na setkání se nevešla. Cesta s překlady
  v JSON souborech a `fetch` nefunguje, protože stránka se otevírá jako soubor z disku
  a prohlížeč to zablokuje kvůli CORS. Kdo to bude dělat, ať jde přes ten slovníček v JS.

## Jak to otestovat

Scénáře a výsledek posledního kola jsou v `testy.md`. Testuje se v panelu rozšíření
Claude in Chrome, výstup se pak přenese do dokumentace ručně.

Minimum před každou další změnou: tři scénáře z `testy.md` plus pohled na stránku na mobilu.

## Co dělat dál

* nahradit zástupná data reálnými lidmi a fotkami
* nasadit stránku, aby měla veřejnou adresu (plánováno na říjnové setkání, přes Git a GitHub Pages)
* přidat zvětšování fotek v galerii, na to na setkání nebyl čas

**Kdybych měla čas, udělala bych v tomhle pořadí:**

1. nasadit stránku, aby měla veřejnou adresu. Odblokuje to i pohodlnější testování,
   protože na adresu http se dostane i Cowork, ne jen rozšíření
2. nahradit zástupná data reálným týmem, včetně fotek
3. zvětšování fotek v galerii, protože to je věc, kterou lidé u galerie čekají

## Autor a kontakt

Michaela Černochová, michaela.cernochova@nova.cz
Vzniklo v programu AI Ambasadors, TV Nova. Stránku postavila 1. skupina na prvním setkání
a doplnila na druhém setkání „Profesionalizace vibecodingu".
