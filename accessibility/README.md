# Accessibility Boilerplate - European Standards 2025

Een battle-tested CSS boilerplate voor toegankelijke websites die voldoet aan de Europese toegankelijkheidseisen 2025 (European Accessibility Act + WCAG 2.1 Level AA).

## 🎯 Kenmerken

✅ **WCAG 2.1 Level AA compliant**  
✅ **European Accessibility Act ready**  
✅ **Tailwind CSS compatible**  
✅ **Focus-visible voor keyboard navigatie**  
✅ **Reduced motion ondersteuning**  
✅ **High contrast mode**  
✅ **Touch targets (44x44px minimum)**  
✅ **Skip links**  
✅ **Screen reader utilities**  
✅ **Aanpasbare theme colors**  

## 📦 Bestanden

- **`a11y-boilerplate.css`** - De hoofdstylesheet (gebruik dit in je projecten)
- **`a11y-demo.html`** - Interactieve demo pagina
- **`IMPLEMENTATIE.md`** - Uitgebreide implementatie gids

## 🚀 Snelstart

### 1. Voeg stylesheet toe

```html
<head>
  <!-- Laad VOOR andere stylesheets -->
  <link rel="stylesheet" href="a11y-boilerplate.css">
  <link rel="stylesheet" href="tailwind.css">
</head>
```

### 2. Voeg skip link toe

```html
<body>
  <a href="#main-content" class="skip-link">
    Spring naar hoofdinhoud
  </a>
  
  <main id="main-content">
    <!-- Je content -->
  </main>
</body>
```

### 3. Pas theme color aan (optioneel)

```css
:root {
  --a11y-primary: #7c3aed;  /* Je brand kleur */
}
```

## 🎨 Theme configuratie

Pas eenvoudig je brand colors aan via CSS custom properties:

```css
:root {
  /* Hoofdkleur */
  --a11y-primary: #0066cc;
  --a11y-primary-dark: #004d99;
  
  /* Focus styling */
  --a11y-focus-width: 3px;
  --a11y-focus-offset: 2px;
  --a11y-focus-style: solid;
  
  /* Animatie snelheid */
  --a11y-transition-speed: 0.2s;
}
```

## ✨ Belangrijkste features

### Focus management
- Gebruikt moderne `:focus-visible` - geen focus ring bij muisklik
- Duidelijke focus indicators voor keyboard navigatie
- Automatische aanpassing in high contrast mode

### Reduced motion
- Respecteert `prefers-reduced-motion`
- Schakelt automatisch animaties uit indien nodig

### Touch targets
- Automatisch minimaal 44x44px op touch devices
- Voldoet aan WCAG 2.5.5

### Form accessibility
- Duidelijke error states voor invalide velden
- Disabled states zijn visueel onderscheidbaar
- Focus states voor checkboxes en radio buttons

### Utility classes
- `.sr-only` / `.visually-hidden` - Voor screen readers only content
- `.skip-link` - Skip navigation link
- `.focus-within` - Style parent bij child focus

## 🧪 Demo bekijken

Open `a11y-demo.html` in je browser en:

1. Navigeer met **Tab** door de pagina
2. Let op de duidelijke focus indicators
3. Test formulier validatie
4. Bekijk verschillende interactieve states

## 📖 Uitgebreide documentatie

Zie `IMPLEMENTATIE.md` voor:

- Gedetailleerde implementatie instructies
- WCAG compliance overzicht
- Tailwind integratie tips
- Best practices
- Testing checklist
- Veelgestelde vragen
- Resources en tools

## 🎯 Wat deze stylesheet dekt

| Feature | Status | WCAG |
|---------|--------|------|
| Focus indicators | ✅ | 2.4.7 (AA) |
| Skip links | ✅ | 2.4.1 (A) |
| Reduced motion | ✅ | 2.3.3 (AAA) |
| High contrast | ✅ | 1.4.11 (AA) |
| Touch targets | ✅ | 2.5.5 (AAA) |
| Form errors | ✅ | 3.3.1 (A) |
| Keyboard access | ✅ | 2.1.1 (A) |
| Consistent ID | ✅ | 3.2.4 (AA) |

## ⚠️ Wat je zelf nog moet doen

Deze stylesheet dekt **visuele en interactie** toegankelijkheid. 

