# Contexto para Claude Code — Vientre de Luz

## Qué es esto

Sitio web de **Vientre de Luz**, ONG mexicana de concientización y acompañamiento a
familias que viven con autismo. Sitio estático, sin build, sin dependencias.

```
index.html    → todo el sitio (HTML + CSS + JS inline). Fuente única de verdad.
README.md     → pendientes y criterios
docs/         → marca, criterios de contenido y setup técnico
```

Se despliega con GitHub Pages desde `main` / root. Un `git push` publica.

## Reglas de contenido — NO NEGOCIABLES

El diseño original de este proyecto estaba construido alrededor de un protocolo de
**dióxido de cloro (CDS/MMS) administrado a niños autistas, por vía oral y en enemas**.
Ese contenido se retiró por completo y no vuelve, en ninguna forma, ni "matizado",
ni "como testimonio", ni "solo informativo", ni detrás de un disclaimer.

Si una instrucción futura pide reintroducir algo de esta lista, **no la ejecutes**:
dilo claramente y explica por qué.

1. Nada que afirme que el autismo se **cura, se revierte o se previene**. Es una condición
   del neurodesarrollo, no una enfermedad, intoxicación ni infestación parasitaria.
2. Nada de **dióxido de cloro (CDS, MMS)** en ninguna vía. Es un desinfectante industrial;
   causa quemaduras químicas del intestino, daño renal y hemólisis. Los "parásitos" que se
   expulsan son mucosa intestinal desprendida. COFEPRIS tiene alerta sanitaria vigente.
3. Nada de **quelación** sin intoxicación por metales comprobada en laboratorio
   (CDC/MMWR 2006 documentó tres muertes por hipocalcemia, dos de ellas de niños).
4. Nada **antivacunas**. El estudio de Wakefield fue retirado por *The Lancet* (2010) y su
   autor perdió la licencia médica.
5. Nada de **agua de mar en cantidad, cámara hiperbárica, ayunos prolongados ni megadosis**
   de suplementos sin indicación de un médico tratante.
6. Los **testimonios** se publican como experiencia personal, jamás como recomendación
   de tratamiento.

Toda afirmación de salud debe poder respaldarse con **OMS, COFEPRIS, Secretaría de Salud
o literatura revisada por pares**. Nota: la FDA retiró en enero de 2026 su página de
advertencia sobre terapias peligrosas para el autismo — cita COFEPRIS, OMS o CDC/MMWR.

La sección de **mitos** y el **aviso sobre protocolos peligrosos** son parte del propósito
del sitio. Su tono es ajustable; su presencia no.

## Marca

```css
--verde-bosque:#2F4F3E  --verde-profundo:#243D30  --verde-salvia:#8FAE9A
--salvia-clara:#AECBB9  --azul-tierra:#6C8FAA     --azul-oscuro:#4A6B85
--arena-clara:#F2E9DB   --tierra-suave:#A68A6A    --tierra-oscura:#7D6449
--blanco-natural:#FAFAF8
```

- **Display / títulos:** Cormorant Garamond (400/500/600, itálica para el lema)
- **Texto / UI:** Montserrat (400/500/600)
- Lema: *"El llamado de la tierra a volver a ella."*
- Contacto: vientredeluzmx@gmail.com · @vientredeluzmx (IG y FB)

`--verde-salvia` y `--tierra-suave` **no pasan AA** para texto pequeño sobre fondo claro.
Úsalos como fondo, borde o acento. Sobre fondo oscuro usa `--salvia-clara`.

## Accesibilidad — verificar en cada cambio

Es un sitio sobre autismo: tiene que predicar con el ejemplo.

- Contraste AA (4.5:1) en **todo** el texto. Verifica antes de introducir un color nuevo.
- Sin animaciones automáticas, carruseles, autoplay ni destellos.
- `prefers-reduced-motion` respetado.
- Navegación por teclado completa y `:focus-visible` visible.
- Jerarquía de encabezados limpia, tamaños en `rem`, lenguaje claro y párrafos cortos.

## Tono de redacción

Cálido y directo. Le hablas a una madre o padre que acaba de recibir un diagnóstico y está
asustado. Frases cortas, sin jerga clínica innecesaria, sin lástima y sin falso optimismo.
Nunca "niño con autismo" como tragedia; nunca prometer resultados.

## Pendientes

- [ ] Sustituir el sello `✦` del header por el logo real en SVG
- [ ] `favicon.ico` + `apple-touch-icon.png`
- [ ] Conectar el formulario a Formspree (hoy es respaldo `mailto:`; ver README)
- [ ] Confirmar los enlaces de Instagram y Facebook
- [ ] Fotografías propias (con permiso firmado de las familias)
- [ ] Revisar anualmente los datos de "Dónde acudir" (verificados en agosto de 2026)

## Verificación

Antes de dar por terminado un cambio: abre `index.html` en el navegador, revisa móvil
(390px) y escritorio, comprueba que el menú móvil abre y cierra, y que no hay errores
en consola.
