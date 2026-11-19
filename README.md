# ui-ux-design

Skill de agente (Claude Code y compatibles con el formato `SKILL.md`) para diseñar, implementar y revisar interfaces con criterio verificable: heurísticas de Nielsen, Leyes de UX (Yablonski), Refactoring UI, diseño centrado en el usuario (Lowdermilk, ISO 9241), WCAG 2.2 AA y patrones con evidencia (NN/g, GOV.UK, Baymard). En español.

## Instalación

Claude Code, para todos tus proyectos:

```bash
git clone https://github.com/JVISERASS/ui-ux-design ~/.claude/skills/ui-ux-design
```

Solo para un proyecto: clónalo en `.claude/skills/ui-ux-design` dentro del repo.

Con el CLI `skills`:

```bash
npx skills add JVISERASS/ui-ux-design
```

## Contenido

| Fichero | Para qué |
|---|---|
| `SKILL.md` | Lo esencial, siempre cargado: prioridades, necesidad antes que solución, estructura, diseño visual, accesibilidad y cómo responder según la petición |
| `references/centrado-en-usuario.md` | De petición a necesidad, entrevistas, tests, severidad, métricas y SUS |
| `references/leyes-ux.md` | Las 30 leyes de lawsofux.com, mapa por situación y malos usos |
| `references/diseno-visual.md` | Refactoring UI con valores y CSS/Tailwind, OKLCH, tokens, modo oscuro y densidad |
| `references/patrones.md` | Formularios, estados, tablas, dashboards, navegación móvil, microcopy y patrones engañosos |
| `references/accesibilidad.md` | WCAG 2.2 A/AA como checklist, ARIA, marco legal UE/España y receta de pruebas |
| `references/fuentes.md` | De dónde sale cada cosa y cuánto fiarse |

Todo está parafraseado y enlazado a su fuente; lo no comprobado va marcado como **UNVERIFIED**.