Je bent zelf verantwoordelijk voor:
- ✍️ Semantische HTML structuur
- 🖼️ Alt teksten voor afbeeldingen
- 🏷️ ARIA labels waar nodig
- 📋 Logische heading structuur (h1, h2, h3)
- 🎨 Kleurcontrast (min. 4.5:1)
- 📝 Form labels en error messages
- ♿ Screen reader testing

## 🔧 Compatibiliteit

### Browsers
✅ Chrome/Edge (desktop & mobile)  
✅ Firefox (desktop & mobile)  
✅ Safari (desktop & mobile)  
✅ Modern browsers met CSS custom properties support  

### Frameworks
✅ Tailwind CSS  
✅ Bootstrap  
✅ Vanilla CSS  
✅ React / Vue / Angular  
✅ Next.js / Nuxt.js  

## 🧪 Testing tools

Aanbevolen tools voor accessibility testing:

- **axe DevTools** - Browser extensie (gratis)
- **WAVE** - Web accessibility tool
- **Lighthouse** - Chrome DevTools audit
- **NVDA** - Screen reader (Windows, gratis)
- **VoiceOver** - Screen reader (macOS/iOS, ingebouwd)

## 📚 Resources

- [WCAG 2.1 Quick Reference](https://www.w3.org/WAI/WCAG21/quickref/)
- [European Accessibility Act](https://ec.europa.eu/social/main.jsp?catId=1202)
- [Digitoegankelijk.nl](https://www.digitoegankelijk.nl/)
- [WebAIM](https://webaim.org/)
- [A11y Project](https://www.a11yproject.com/)

## 💡 Tips voor implementatie

1. **Laad altijd als eerste** - Vóór Tailwind of andere frameworks
2. **Test met keyboard** - Tab door je hele site
3. **Test met screen reader** - Gebruik NVDA of VoiceOver
4. **Check contrast** - Gebruik tools zoals Lighthouse
5. **Valideer HTML** - Semantisch correcte markup is de basis

## 🤝 Tailwind integratie

Deze stylesheet werkt naadloos met Tailwind:

```html
<!-- Tailwind classes werken gewoon -->
<button class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded">
  Button met automatische focus states
</button>

<!-- Of gebruik Tailwind's ring utilities -->
<button class="focus:ring-2 focus:ring-blue-500">
  Custom Tailwind focus
</button>
```

## ⚡ Performance

- **Kleine footprint**: ~10KB ongeminified
- **Geen JavaScript vereist**: Pure CSS
- **Geen dependencies**: Standalone
- **Modern CSS**: Custom properties, `:focus-visible`, `@media` queries

## 🛡️ Browser support

Gebruikt moderne CSS features:
- CSS Custom Properties (IE11 ❌, moderne browsers ✅)
- `:focus-visible` (met fallback naar `:focus`)
- `@media (prefers-reduced-motion)`
- `@media (prefers-contrast)`

Voor IE11 ondersteuning, gebruik een PostCSS plugin om custom properties te polyfill.

## 📝 Changelog & Updates

Deze boilerplate is gebaseerd op:
- WCAG 2.1 Level AA (2018)
- European Accessibility Act requirements (2025)
- Modern CSS best practices (2025)

## 🎓 Leren

Begin met:
1. Open `a11y-demo.html` en tab door de pagina
2. Lees `IMPLEMENTATIE.md` voor details
3. Pas de theme colors aan in je project
4. Test met keyboard en screen reader
5. Gebruik geautomatiseerde tools voor extra checks

## 💬 Veelgestelde vragen

**Q: Moet ik nog andere accessibility libraries gebruiken?**  
A: Nee, deze stylesheet dekt de basis. Voor complexe componenten heb je mogelijk JavaScript libraries nodig.

**Q: Werkt dit met mijn framework?**  
A: Ja! Pure CSS werkt met alle frameworks.

**Q: Kan ik de focus styles aanpassen?**  
A: Ja, via CSS custom properties. Zie theme configuratie hierboven.

**Q: Is dit genoeg voor volledige compliance?**  
A: Nee, je moet ook zorgen voor semantische HTML, alt teksten, ARIA labels, etc. Zie "Wat je zelf nog moet doen".

---

**Gemaakt voor een toegankelijker web 🌐**

Vragen? Zie `IMPLEMENTATIE.md` voor uitgebreide documentatie!
# accessibility
# accessibility
# accessibility
