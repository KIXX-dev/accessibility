# A11y Boilerplate - Implementatie Gids

## 📋 Inhoudsopgave

1. [Over deze boilerplate](#over-deze-boilerplate)
2. [Snelstart](#snelstart)
3. [Theme configuratie](#theme-configuratie)
4. [WCAG & EAA compliance](#wcag--eaa-compliance)
5. [Tailwind integratie](#tailwind-integratie)
6. [Best practices](#best-practices)
7. [Testing checklist](#testing-checklist)

---

## Over deze boilerplate

Deze accessibility stylesheet is ontwikkeld om te voldoen aan:

- **European Accessibility Act (EAA)** - verplicht vanaf juni 2025
- **WCAG 2.1 Level AA** - de internationale standaard
- **EN 301 549** - Europese norm voor digitale toegankelijkheid

### Belangrijkste features

✅ **Focus management** - Duidelijke keyboard navigatie met `:focus-visible`  
✅ **Skip links** - Spring naar hoofdinhoud  
✅ **Reduced motion** - Respecteert gebruikersvoorkeuren  
✅ **High contrast** - Ondersteuning voor hoge contrast modus  
✅ **Touch targets** - Minimaal 44x44px voor mobiele gebruikers  
✅ **Form accessibility** - Verbeterde error states en validation  
✅ **Screen reader support** - Utility classes voor SR-only content  
✅ **Tailwind compatible** - Werkt naadloos met Tailwind CSS  

---

## Snelstart

### 1. Installatie

Voeg de stylesheet toe aan je HTML, **vóór** andere stylesheets:

```html
<!DOCTYPE html>
<html lang="nl">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  
  <!-- A11y Boilerplate - ALTIJD EERSTE LADEN -->
  <link rel="stylesheet" href="a11y-boilerplate.css">
  
  <!-- Daarna je andere stylesheets -->
  <link rel="stylesheet" href="tailwind.css">
  <link rel="stylesheet" href="custom.css">
</head>
```

### 2. Skip link toevoegen

Voeg direct na de opening `<body>` tag een skip link toe:

```html
<body>
  <!-- Skip link - VERPLICHT voor keyboard navigatie -->
  <a href="#main-content" class="skip-link">
    Spring naar hoofdinhoud
  </a>
  
  <header>...</header>
  
  <main id="main-content">
    <!-- Je hoofdcontent -->
  </main>
</body>
```

### 3. Klaar! 🎉

Je website heeft nu automatisch:
- Duidelijke focus indicators bij Tab navigatie
- Reduced motion ondersteuning
- High contrast mode ondersteuning
- Verbeterde touch targets op mobiel
- En meer...

---

## Theme configuratie

### Basis: Theme color aanpassen

Pas de primaire kleur aan in je CSS of inline in HTML:

```css
:root {
  --a11y-primary: #7c3aed;        /* Je brand kleur */
  --a11y-primary-dark: #6d28d9;   /* Donkere variant */
}
```

### Geavanceerd: Focus styling aanpassen

```css
:root {
  /* Focus indicator configuratie */
  --a11y-focus-width: 3px;      /* Dikte van focus ring */
  --a11y-focus-offset: 2px;     /* Afstand tot element */
  --a11y-focus-style: solid;    /* solid, dashed, dotted */
  
  /* Animatie snelheid */
  --a11y-transition-speed: 0.2s;
}
```

### Per project aanpassen

**Optie 1: In je hoofd stylesheet**
```css
/* main.css */
@import 'a11y-boilerplate.css';

:root {
  --a11y-primary: #ff6b6b;
}
```

**Optie 2: Inline in HTML**
```html
<style>
  :root {
    --a11y-primary: #4ecdc4;
    --a11y-primary-dark: #45b7aa;
  }
</style>
```

### Dark mode ondersteuning

De stylesheet past automatisch aan bij dark mode:

```css
@media (prefers-color-scheme: dark) {
  :root {
    --a11y-primary: #4d9fff;  /* Lightere kleur voor donkere achtergrond */
  }
}
```

---

## WCAG & EAA compliance

### Wat deze stylesheet dekt

| WCAG Criterium | Level | Status | Beschrijving |
|----------------|-------|--------|--------------|
| 1.4.3 Contrast | AA | ✅ | Focus states hebben voldoende contrast |
| 1.4.11 Non-text Contrast | AA | ✅ | UI componenten zijn herkenbaar |
| 1.4.12 Text Spacing | AA | ✅ | Tekst blijft leesbaar bij user overrides |
| 2.1.1 Keyboard | A | ✅ | Alle functionaliteit is keyboard accessible |
| 2.4.1 Bypass Blocks | A | ✅ | Skip link aanwezig |
| 2.4.7 Focus Visible | AA | ✅ | Focus is altijd duidelijk zichtbaar |
| 2.5.5 Target Size | AAA | ✅ | Touch targets minimaal 44x44px |
| 3.2.4 Consistent Identification | AA | ✅ | Consistente focus styling |
| 3.3.1 Error Identification | A | ✅ | Form errors zijn duidelijk |

### Wat je zelf nog moet doen

⚠️ Deze stylesheet dekt **visuele en interactie** toegankelijkheid. Je bent zelf verantwoordelijk voor:

1. **Semantische HTML** - Gebruik correcte HTML5 elementen
2. **Alt teksten** - Alle afbeeldingen moeten alt attributes hebben
3. **ARIA labels** - Waar nodig voor complexe componenten
4. **Heading structuur** - Logische h1, h2, h3 volgorde
5. **Kleurcontrast** - Minimaal 4.5:1 voor normale tekst
6. **Form labels** - Alle inputs moeten een label hebben
7. **Error messages** - Duidelijke en bruikbare foutmeldingen

---

## Tailwind integratie

### Hoe het werkt

De stylesheet is ontworpen om **niet** te conflicteren met Tailwind:

1. Gebruikt lage specificiteit waar mogelijk
2. Focus styles worden alleen toegepast als Tailwind's `ring-*` classes niet aanwezig zijn
3. Custom properties voor theming in plaats van hardcoded kleuren

### Tailwind ring utility behouden

Als je Tailwind's focus ring wilt gebruiken in plaats van onze focus styles:

```html
<!-- Deze button gebruikt Tailwind's ring -->
<button class="focus:ring-2 focus:ring-blue-500">
  Tailwind focus
</button>

<!-- Deze button gebruikt onze a11y focus -->
<button>
  Default a11y focus
</button>
```

### Best practice: Combineer beide

```html
<button class="bg-blue-500 text-white px-4 py-2 rounded
               focus:ring-2 focus:ring-blue-300">
  Button met Tailwind ring EN a11y fallback
</button>
```

### Tailwind plugin optie

Voor nog betere integratie kun je een Tailwind plugin maken:

```javascript
// tailwind.config.js
module.exports = {
  theme: {
    extend: {
      colors: {
        'a11y': 'var(--a11y-primary)',
      }
    }
  },
  plugins: [
    function({ addUtilities }) {
      addUtilities({
        '.focus-a11y': {
          'outline': '3px solid var(--a11y-primary)',
          'outline-offset': '2px',
        }
      })
    }
  ]
}
```

Dan in HTML:
```html
<button class="focus-a11y">Button met custom focus</button>
```

---

## Best practices

### 1. Skip links

**Altijd** een skip link toevoegen als eerste element in `<body>`:

```html
<body>
  <a href="#main-content" class="skip-link">
    Spring naar hoofdinhoud
  </a>
  
  <!-- Optioneel: Extra skip links -->
  <a href="#navigation" class="skip-link">
    Naar navigatie
  </a>
</body>
```

### 2. Focus management bij modals

Bij het openen van een modal/dialog:

```javascript
// Simpel voorbeeld
function openModal(modalId) {
  const modal = document.getElementById(modalId);
  const firstFocusable = modal.querySelector('button, [href], input, select, textarea, [tabindex]:not([tabindex="-1"])');
  
  modal.showModal(); // Of toon op andere manier
  firstFocusable?.focus();
}
```

### 3. Screen reader only content

Gebruik `.sr-only` voor content die alleen voor screen readers bedoeld is:

```html
<button>
  <svg>...</svg>
  <span class="sr-only">Sluiten</span>
</button>

<a href="/artikel">
  Lees meer
  <span class="sr-only">over ons nieuwe product</span>
</a>
```

### 4. Form accessibility

Zorg voor duidelijke labels en error messages:

```html
<div>
  <label for="email">
    E-mailadres
    <span class="text-red-600" aria-label="verplicht">*</span>
  </label>
  
  <input 
    type="email" 
    id="email"
    name="email"
    required
    aria-describedby="email-error"
    aria-invalid="true"
  >
  
  <p id="email-error" class="text-red-600" role="alert">
    Voer een geldig e-mailadres in
  </p>
</div>
```

### 5. Keyboard navigatie testen

Test **altijd** je website met alleen het toetsenbord:

1. Gebruik `Tab` om vooruit te navigeren
2. Gebruik `Shift + Tab` om terug te gaan
3. Gebruik `Enter` of `Space` om te activeren
4. Check of **alle** interactieve elementen bereikbaar zijn
5. Check of de focus volgorde logisch is

### 6. Touch targets op mobiel

Zorg dat klikbare elementen groot genoeg zijn:

```css
/* De stylesheet doet dit automatisch, maar als je override: */
@media (pointer: coarse) {
  .small-button {
    min-height: 44px;
    min-width: 44px;
    padding: 0.75rem; /* Extra padding helpt ook */
  }
}
```

---

## Testing checklist

### Handmatige tests

- [ ] **Tab navigatie** - Alle interactieve elementen zijn bereikbaar
- [ ] **Focus visibility** - Focus indicator is altijd duidelijk zichtbaar
- [ ] **Skip link** - Werkt en is zichtbaar bij focus
- [ ] **Form validation** - Error states zijn duidelijk
- [ ] **Keyboard only** - Alle functionaliteit werkt zonder muis
- [ ] **Mobile touch** - Alle knoppen zijn groot genoeg (min 44x44px)

### Browser tests

Test in minimaal:
- [ ] Chrome (desktop & mobile)
- [ ] Firefox (desktop)
- [ ] Safari (desktop & mobile)
- [ ] Edge (desktop)

### Screen reader tests

Test met minimaal één screen reader:
- [ ] **NVDA** (Windows, gratis)
- [ ] **JAWS** (Windows, betaald)
- [ ] **VoiceOver** (macOS/iOS, ingebouwd)
- [ ] **TalkBack** (Android, ingebouwd)

### Geautomatiseerde tools

Gebruik tools voor een snelle scan:
- [ ] **axe DevTools** - Browser extensie
- [ ] **WAVE** - Web accessibility evaluation tool
- [ ] **Lighthouse** - In Chrome DevTools (Accessibility audit)
- [ ] **Pa11y** - Command line tool

### Handmatige WCAG checks

Dingen die tools niet kunnen detecteren:
- [ ] Alt teksten zijn **beschrijvend** (niet alleen "afbeelding")
- [ ] Link teksten zijn **betekenisvol** (niet alleen "klik hier")
- [ ] Error messages zijn **duidelijk en actionable**
- [ ] Heading structuur is **logisch** (h1 → h2 → h3)
- [ ] Focus volgorde is **logisch**
- [ ] Kleurcontrast is **voldoende** (4.5:1 voor tekst)

---

## Veelgestelde vragen

### Moet ik nog andere accessibility libraries gebruiken?

Nee, deze stylesheet dekt de basis visuele en interactie toegankelijkheid. Voor complexe componenten (zoals carousels, accordions, tabs) heb je mogelijk wel JavaScript libraries nodig.

### Werkt dit met React/Vue/Angular?

Ja! Deze stylesheet is framework-agnostic. Zorg ervoor dat je:
1. De stylesheet laadt vóór je framework styles
2. Skip links implementeert in je root component
3. Focus management implementeert bij route changes

### Kan ik de focus styles uitschakelen?

**Nee, doe dit nooit!** Focus indicators zijn essentieel voor keyboard gebruikers. Als je ze niet mooi vindt, pas dan de styling aan via de CSS custom properties.

### Hoe test ik of mijn site compliant is?

1. Gebruik deze stylesheet ✅
2. Volg de [Testing checklist](#testing-checklist) hierboven
3. Test met echte gebruikers met beperkingen (als mogelijk)
4. Overweeg een professional accessibility audit

### Moet ik een toegankelijkheidsverklaring publiceren?

Ja! Voor Nederlandse websites is dit verplicht. Zie: https://www.toegankelijkheidsverklaring.nl/

---

## Resources

### Officiële documentatie
- [WCAG 2.1 Guidelines](https://www.w3.org/WAI/WCAG21/quickref/)
- [European Accessibility Act](https://ec.europa.eu/social/main.jsp?catId=1202)
- [EN 301 549](https://www.etsi.org/deliver/etsi_en/301500_301599/301549/03.02.01_60/en_301549v030201p.pdf)

### Nederlandse resources
- [Digitoegankelijk.nl](https://www.digitoegankelijk.nl/)
- [Toegankelijkheidsverklaring.nl](https://www.toegankelijkheidsverklaring.nl/)
- [Logius Accessibility](https://www.logius.nl/domeinen/toegankelijkheid)

### Testing tools
- [axe DevTools](https://www.deque.com/axe/devtools/)
- [WAVE](https://wave.webaim.org/)
- [Lighthouse](https://developer.chrome.com/docs/lighthouse/overview/)
- [Pa11y](https://pa11y.org/)

### Leren
- [WebAIM](https://webaim.org/)
- [A11y Project](https://www.a11yproject.com/)
- [MDN Accessibility](https://developer.mozilla.org/en-US/docs/Web/Accessibility)

---

## Ondersteuning

Heb je vragen of problemen? Check de volgende bronnen:

1. Lees de [Best practices](#best-practices) sectie
2. Test met de [Testing checklist](#testing-checklist)
3. Raadpleeg de [Resources](#resources)

---

## Licentie & Credits

Deze accessibility boilerplate is gebaseerd op:
- WCAG 2.1 Level AA requirements
- European Accessibility Act guidelines
- Modern CSS best practices
- Real-world testing met gebruikers

Vrij te gebruiken voor persoonlijke en commerciële projecten. Attributie wordt gewaardeerd maar is niet verplicht.

---

**Gemaakt met ❤️ voor een toegankelijker web**
