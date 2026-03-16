# Dashboard v&nbsp;Looker&nbsp;Studio

---

# Co dnes vytvoříme?

<div style="display: flex; gap: 40px;">

<div style="flex: 1;">

- Naučíme se základy Looker Studia.
- Připojíme si náš CSV soubor se školskými daty.
- Vytvoříme dynamické filtry (Kraj, ORP, Typ školy).
- Zobrazíme klíčové metriky (počty škol, cizinců a uprchlíků).
- Analyzujeme věk, ročníky a regionální rozložení.

</div>

<div style="flex: 1;">

![dashboard](./assets/img/dashboard.png)

</div>

</div>
---

# Co je to Looker Studio?
- Bezplatný nástroj od Googlu pro vizualizaci dat.
- Umožňuje přeměnit surová data (Excel, CSV) na interaktivní reporty.
- **Výhoda:** Vše se děje v prohlížeči, reporty můžete snadno sdílet.

---

# Připojení dat
1. Přejděte na [lookerstudio.google.com](https://lookerstudio.google.com).
2. Klikněte na **Vytvořit** -> **Přehled** (Report).
3. Jako zdroj dat vyberte **Nahrání souboru** (File Upload).
4. Nahrajte náš soubor [zs.data.sample.xlsx](./assets/data/zs.data.sample.xlsx).
5. Přidejte nové počítané pole (**rok narození** z `DatNaroz`). 
6. Přidejte nové počítané pole (**kraj** z **KrajBudova**  a překódujeme `Hlavní město Praha` na `Prague`)
7. Klikněte na **Přidat do přehledu**.

---

# Seznámení s daty
Základní sloupce, se kterými budeme pracovat:
- `RedIzo` / `izo`: Identifikátory škol
- `rocnik`: Ročník žáka
- `urcena`: Zda je škola určená (1) nebo ne (0)
- **Skupiny žáků:** 
    - `CZESum` (Češi), 
    - `CIZSum` (Ostatní cizinci)
    - `Usum` (Uprchlíci z UA s dočasnou ochranou)

---

# Dynamické filtry
Aby si uživatel mohl data "proklikat", přidáme filtry.
1. V horním menu klikněte na **Přidat ovládací prvek** -> **Rozbalovací seznam**.
2. V pravém panelu nastavte **Pole ovládacího prvku** na:
   - `Kraj` (Kraj)
   - `Rok Narození`
   - `Urcena` (Typ školy: určená/neurčená)

*Tip: Filtry nyní budou ovlivňovat všechny grafy, které přidáme.*

---

# Základní ukazatele
Kolik máme celkem škol a žáků?
1. Klikněte na **Přidat graf** -> **Souhrn** (Scorecard).
2. **Počet škol:** V pravém panelu dejte jako metriku `RedIzo` a zvolte agregaci *Počet unikátních* (Count Distinct).
3. **Počet žáků:** Přidejte další kartu a jako metriku vložte `Usum` pro uprchlíky, nebo `CIZALLSum` pro všechny cizince.
4. Přidejte filter **rok narození** a 

---

# Regionální rozložení
Kde se nacházejí určené školy a žáci?
1. **Přidat graf** -> **Kombinovaná mapa** (nebo Geografická mapa, pokud máte čisté názvy obcí).
2. **Dimenze:** `Kraj`.
3. **Metriky:** 
    - `RedIzo` (Počet unikátních = Počet škol).
    - `CIZALL` (Celkem žáků cizinců)
4. **Filtrování:** Na graf aplikujte vpravo dole filtr: `urcena` = 1.
*Vidíme tak, kolik určených škol je v jednotlivých okresech/ORP.*

---

# Složení žáků
Jaké je složení žáků podle původu?
1. **Přidat graf** -> **Skládaný sloupcový graf**.
2. **Dimenze:** `KrajBudova` nebo `ORPBudova`.
3. **Metriky (přidejte všechny tři):** `CZESum`, `CIZSum`, `Usum`.
*Výsledek: Názorný pohled na to, jaký podíl v regionech tvoří Češi, běžní cizinci a žáci s dočasnou ochranou.*

---

# Analýza Věk vs. Ročník
Jsou cizinci umisťováni do nižších ročníků v porovnání s věkem?
1. **Přidat graf** -> **Kontingenční tabulka** s podmíněným formátováním.
2. **Řádek/Dimenze X:** `DatNaroz` (Rok narození / věk).
3. **Sloupec/Dimenze Y:** `rocnik`.
4. **Metrika:** `Usum` nebo `CIZALLSum`.
*Z grafu snadno vyčteme "shluky" – např. 15letí žáci umístění v 7. ročníku.*

---

# Žáci v 9. třídách
Jak jsou na tom cizinci před přechodem na SŠ?
1. **Přidat graf** -> **Prstencový graf**.
2. **Dimenze:** `KrajBudova`.
3. **Metrika:** `CIZALLSum` (celkem cizinců).
4. **Filtr tabulky:** Nastavte pravidlo `rocnik` = "9. ročník" (případně odpovídající kód z číselníku RARO).
*Přehledně ukáže, ve kterých regionech bude potřeba řešit kapacitu a jazykovou podporu pro SŠ.*

---

# Co nás čeká příště?
**Vývoj počtu žáků v čase!**
- Připravíme si časové řady (Time series).
- Ukážeme si, jak roste/klesá počet `CIZ` a `CZE` napříč kraji a ORP.
- Naučíme se kombinovat data z různých pololetí.

---

# Děkuji za pozornost!
Zkuste si nyní proklikat filtry a prozkoumat data z vašeho regionu.