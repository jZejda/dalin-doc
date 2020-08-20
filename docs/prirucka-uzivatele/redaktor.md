---
sidebarDepth: 2
---

# Správa obsahu

[[TOC]]

---

::: warning ROLE REDAKTOR
Komponenty níže může primárně ovládat uživatel, který má od správce přidělenu roli REDAKTOR. 
:::

## Novinka

Novinka nese časově ohraničenou informaci. Novinka se zobrazí na úvodní stránce veřejné části, 
pokude se jedná o interní novinku, tato se zobrazí na titulní stránce klientské části.
Novinka by měla být vizuálně i obsahově zajímavá :dart: aby si jí uživatelé chtěli přečíst :-).

### Možnosti novinky
- **Nadpis** 
- **Úvodník** (krátkou informaci, která se zobrazí na titulní stránce max 220 znaků) Nevkládejte html znaky, prozatím to nic neudělá.
- Obsah (není povinný, rozšiřuje úvodník)
- URL obrázku - nejlépe nalinkovat nějakou zmenšeninu ve tvaru `media/2019/05/thubnails/obrazek.jpg`
- Zdali je novinka interní (novinka se zobrazí přihlášeným uživatelům)

### Komentáře
**Plán** Umožnit komentovat novinky nepřihlášenému návštěvníkovi stránky.

## Stránka

Sekce stránek umožní, vytvářet klasické stránky. Stránku chápej jako časově neomezenou infomraci. 
Stránce je možné přidávat různé stavy (rozpracováno, veřejné ...), dále je možné stránku zařadit do Kategorie a sdružovat stránky stejné kategorie.
Například se hodí u stránek závodů. Vytvořím jednu kategorii sdružující informace k závodu.

U takto označených stránek je pak možné zobrazit postranní menu ostatních stránek stejné kategorie. Pořadí menu je možné ovlivnit hodnotou výhy stránky.

::: tip
Správu [kategorií](#kategorie) najdeš níže.
:::

### Možnosti stránky
- **Nadpis**
- **Obsah** (hlavní část stránky v html)
- **Stav** ()
- Kategorie (vždy možné zařadit do jedné z kategorií)
- Zobrazení postranního menu (bude zobrazovat ostatní stránky stejné kategorie)
- Váha (pořadí stránky v postranním menu)
- Uživatel (uživatel který obsah vytvořil)

## Kategorie

Kategorie zařadí stránku do konkrétního oddělení. Výchozí kategorie je **Nezařazeno**. V této části můžeš vytvořit libovonou 
kategorii, přidát jí název, krátký popis a odkaz.

Po vytvoření kategorie, můžeš tuto přiřadit stránce a spojit více stránk obsahově do jednoho oddílu.

**Pokud stránky zařadíš do kategorií, můžeš:**

- Zobrazit stránky stejné kategorie s odkazy na stránky další stejné kategorie
- Zobrazit seznam stránke jedné kategorie

## Mediální soubory

Jednoduchý nástroj pro nahrání souboru na server. Soubory se automaticky nachrávají do adresářové strukuty `./rok/mesíc/`,
například `./2019/04/soubor`.

Názvy souborů jsou před nahráním očistěny od nedovolených znaků, diakkritiky apod. Na nahrané soubory je možné se následně
ze stránek odkazovat. Obrázky pro náhled, textové sobory ke stažení a pod.

Velikost uploadu obrázku je nastavena na 5 MB, jelikož je automaticky zmenšen na **1200 x poměr**, plus je vytvořena **zmenšenina** v adresáři `,/thubnails/` stejného obráku. Pokud jí nepotřebuješ, klidně smaž.
