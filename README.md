Super, tady je návrh README.md pro repozitář Celovecerni-aktivity:
markdown
# 🎉 Celovečerní aktivity
Tato složka obsahuje šablonu a jednotlivé akce s celovečerními soutěžemi.

---

## Jak vytvořit novou akci

### 1. Zkopíruj šablonu
Zkopíruj obsah `akce/template-akce/` do nové složky v:
akce/
Například:
akce/vanocni-vecirek/

tj. add file → create new file a do názvu vlož: `akce/vanocni-vecirek/index.html`
(GitHub podle lomítek sám vytvoří potřebné složky)

Zkopíruj z `template-akce`:
- `index.html`
- `style.css`

### 2. Uprav index.html
- Změň `<title>` a `<h1>` podle názvu akce
- U každé karty uprav text (název soutěže) a odkaz:
```html
  <div class="card" onclick="window.open('SKUTEČNÝ_ODKAZ', '_blank')">
      🪞<br> Název soutěže
  </div>
```
- Karet může být víc nebo míň než 3, stačí přidat/ubrat celé `<div class="card">...</div>` bloky

### 3. Uprav style.css
- **Pozadí** – vlož odkaz na obrázek:
```css
  background-image: url("https://tvuj-obrazek.png");
```
  (obrázky nahrávám přes ibb.co, stejně jako doteď)
- **Barvy karet** – uprav podle tématu akce:
```css
  .card {
      border: 1px solid rgba(255, 215, 120, 0.25); /* barva obrysu */
  }
  .card:hover {
      background: linear-gradient(135deg, ..., ...); /* barvy při najetí myší */
  }
```

### 4. Config – nastav aktivní akci
V kořenovém souboru `config.js` změň:
```javascript
const ACTIVE_EVENT = "vanocni-vecirek";
```
a přidej název nové akce do seznamu komentářů pod tím, ať máš přehled:
```javascript
// Dostupné akce:
// template-akce
// lockhart
// ples-letniho-slunovratu
// vanocni-vecirek
```

### 5. Hotovo 🎉
- Kořenová adresa webu (`.../Celovecerni-aktivity/`) automaticky přesměruje na akci nastavenou v `config.js`
- Konkrétní akci lze otevřít i přímo přes její vlastní adresu, např.:
.../Celovecerni-aktivity/akce/vanocni-vecirek/
- Rádio spustím tak, že jdu do Settings → Pages → Visit site

---

## ⚠️ Cache-busting

`config.js` se v kořenovém `index.html` načítá s automatickým "razítkem" (`?t=Date.now()`), takže **není potřeba ručně nic zvyšovat** – změna v `config.js` se vždy projeví hned po refreshi.

Pokud by ses přesto setkala se starou verzí stránky, zkus:
- Tvrdý refresh: `Cmd/Ctrl + Shift + R`
- Otevřít stránku v anonymním okně

---

## ✅ Checklist po vytvoření nové akce

- [ ] Zkopírovat `akce/template-akce/` do nové složky
- [ ] Upravit `index.html` (title, h1, karty, odkazy)
- [ ] Upravit `style.css` (pozadí, barvy karet)
- [ ] Aktualizovat `ACTIVE_EVENT` v `config.js`
- [ ] Přidat název akce do seznamu komentářů v `config.js`
- [ ] Commit + push
- [ ] Počkat na zelenou fajfku v Actions
- [ ] Otestovat v anonymním okně
