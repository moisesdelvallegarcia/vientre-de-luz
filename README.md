# Vientre de Luz

Sitio de la ONG **Vientre de Luz** — concientización y acompañamiento a familias que viven con autismo en México.

## Estructura

Sitio estático de tres páginas con hoja de estilo compartida. Sin build, sin dependencias.

```
CLAUDE.md                     → contexto que Claude Code carga solo
index.html                    → portada (6 pasos)
recetas.html                  → recetas integrales
acerca.html                   → acerca de y aviso de privacidad
styles.css                    → estilos compartidos
docs/marca.md                 → sistema de marca (colores, tipografías, logo)
docs/criterios-de-contenido.md→ qué se publica y qué no, y por qué
docs/setup-tecnico.md         → PowerShell, GitHub y DNS de GoDaddy
_notas/                       → PRIVADO, no se sube (está en .gitignore)
```

> **Antes del primer push**, corre `git status` y confirma que `_notas/` no aparece.
> Contiene material sobre personas reales.

## Ver en local

Abre `index.html` en el navegador. O con servidor:

```powershell
npx serve .
```

## Publicar

Publicado en **https://moisesdelvallegarcia.github.io/vientre-de-luz/**

Cada `git push` a `main` actualiza el sitio. GitHub Pages ya está activo
(Settings → Pages → Deploy from a branch → `main` / root).

### Sobre el dominio propio

**No hay archivo `CNAME` en el repo, a propósito.** `vientredeluz.com` está registrado
en GoDaddy pero su DNS todavía apunta a otro servidor. Con un `CNAME` presente, Pages
redirige la URL de github.io al dominio y el sitio deja de cargar.

El orden correcto es: primero los registros DNS en GoDaddy (4 registros `A` + `CNAME www`,
los valores están en `docs/setup-tecnico.md`), y hasta que resuelvan, crear el `CNAME`
con una sola línea, `vientredeluz.com`.

## Pendientes antes de salir a producción

- [ ] Sustituir el sello `✦` del encabezado por el logo real en SVG
- [ ] Agregar `favicon.ico` y `apple-touch-icon.png`
- [ ] Conectar el formulario: crear cuenta en [Formspree](https://formspree.io)
      y reemplazar `TU-ID-AQUI` en el `action` del `<form>`
- [ ] Confirmar los enlaces de Instagram y Facebook
- [ ] Revisar anualmente los datos de "Dónde acudir" (verificados en agosto de 2026)
- [ ] Agregar fotografías propias (con permiso firmado de las familias)

## Criterios de contenido

Este sitio orienta, no diagnostica ni trata. Todo lo que se publique debe cumplir:

1. **Nada que prometa curar o revertir el autismo.** No existe tal cosa.
2. **Nada de protocolos de dióxido de cloro (CDS/MMS), quelación ni sustancias
   ingeridas o aplicadas sin indicación de un médico tratante.** Son peligrosos
   y hay niños hospitalizados y fallecidos por ellos.
3. **Nada antivacunas.** No hay relación entre vacunas y autismo.
4. Los testimonios se publican como experiencia personal, nunca como
   recomendación de tratamiento.
5. Toda afirmación de salud debe poder respaldarse con OMS, COFEPRIS, Secretaría
   de Salud o literatura médica revisada por pares.

## Verificación de contenido (agosto 2026)

Datos confirmados contra fuente primaria: teléfono, dirección y horario del Centro
Autismo Teletón Ecatepec; artículos 10 y 17 de la Ley General (publicada en el DOF
el 30/04/2015, sin reformas posteriores); vigencia de USAER; datos de la OMS sobre
vacunas y autismo. Al citar riesgos de dióxido de cloro conviene apoyarse en COFEPRIS,
OMS y CDC/MMWR: la FDA retiró en enero de 2026 su página de advertencia sobre
terapias peligrosas para el autismo.

## Accesibilidad

Verificado: contraste AA en todo el texto, navegación por teclado, `prefers-reduced-motion`,
sin autoplay ni destellos, jerarquía de encabezados correcta, tamaños en `rem`.
Mantener estos criterios en cualquier cambio.
